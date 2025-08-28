# DC to AC Inverters
- 🎓 EEE 513 - Advanced Power Electronics (2.00 Credits) | Lecture 1
- 👨‍🎓 Md. Hassanul Karim Roni, Assistant Professor, EEE, HSTU, Dinajpur
- 📧 hkroni@tch.hstu.ac.bd

---

## Learning Objectives
By the end of this lecture, students will be able to:
- Understand the principles of DC to AC conversion (inversion)
- Analyze single-phase and three-phase inverter circuits
- Design and analyze PWM control strategies
- Calculate harmonic content and THD in inverter outputs
- Understand different inverter topologies and their applications
- Design output filters for inverter systems
- Analyze multilevel inverter configurations
- Select appropriate inverters for specific applications

---

## 1. Introduction to Inverters

### 1.1 Definition and Purpose

**Inverters** are power electronic circuits that convert DC power to AC power. They are the complement of rectifiers and are essential for many modern applications.

### 1.2 Classification of Inverters

#### **By Output Waveform:**
- **Square Wave Inverters**: Simple switching, high harmonic content
- **Modified Sine Wave**: Stepped approximation of sine wave  
- **Pure Sine Wave**: High-quality sinusoidal output

#### **By Phase Number:**
- **Single-Phase Inverters**: For residential and small commercial loads
- **Three-Phase Inverters**: For industrial and high-power applications

#### **By Switching Technique:**
- **PWM Inverters**: Pulse Width Modulation for quality control
- **Square Wave Inverters**: Fixed duty cycle operation

#### **By Circuit Configuration:**
- **Voltage Source Inverters (VSI)**: DC voltage source input
- **Current Source Inverters (CSI)**: DC current source input

#### **By Isolation:**
- **Transformer Isolated**: Galvanic isolation provided
- **Transformerless**: Direct connection without isolation

### 1.3 Applications of Inverters

#### **Renewable Energy Systems:**
- **Solar PV inverters**: Grid-tied and off-grid systems
- **Wind turbine inverters**: Variable speed wind generation
- **Energy storage systems**: Battery backup systems

#### **Motor Drives:**
- **Variable Frequency Drives (VFDs)**: Industrial motor control
- **Electric vehicle drives**: Traction motor control
- **Servo drives**: Precision motion control

#### **Uninterruptible Power Supplies (UPS):**
- **Online UPS**: Continuous inverter operation
- **Offline UPS**: Backup inverter operation
- **Line-interactive UPS**: Hybrid operation

#### **Grid Applications:**
- **HVDC transmission**: High-voltage DC links
- **STATCOM**: Static VAR compensation
- **Grid stabilization**: Power quality improvement

---

## 2. Single-Phase Inverters

### 2.1 Single-Phase Half-Bridge Inverter

#### **Circuit Configuration:**
- Two switches (S1, S2) with complementary operation
- Split DC supply (Vdc/2 each)
- Output voltage switches between +Vdc/2 and -Vdc/2

#### **Operation:**
**Mode 1 (0 < t < T/2):**
- S1 ON, S2 OFF
- vo = +Vdc/2

**Mode 2 (T/2 < t < T):**
- S1 OFF, S2 ON  
- vo = -Vdc/2

#### **Output Voltage Analysis:**

**Fourier Series:**
```
vo(t) = (4Vdc/π) Σ[n=1,3,5,...] (1/n) sin(nωt)
```

**Fundamental Component:**
```
v1(t) = (4Vdc/π) sin(ωt)
V1(rms) = (4Vdc)/(π√2) = 0.9Vdc
```

**THD Calculation:**
```
THD = √(Σ[n=3,5,7,...] Vn²)/V1 = √(π²/8 - 1) = 48.3%
```

### 2.2 Single-Phase Full-Bridge Inverter

#### **Circuit Configuration:**
- Four switches arranged in H-bridge configuration
- Single DC supply Vdc
- More versatile than half-bridge

#### **Switching Modes:**

**Mode 1 (Square Wave Operation):**
- S1, S4 ON for T/2
- S2, S3 ON for T/2
- vo = ±Vdc

**Mode 2 (PWM Operation):**
- Pulse width modulation for harmonic control
- Variable duty cycle control

#### **Output Voltage (Square Wave):**

