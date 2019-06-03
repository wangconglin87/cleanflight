# 电池监测

监测视电池状态。电压可以触发低电压报警[BB响](Buzzer.md)，板载LED以及LED灯带闪烁。

低电压报警：

* 确保有足够的时间安全降落
* 保护电池不过放

电池芯片的最小和最大电压都可以设置，连接电池后，相关电压用来测算电芯的数量。

只能测量电池总电压，无法测量单个电芯的电压。

## Supported targets

All targets support battery voltage monitoring unless status.

## 连接

使用电池前，**检查正负极**

**连接前**，检测电压。不正确的电压或相反极性都有可能烧毁飞控。

### Naze32

Naze32有板载的分压电路，可直接将电池连接到VBAT上。

**注意：** 连接电池前，确保电池已从分电板上断开。再次检查连线。不正确的连线会立刻烧毁飞控及连接的外围设备（ESC，GPS，接收器等）。

### CC3D

CC3D没有分压器。需要输出最大值为3.3V的分压器。连接分压器的信号输出端到S5_IN/PA0/RC5。

注:

* S5_IN/PA0/RC5是8针连接器的第7针, 倒数第二个, GND/+5/PPM的对面.

* 当启用电池检测的时候，RC5就不能用来接受PWM的输入了。

### Sparky

See the [Sparky board chapter](boards/Board%20-%20Sparky.md).

## 配置

启用 `VBAT`

配置电芯大小电压使用下列命令：

`vbat_scale` - 校准电压 (通过 `status` 可以查看)

`vbat_max_cell_voltage` - 电芯最大电压, 例：43 = 4.3V

`vbat_min_cell_voltage` - 电芯最大电压, 触发电池损坏警报(battery-critical)，例：33 = 3.3V

`vbat_warning_cell_voltage` - 报警电压(battery-warning)，例： 34 = 3.4V

`vbat_hysteresis` - 迟滞电压，触发低电压报警(low-battery)，例：1 = 0.1V

示例：

```
set vbat_scale = 110
set vbat_max_cell_voltage = 43
set vbat_min_cell_voltage = 33
set vbat_warning_cell_voltage = 34
set vbat_hysteresis = 1
```

# 电流监测

支持外部电流计（查看相应的飞控说明书）

启用后，相应数据会被计算并发送给遥测和OLED子系统：

* 安培
* 已使用多少毫安时
* 剩余容量

## 配置

启用电流监测命令：

```
feature CURRENT_METER
```

Configure the current meter type using the `amperage_meter_type` settings here:
使用`amperage_meter_type`设置电流计类型

| Value   | Sensor Type            | 传感器类型              |
| ------- | ---------------------- | ---------------------- |
| NONE    | None                   |
| ADC     | ADC/hardware sensor    |
| VIRTUAL | Virtual sensor         |

Configure capacity using the `battery_capacity` setting, in mAh units.

If you're using an OSD that expects the multiwii current meter output value, then set `multiwii_amperage_meter_output` to `ON` (this multiplies amperage sent to MSP by 10 and truncates negative values)).

### ADC Sensor

The current meter needs to be configured so the value read at the Analog to Digital Converter (ADC) input matches actual current draw.  Just like you need a voltmeter to correctly calibrate your voltage reading you also need an ammeter to calibrate the current sensor.
Unlike voltage sensing which is usually quite good from the factory, current sensing varies significantly from board to board and should be calibrated.

It is recommended to set `multiwii_amperage_meter_output` to `OFF` when calibrating ADC current sensor.

To measure the current a linear response device is used that converts the current traveling through it to a voltage to be read by the ADC on your flight controller.
The maximum voltage that the flight controller can read is 3.3V (3300 mV), this is usually the limiting factor on the maximum measurable current.
Most sensors use a shunt resistor to measure current however there are a few that use hall effect sensors.

The flight controller uses the following equation to convert the measured ADC voltage to a current.
```
Current(Amps) = ADC (mV) / amperage_meter_scale * 10 + amperage_meter_offset / 1000
```
Where the calibrations are:

| Setting                       | Description                                              |
| ----------------------------- | -------------------------------------------------------- |
| `amperage_meter_scale`     | The scaling factor in mV/10A  |
| `amperage_meter_offset`    | The offset in mA |

This is in the mathematical form of y = x/m + b and with a few measurements along this line you can calibrate any combination of sensor and flight controller to a high accuracy.

#### Calibrate using an ammeter

**!!Important: Always take off your props before doing any testing!!**

To calibrate your flight controller with a current meter follow these steps.

