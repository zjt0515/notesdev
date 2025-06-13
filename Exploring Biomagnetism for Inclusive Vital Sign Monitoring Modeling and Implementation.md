https://dl.acm.org/doi/10.1145/3636534.3690702

###  Exploring Biomagnetism for Inclusive Vital Sign Monitoring: Modeling and Implementation 

本文介绍了MagWear的设计、实现和评估，这是一种新的基于生物磁学的系统，可以准确、全面地监测具有不同肤色的移动用户的心率和呼吸速率。MagWear的贡献是双重的。首先，我们建立了一个数学模型，描述了血液在外磁场作用下的磁耦合效应。该模型揭示了监测个体生命体征时准确性的变化。其次，利用从该数学模型中得出的见解，我们提出了一种软硬件协同设计，有效地处理人类多样性对生命体征监测性能的影响，使该通用解决方案更接近于实际采用。我们在两层PCB板上实现了MagWear的原型，并遵循IRB协议进行系统评估。我们对30名志愿者进行的广泛实验表明，MagWear实现了高监测精度，心率的平均百分比误差（MPE）为1.55%，呼吸率为1.79%。与Apple Watch 8的直接比较进一步展示了MagWear在不同用户条件下的一贯高性能。

###  WiProfile: Unlocking Diffraction Effects for Sub-Centimeter Target Profiling Using Commodity WiFi Devices 

使用单个毫米波雷达的群组分析MeatSpec:通过消费者级光谱成像MetaBioLiq:BioFluids的可穿戴被动后表面辅助毫米波传感平台MoiréVib:基于Moiré）模式EMTrig:LiDAR感知的电磁注入触发的物理对抗示例通过全局压缩比决策在移动设备上实现快速活动识别的协作压缩方案基于可穿戴PPG的个性化自由重量训练Accuth+监控系统：基于加速计的Wrist Worn可穿戴设备的防欺骗语音认证AGR:使用解译的声步态识别ble微距离像ATP：多径和多普勒效应下的声学跟踪和定位

###  BrailleReader: Braille Character Recognition Using Wearable Motion Sensor 

16

###  Cloud-Assisted Secure and Cost-Effective Authenticated Solution for Remote Wearable Health Monitoring System 

###  CROMOSim: A Deep Learning-Based Cross-Modality Inertial Measurement Simulator 

###  EdgeActNet: Edge Intelligence-Enabled Human Activity Recognition Using Radar Point Cloud 

 EdgeTimer: Adaptive Multi-Timescale Scheduling in Mobile Edge Computing with Deep Reinforcement Learning 

 FTP: Enabling Fast Beam-Training for Optimal mmWave Beamforming 

### Gsyn: Reducing Staleness and Communication Waiting via Grouping-based Synchronization for Distributed Deep Learning 

https://ieeexplore.ieee.org/document/10621250

分布式深度学习已被广泛应用于大规模数据集上的深度神经网络训练。然而，在数据并行训练中，常用的参数服务器架构存在同步时间长的问题。虽然现有的解决方案都是通过打破同步障碍或限制过时界限来减少同步开销，但它们不可避免地会遇到收敛效率低和同步等待时间长的问题。为了解决这些问题，我们建议使用Gsyn来减少同步开销和过时性。具体来说，Gsyn将工人分为多个组。同一组中的工作人员使用批量同步并行方案相互协调，以实现高收敛效率，并且每个组与参数服务器异步通信，以减少同步等待时间，从而提高收敛效率。此外，我们从理论上分析了最佳组数，以在陈旧性和同步等待之间实现良好的折衷。在具有多个训练任务的真实集群中的评估测试表明，Gsyn是有益的，与最先进的解决方案相比，它将分布式训练加速了27%。

###  LoBaCa: Super-Resolution LoRa Backscatter Localization for Low-Cost Tags 

###  Real-Time Contactless Eye Blink Detection Using UWB Radar 