**Fourier Series:**
```
vo(t) = (4Vdc/π) Σ[n=1,3,5,...] (1/n) sin(nωt)
```

**RMS Value:**
```
Vo(rms) = Vdc
```

**Fundamental RMS:**
```
V1(rms) = (4Vdc)/(π√2) = 0.9Vdc
```

### 2.3 Performance Parameters

#### **Form Factor:**
```
FF = Vrms/Vavg
```

#### **Distortion Factor:**
```
DF = V1(rms)/Vrms
```

#### **Total Harmonic Distortion:**
```
THD = √(Vrms² - V1²)/V1
```

#### **Harmonic Factor:**
```
HFn = Vn/V1 (for nth harmonic)
```

---

## 3. Pulse Width Modulation (PWM)

### 3.1 PWM Principle

PWM controls the output voltage by varying the width of pulses while keeping the switching frequency constant.

#### **Key Parameters:**
- **Modulation Index (ma)**: ma = Vm/Vtri (0 ≤ ma ≤ 1)
- **Frequency Ratio (mf)**: mf = ftri/fref
- **Switching Frequency (fs)**: Frequency of triangular carrier

### 3.2 Sinusoidal PWM (SPWM)

#### **Generation Method:**
- Compare sinusoidal reference with triangular carrier
- Switch states determined by comparison result
- Output pulse width varies sinusoidally

#### **Output Voltage Analysis:**

**For ma ≤ 1:**
```
V1(rms) = ma × (Vdc/√2)
```

**Linear Relationship:**
- Output voltage directly proportional to modulation index
- Excellent linearity for ma ≤ 1

#### **Harmonic Content:**
- Harmonics appear around switching frequency (mf)
- Lower order harmonics significantly reduced
- THD typically 5-15% depending on mf

### 3.3 Space Vector PWM (SVPWM)

#### **Principle:**
- Uses space vector representation of three-phase quantities
- Optimal switching pattern generation
- Better DC bus utilization than SPWM

#### **Advantages:**
- 15% higher output voltage than SPWM
- Lower harmonic distortion
- Better DC link utilization
- Reduced switching losses

#### **Applications:**
- Three-phase motor drives
- Grid-tied inverters
- High-performance applications

### 3.4 Modified PWM Techniques

#### **Third Harmonic Injection:**
- Adds 3rd harmonic to reference signal
- Increases fundamental output by 15%
- Zero sequence has no effect on line-to-line voltages

#### **Selective Harmonic Elimination (SHE):**
- Pre-calculated switching angles
- Eliminates specific low-order harmonics
- Complex calculation but excellent results

---

## 4. Three-Phase Inverters

### 4.1 Three-Phase Voltage Source Inverter

#### **Circuit Configuration:**
- Six switches arranged in three legs
- Each leg has two complementary switches
- Produces three-phase AC output from DC input

#### **Switch States:**
Eight possible switching states:
- **Active States (1-6)**: One switch per leg conducting
- **Zero States (0,7)**: Three upper or three lower switches conducting

### 4.2 180° Conduction Mode

#### **Operation:**
- Each switch conducts for 180°
- 60° phase shift between phases
- Simple control but high harmonic content

#### **Line-to-Line Voltage:**
```
vab(t) = (2√3Vdc/π) Σ[n=1,5,7,11,13,...] (1/n) sin(nωt + φn)
```

**Fundamental RMS (Line-to-Line):**
```
VAB1(rms) = (√6/π) Vdc = 0.78 Vdc
```

### 4.3 PWM Operation

#### **SPWM for Three-Phase:**
- Three sinusoidal references (120° apart)
- Single triangular carrier
- Independent control of each leg

#### **Output Characteristics:**
**For ma ≤ 1:**
```
VAN1(rms) = ma × (Vdc/(2√2))
VAB1(rms) = ma × (√3Vdc/(2√2))
```

#### **Overmodulation Region (ma > 1):**
- Non-linear relationship
- Increased harmonic content
- Maximum fundamental at ma ≈ 3.24

---

## 5. Multilevel Inverters

### 5.1 Need for Multilevel Inverters

#### **Advantages:**
- **Lower harmonic distortion**: More voltage levels
- **Reduced dv/dt**: Lower switching stress
- **Higher power capability**: Series connection of devices
- **Better power quality**: Closer to sinusoidal output