1. Make a copy of [this google sheet](https://docs.google.com/spreadsheets/d/1lkL-X_FT9x2oqrwQEctDsEUhgdY19upNGc78M6FfJXY/). It will do all of the maths for you.
2. Hook your ammeter up in series with your drone and a charged battery. I suggest an XT60 extender with one lead cut. Now your ammeter will be displaying the true current draw of your system.
3. Connect to your flight controller through the configurator and check your current calibrations. Change them in the google sheet if needed.
4. Use the motor tab to increase the throttle and change the current draw of the drone to around 1 A on the ammeter (it does not matter if it is not exact).
5. Switch back to the power and battery tab and record current from the ammeter in the measured current column and the current reported by Betaflight in the flight controller current column (both in amps, to 2 decimal places).
6. Repeat this measurement (steps 4 and 5) 3 or more times at various currents from 0 to 5 Amps (make sure not to go over your ammeter rated current).
7. Once this is done make sure the results are linear on the graph and that the regression value is green. You can now update to the new calibration values and enjoy accurate battery usage information.

The same method can be applied to both hall effect sensors and shunt resistors. Shunt resistors will usually have an offset of less than +/- 1000 mA however hall effect sensors offsets will be much higher.
Note that while your calibration may be correct there is still a maximum current measure that you may exceed at maximum throttle, this will cause the current recorded by the flight controller to ceiling at this value even if the actual current is higher.
As a result the reported mAh used may be less than is actually used, always keep an eye on the battery voltage as well.

If you do not want to use google sheets then simply use some other tool that preforms a linear regression on the dataset. Multiply `amperage_meter_scale` used in testing by the slope and subtract the intercept in mA from  `amperage_meter_offset` to get the corrected calibration values.

### Virtual Sensor

The virtual sensor uses the throttle position to calculate an estimated current value. This is useful when a real sensor is not available. The following settings adjust the virtual sensor calibration:

| Setting                       | Description                                              |
| ----------------------------- | -------------------------------------------------------- |
| `amperage_meter_scale`     | The throttle scaling factor [centiamps, i.e. 1/100th A]  |
| `amperage_meter_offset`    | The current at zero throttle (while disarmed) [centiamps, i.e. 1/100th A] |

There are two simple methods to tune these parameters:  one uses a battery charger and another depends on actual current measurements.

#### Tuning Using Actual Current Measurements
If you know your craft's current draw (in Amperes) while disarmed (Imin) and at maximum throttle while armed (Imax), calculate the scaling factors as follows:
```
amperage_meter_scale = (Imax - Imin) * 100000 / (Tmax + (Tmax * Tmax / 50))
amperage_meter_offset = Imin * 100
```
Note: Tmax is maximum throttle offset (i.e. for `max_throttle` = 1850, Tmax = 1850 - 1000 = 850)

For example, assuming a maximum current of 34.2A, a minimum current of 2.8A, and a Tmax `max_throttle` = 1850:
```
amperage_meter_scale = (Imax - Imin) * 100000 / (Tmax + (Tmax * Tmax / 50))
                    = (34.2 - 2.8) * 100000 / (850 + (850 * 850 / 50))
                    = 205
amperage_meter_offset = Imin * 100 = 280
```
#### Tuning Using Battery Charger Measurement
If you cannot measure current draw directly, you can approximate it indirectly using your battery charger.  
However, note it may be difficult to adjust `amperage_meter_offset` using this method unless you can
measure the actual current draw with the craft disarmed.

Note:
+ This method depends on the accuracy of your battery charger; results may vary.
+ If you add or replace equipment that changes the in-flight current draw (e.g. video transmitter,
  camera, gimbal, motors, prop pitch/sizes, ESCs, etc.), you should recalibrate.

The general method is:

1. Fully charge your flight battery
2. Fly your craft, using >50% of your battery pack capacity (estimated)
3. Note Cleanflight's reported mAh drawn
4. Fully charge your flight battery again, noting the amount of mAh recharged
5. Adjust `amperage_meter_scale` to according to the formula given below
6. Repeat and test

Given (a) the mAh recharged and (b) the cleanflight reported mAh drawn, calculate a new `amperage_meter_scale` value as follows:
```
amperage_meter_scale = old_amperage_meter_scale * (mAh_recharged / cleanflight_reported_mAh_drawn)
```
For example, assuming:
+ An amount recharged of 1500 mAh
+ A Cleanflight reported current drawn of 2000 mAh
+ An existing `amperage_meter_scale` value of 400 (the default)

Then the updated `amperage_meter_scale` is:
```
amperage_meter_scale = old_amperage_meter_scale * (mAh_recharged / cleanflight_reported_mAh_drawn)
                     = 400 * (1500 / 2000)
                     = 300
```
