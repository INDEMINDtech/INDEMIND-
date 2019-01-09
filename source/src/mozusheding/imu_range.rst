.. _imu_range:

设定加速度计及陀螺仪的量程
=============================

通过 API 的 ``SetOptionValue()`` 函数，就可以设定当前打开设备的各类控制值。

设定加速度计及陀螺仪的量程，就是设定 ``Option::ACCELEROMETER_RANGE`` 和 ``Option::GYROSCOPE_RANGE`` 。

.. Attention::

  * 加速度计量程有效值（单位：g）： 4, 8, 16, 32 。
  * 陀螺仪量程有效值（单位：deg/s）： 500, 1000, 2000, 4000 。

参考代码片段：

.. code-block:: c++

  auto &&api = API::Create(argc, argv);
  if (!api)
    return 1;

  // ACCELEROMETER_RANGE values: 4, 8, 16, 32
  api->SetOptionValue(Option::ACCELEROMETER_RANGE, 8);
  // GYROSCOPE_RANGE values: 500, 1000, 2000, 4000
  api->SetOptionValue(Option::GYROSCOPE_RANGE, 1000);

  LOG(INFO) << "Set ACCELEROMETER_RANGE to "
            << api->GetOptionValue(Option::ACCELEROMETER_RANGE);
  LOG(INFO) << "Set GYROSCOPE_RANGE to "
            << api->GetOptionValue(Option::GYROSCOPE_RANGE);

参考运行结果，于 Linux 上：

.. code-block:: bash

  $ ./samples/_output/bin/tutorials/ctrl_imu_range
  I/utils.cc:28 Detecting MYNT EYE devices
  I/utils.cc:38 MYNT EYE devices:
  I/utils.cc:41   index: 0, name: MYNT-EYE-S1030, sn: 4B4C1F1100090712
  I/utils.cc:49 Only one MYNT EYE device, select index: 0
  I/imu_range.cc:34 Set ACCELEROMETER_RANGE to 8
  I/imu_range.cc:36 Set GYROSCOPE_RANGE to 1000
  I/imu_range.cc:81 Time beg: 2018-11-21 15:34:57.726428, end: 2018-11-21 15:35:12.190478, cost: 14464ms
  I/imu_range.cc:84 Img count: 363, fps: 25.0967
  I/imu_range.cc:86 Imu count: 2825, hz: 195.312


样例程序按 ``ESC/Q`` 结束运行后，imu量程设置完成。该结果将固化在硬件内部，不受掉电影响。

完整代码样例，请见 `imu_range.cc <https://github.com/slightech/MYNT-EYE-S-SDK/blob/master/samples/tutorials/control/imu_range.cc>`_ 。