#### **Applications:**
- High-voltage motor drives
- Grid-tied renewable systems
- HVDC transmission
- Power quality applications

### 5.2 Diode-Clamped (Neutral Point Clamped)

#### **3-Level NPC Configuration:**
- Four switches per phase with clamping diodes
- Three voltage levels: +Vdc/2, 0, -Vdc/2
- Split DC link with neutral point

#### **Switching States:**
- **P State**: S1, S2 ON → vo = +Vdc/2
- **O State**: S2, S3 ON → vo = 0  
- **N State**: S3, S4 ON → vo = -Vdc/2

#### **Advantages:**
- Simple structure and control
- Established technology
- Good for medium voltage drives

#### **Disadvantages:**
- Unequal switch utilization
- Neutral point voltage fluctuation
- Complex for higher levels (>3)

### 5.3 Flying Capacitor (Capacitor-Clamped)

#### **3-Level FC Configuration:**
- Floating capacitors for voltage clamping
- Redundant switching states
- Natural voltage balancing capability

#### **Switching Strategy:**
- Multiple states for same output level
- Capacitor voltage balancing through state selection
- Phase-shifted PWM often used

#### **Advantages:**
- Modular structure
- Natural voltage balancing
- Suitable for higher levels

#### **Disadvantages:**
- Large number of capacitors
- Capacitor voltage monitoring required
- Higher cost and complexity

### 5.4 Cascaded H-Bridge (CHB)

#### **Configuration:**
- Multiple H-bridge units in series per phase
- Separate DC sources required
- Most suitable for high voltage applications

#### **For n H-bridges:**
- Voltage levels: 2n+1
- Total switches: 8n per phase
- Independent DC sources: n per phase

#### **Advantages:**
- Modular structure
- Easy to extend to higher levels
- Fault tolerance capability
- Excellent for high power applications

#### **Applications:**
- Medium voltage drives
- Grid-tied PV systems
- STATCOM applications

---

## 6. Control Strategies

### 6.1 Voltage Control Methods

#### **Amplitude Control:**
- **PWM**: Varies pulse width
- **Multiple PWM**: Several pulses per half cycle
- **Sinusoidal PWM**: Sinusoidal reference modulation

#### **Frequency Control:**
- Variable frequency operation
- Constant V/f control for motors
- Field-oriented control for high performance

### 6.2 Current Control

#### **Hysteresis Current Control:**
- Maintains current within hysteresis band
- Fast dynamic response
- Variable switching frequency

#### **Ramp Comparison Current Control:**
- Fixed switching frequency
- Good for parallel operation
- More complex implementation

#### **Predictive Current Control:**
- Uses system model for prediction
- Excellent dynamic response
- Requires accurate parameters

### 6.3 Vector Control

#### **Field-Oriented Control (FOC):**
- Decouples torque and flux control
- AC motor behaves like DC motor
- Requires coordinate transformations

#### **Direct Torque Control (DTC):**
- Direct control of torque and flux
- Fast torque response
- Simple implementation

---

## 7. Output Filters

### 7.1 Need for Output Filtering

#### **PWM Inverter Issues:**
- High-frequency switching harmonics
- dv/dt stress on motor windings
- EMI/EMC compliance requirements
- Common-mode voltages

### 7.2 L Filter

#### **Configuration:**
- Series inductor per phase
- Simple and economical
- First-order filtering

#### **Design Equations:**
```
L = Vdc/(8 × fs × ΔiL)
```
Where ΔiL is the peak-to-peak ripple current.

#### **Characteristics:**
- Current source behavior at output
- Good current ripple reduction
- Minimal voltage regulation

### 7.3 LC Filter

#### **Configuration:**
- Series inductor and shunt capacitor
- Second-order filtering
- Better harmonic attenuation

#### **Design Considerations:**
**Resonant Frequency:**
```
fr = 1/(2π√LC)
```

**Design Guidelines:**
- fr should be > 2×fref and < fs/10
- Damping may be required
- Consider load interaction

#### **Advantages:**
- Excellent high-frequency attenuation
- Voltage source behavior
- Good for long cable runs