闪烁检测对于各种人机交互场景至关重要，例如虚拟现实和驾驶状态检测。近年来，它得到了工业界和学术界的高度重视。现有的非接触检测系统（相机、声学等）取得了重大进展，但各种问题阻碍了它们的广泛采用，包括隐私问题、视线要求和成本问题。因此，迫切需要一个简单而强大的系统，可以使用普通的商业设备检测眨眼。在本文中，我们提出了BlinkRadar，它使用低成本定制脉冲无线电超宽带（IR-UWB）雷达来进行非接触和细粒度闪烁检测。BlinkRadar可以可靠地检测驾驶条件下的驾驶员闪烁，从而可以推断出昏昏欲睡的驾驶。为了有效地提取眨眼信号，我们分析了真实的实验数据，研究了眨眼模式的特征，并成功地使用多序列变分模式分解（MS-VMD）算法将眨眼信号从噪声信号中分离出来。我们在两种不同的环境（安静的房间和移动的车辆）中进行了广泛的实验，发现BlinkRadar的平均闪烁检测精度超过96.2%。我们的结果证明了使用UWB雷达进行非接触眨眼检测的可行性。

###  Self-supervised Learning for Complex Activity Recognition through Motif Identification Learning 

15

由于收集标记传感器数据的成本，有效地使用未标记数据进行预训练的人类活动识别（HAR）自监督学习（SSL）方法受到了关注。然而，将以前的SSL应用于实际工业环境中的复杂活动带来了挑战。尽管工作程序是一致的，但不同的情况，例如包装过程中不同大小的包装和内容物，在同一活动类别中引入了显著的可变性。在本研究中，我们专注于与特定活动中的特征和必要动作（传感器数据模体）相对应的传感器数据，例如组装盒活动中的拉伸打包带动作，并建议在自监督学习中训练神经网络，以便其识别特征动作的发生，即Motif识别学习（MoIL）。网络中的特征提取器随后用于下游活动识别任务，从而能够准确识别包含这些特征动作的活动，即使使用有限的标记训练数据。MoIL方法是在真实世界的工业活动数据上进行评估的，包括最先进的SSL任务，在有限的培训标签下提高了23.85%

https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=10788514

###  SlpRoF: Improving the Temporal Coverage and Robustness of RF-Based Vital Sign Monitoring During Sleep 

17

大多数现有的基于RF的生命体征监测系统要么假设人体处于静止状态，要么在检测到运动时丢弃测量值，以输出可靠的呼吸频率和心率。这种假设极大地限制了这些系统在实践中的可用性。即使在睡眠期间，人也可以经历各种身体状态，包括轻度睡眠中的转身和不自主抽搐，深度睡眠中的静止，或由于睡眠障碍（如不宁腿综合征）导致的异常肢体运动。在这项工作中，我们开发了SlpRoF，这是一种低成本的无接触系统，使用商用现成UWB雷达，在睡眠期间实现高时间覆盖和高精度生命体征监测。通过将身体状态分为静止状态、肢体运动状态和躯干运动状态，并在前两个状态期间提取生命体征，它直接增加了夜间的有效报告周期。通过分析高阶谐波并利用来自身体多个部位的捕获信号中的空间分集，它提高了心率估计的准确性，从而通过可靠的评估间接增加了时间覆盖。实验结果表明，SlpRoF能够分别实现呼吸速率0.44次/min、呼吸间隔1.55 s和心率0.9次/min的平均中位绝对误差（MAE）。

https://ieeexplore.ieee.org/document/10354454

> 分布式深度学习已被广泛应用于大规模数据集上的深度神经网络训练。然而，常用的参数服务器架构在数据并行训练中存在同步时间过长的问题。虽然现有的解决方案都是通过打破同步壁垒或限制过时界限来减少同步开销，但它们不可避免地会遇到收敛效率低和同步等待时间长的问题。为了解决这些问题，我们提出Gsyn来减少同步开销和过时性。具体来说，Gsyn将工作人员分成多个组。同一组内的worker采用批量同步并行方案相互协调，达到较高的收敛效率，每组与参数服务器异步通信，减少同步等待时间，从而提高收敛效率。进一步，我们从理论上分析了最优组数，以实现陈旧和同步等待之间的良好权衡。在具有多个训练任务的现实集群中的评估测试表明，Gsyn是有益的，与最先进的解决方案相比，它可以将分布式训练加速高达27%。

> 