#### **Disadvantages:**
- Resonance issues
- Higher cost and size
- Potential instability

### 7.4 LCL Filter

#### **Configuration:**
- Grid-side inductor Lg
- Capacitor C
- Inverter-side inductor Li

#### **Transfer Function:**
```
H(s) = 1/[LiLgCs³ + (Li+Lg)s]
```

#### **Design Process:**
1. Choose total inductance based on ripple requirements
2. Split between Li and Lg (typically 70%-30%)
3. Select capacitor for desired resonant frequency
4. Add damping if required

#### **Applications:**
- Grid-tied inverters
- Active filters
- High-power drives

---

## 8. Inverter Design Example

### 8.1 Design Specifications

**Design a single-phase PWM inverter for:**
- Output: 230V RMS, 50 Hz, 5 kW
- Input: 400V DC
- THD < 5%
- Efficiency > 95%

### 8.2 Design Process

#### **Step 1: Inverter Topology Selection**
- Single-phase full-bridge PWM inverter
- SPWM control with high switching frequency

#### **Step 2: Modulation Index Calculation**
```
Required V1(rms) = 230V
For full-bridge: V1(rms) = ma × (Vdc/√2)
ma = (230 × √2)/400 = 0.815
```
This is within linear range (ma < 1) ✓

#### **Step 3: Switching Frequency Selection**
```
For THD < 5%, choose fs = 10 kHz
mf = fs/fo = 10000/50 = 200
```
High mf ensures low harmonic distortion ✓

#### **Step 4: Switch Selection**
```
Output current: Io(rms) = P/Vo = 5000/230 = 21.7A
Peak current: Ip ≈ 1.4 × 21.7 = 30.4A
Switch voltage rating: > 400V

Choose: IGBTs rated 600V, 50A
```

#### **Step 5: Output Filter Design**
```
For L filter:
Ripple current limit: ΔiL = 10% × Io = 2.17A
L = Vdc/(8 × fs × ΔiL) = 400/(8 × 10000 × 2.17) = 2.3mH

Choose: L = 2.5mH
```

#### **Step 6: Loss Analysis**
```
Conduction losses: 2 × VCE(sat) × Io(avg) ≈ 2 × 2V × 15A = 60W
Switching losses: Estimate 100W at 10kHz
Total losses ≈ 160W
Efficiency = 5000/(5000+160) = 96.9% ✓
```

---

## 9. Advanced Inverter Topics

### 9.1 Grid-Tied Inverters

#### **Requirements:**
- **Synchronization**: Phase and frequency matching
- **Power Factor Control**: Unity or specified PF
- **Anti-Islanding**: Safety disconnection
- **Grid Code Compliance**: Voltage and frequency limits

#### **Control Features:**
- **Phase-Locked Loop (PLL)**: Grid synchronization
- **Current Control**: Power regulation
- **MPPT**: Maximum power point tracking (for PV)

### 9.2 Transformerless Inverters

#### **Advantages:**
- **Higher efficiency**: No transformer losses
- **Reduced size and weight**: No bulky transformer
- **Lower cost**: Eliminated transformer cost

#### **Challenges:**
- **Common-mode currents**: Ground leakage currents
- **Safety**: No galvanic isolation
- **EMI**: Higher electromagnetic interference

#### **Solutions:**
- **H5 Topology**: Additional switch for CM reduction
- **HERIC Topology**: Freewheeling path modification
- **NPC Topology**: Three-level operation

### 9.3 Interleaved Inverters

#### **Concept:**
- Multiple identical inverters in parallel
- Phase-shifted switching patterns
- Current sharing between modules

#### **Benefits:**
- **Reduced output ripple**: Ripple cancellation
- **Higher power capability**: Parallel operation  
- **Improved reliability**: Redundancy
- **Modular design**: Easy maintenance

---

## 10. Applications and Case Studies

### 10.1 Solar PV Inverters

#### **System Types:**
- **String Inverters**: Multiple panels to one inverter
- **Power Optimizers**: Module-level MPPT with string inverter
- **Microinverters**: One inverter per panel

#### **Key Features:**
- **MPPT Efficiency**: >99.5% tracking efficiency
- **CEC Efficiency**: >96% weighted efficiency
- **Grid Support**: Voltage and frequency support

### 10.2 Electric Vehicle Inverters

#### **Requirements:**
- **High power density**: Compact packaging
- **Wide speed range**: 0-15000 RPM operation
- **Bidirectional capability**: Motoring and regeneration
- **Automotive qualification**: Temperature and vibration

#### **Technology Trends:**
- **SiC devices**: Higher efficiency and frequency
- **Integrated design**: Motor and inverter integration
- **800V systems**: Higher voltage for fast charging

### 10.3 Industrial Motor Drives

#### **Applications:**
- **Pumps and fans**: Energy saving applications
- **Conveyors**: Precise speed control
- **Machine tools**: High-performance servo drives

#### **Features:**
- **Sensorless control**: Encoder-free operation
- **Energy recovery**: Regenerative braking
- **Network integration**: Industrial communication

---

## 11. Future Trends

### 11.1 Wide Bandgap Devices

#### **Silicon Carbide (SiC):**
- **Higher switching frequency**: Reduced filter size
- **Lower losses**: Improved efficiency
- **Higher temperature**: Reduced cooling requirements

#### **Gallium Nitride (GaN):**
- **Ultra-high frequency**: MHz operation possible
- **Very low losses**: Highest efficiency
- **Compact design**: Smallest form factors

### 11.2 Digital Control

#### **Microcontroller-Based:**
- **Flexible control**: Software-defined functionality
- **Adaptive algorithms**: Self-tuning parameters
- **Communication**: IoT and smart grid integration

#### **FPGA Implementation:**
- **High-speed control**: Nanosecond resolution
- **Parallel processing**: Multiple control loops
- **Custom algorithms**: Specialized implementations

### 11.3 Artificial Intelligence

#### **Machine Learning:**
- **Predictive maintenance**: Failure prediction
- **Adaptive control**: Self-optimizing systems
- **Grid integration**: Smart inverter functions

---

## Summary

Inverters are crucial power electronic circuits that enable the conversion of DC power to AC power with precise control over voltage, frequency, and power quality.

**Key Takeaways:**
1. **Multiple topologies available**: From simple square wave to complex multilevel
2. **PWM control essential**: For harmonic reduction and voltage control
3. **Filter design critical**: For power quality and EMC compliance
4. **Application-specific requirements**: Grid codes, efficiency, and reliability
5. **Technology evolution**: Wide bandgap devices and digital control

**Inverter Selection Criteria:**

| Application | Topology | Control | Key Requirements |
|-------------|----------|---------|------------------|
| UPS | Single-phase FB | SPWM | Low THD, reliability |
| Motor Drive | 3-phase VSI | SVPWM/FOC | Variable frequency |
| Grid-tied PV | Transformerless | Current control | High efficiency |
| HVDC | Multilevel | Advanced PWM | High voltage/power |

---

## Next Lecture
**Topic**: DC-DC Converters - Switching Power Supplies
**Reading Assignment**: Chapter 5, Sections 5.1-5.4
**Problem Set**: Inverter analysis and PWM design problems

---

## Practice Problems

**Problem 1**: A single-phase full-bridge inverter with Vdc = 200V operates in square wave mode at 60Hz. Calculate:
a) RMS value of output voltage
b) RMS value of fundamental component
c) THD of output voltage
d) Power delivered to a 10Ω resistive load

**Problem 2**: Design a sinusoidal PWM control for the inverter in Problem 1 to produce 120V RMS output at 60Hz. Determine:
a) Required modulation index
b) Switching frequency for mf = 21
c) Expected THD improvement

**Problem 3**: A three-phase PWM inverter with Vdc = 600V uses SPWM with ma = 0.8. Calculate:
a) Fundamental phase voltage (RMS)
b) Fundamental line-to-line voltage (RMS)  
c) Maximum possible output voltage
d) DC bus utilization ratio

**Problem 4**: Design an LC output filter for a PWM inverter with the following specifications:
- Switching frequency: 5 kHz
- Output frequency: 50 Hz
- Load current: 20A RMS
- Ripple current: <5% of load current
- Resonant frequency constraints: 100 Hz < fr < 500 Hz

**Problem 5**: Compare the advantages and disadvantages of a 3-level NPC inverter versus a conventional 2-level inverter for a 1 MW motor drive application.
