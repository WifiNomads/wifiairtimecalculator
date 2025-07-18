# WiFi Airtime Calculator - Complete Documentation

## Table of Contents
1. [About the Calculator](#1-about-the-calculator)
2. [How to Use the Calculator](#2-how-to-use-the-calculator)
3. [Graph and Results Explanation](#3-graph-and-results-explanation)
4. [Calculations and Formulas](#4-calculations-and-formulas)

---

## 1. About the Calculator

### 1.1 What is WiFi Airtime?
WiFi airtime refers to the total time required to transmit a data frame over the wireless medium, including all protocol overhead, timing intervals, and control mechanisms. Understanding airtime is crucial for:
- **Network Performance Analysis**: Calculating actual throughput and efficiency
- **Capacity Planning**: Determining how many devices can be supported
- **Quality of Service (QoS)**: Understanding latency and delay characteristics
- **Protocol Optimization**: Evaluating different configuration impacts

### 1.2 What This Calculator Does
The WiFi Airtime Calculator provides IEEE 802.11 standards-compliant airtime calculations for:
- **All WiFi Generations**: Legacy OFDM (802.11a/g), HT (802.11n), VHT (802.11ac), HE (802.11ax)
- **Multiple PHY Modes**: Single-user and multi-user OFDMA transmissions
- **Complete Protocol Overhead**: Including all timing components and control frames
- **Real-world Scenarios**: Configurable parameters matching actual deployments

### 1.3 What's Included in Calculations

#### Core Components:
- **DIFS/AIFS (Distributed/Arbitration Inter-Frame Spacing)**: Pre-transmission wait time
- **Backoff Period**: Random contention window for collision avoidance
- **RTS/CTS Protection** (Optional): Request-to-Send/Clear-to-Send handshake
- **Preamble and Headers**: Physical layer signaling and MAC headers
- **Data Transmission**: Actual payload with proper encoding
- **SIFS (Short Inter-Frame Spacing)**: Inter-frame gaps
- **Acknowledgment**: ACK or Block-ACK response

#### Advanced Features:
- **MIMO Support**: Multiple spatial streams (1-8 streams)
- **Channel Bonding**: 20/40/80/160 MHz bandwidth options
- **Guard Interval Optimization**: Variable GI for different scenarios
- **QoS Access Categories**: Different priority levels (VO, VI, BE, BK)
- **OFDMA Resource Units**: Multi-user resource allocation
- **Control Frame Rate Selection**: Configurable control frame data rates

---

## 2. How to Use the Calculator

### 2.1 Scenario Selection

#### **Scenario 1: OFDM (non-HT) - Legacy 802.11a/g**
- **Use Case**: Legacy devices, compatibility mode
- **Characteristics**: 
  - Fixed 20 MHz bandwidth
  - Single spatial stream only
  - 0.8 μs guard interval (fixed)
  - Data rates: 6, 9, 12, 18, 24, 36, 48, 54 Mbps
- **When to Use**: Legacy device analysis, backward compatibility testing

#### **Scenario 2: HT or VHT - 802.11n/ac**
- **Use Case**: Modern WiFi 4/5 devices
- **Characteristics**:
  - Bandwidth: 20/40/80/160 MHz (5 GHz), 20/40 MHz (2.4 GHz)
  - Spatial streams: 1-8
  - Guard interval: 0.4 μs (short) or 0.8 μs (long)
  - MCS 0-9 (no 1024-QAM)
- **When to Use**: Most current WiFi deployments, enterprise networks

#### **Scenario 3: HE (OFDMA disabled) - 802.11ax Single User**
- **Use Case**: WiFi 6 single-user transmissions
- **Characteristics**:
  - All bandwidth options available
  - Enhanced guard intervals: 0.8, 1.6, 3.2 μs
  - MCS 0-11 (includes 1024-QAM)
  - Improved efficiency features
- **When to Use**: WiFi 6 performance analysis, single-device optimization

#### **Scenario 4: DL OFDMA - 802.11ax Multi-User**
- **Use Case**: WiFi 6 multi-user OFDMA transmissions
- **Characteristics**:
  - Resource Unit (RU) based allocation
  - Multiple users simultaneously
  - Coordinated transmissions
  - Enhanced signaling overhead
- **When to Use**: Dense deployment analysis, multi-user efficiency studies

### 2.2 Input Parameters Explained

#### **Frequency Band**
- **2.4 GHz**: Maximum 40 MHz bandwidth, higher propagation, more interference
- **5 GHz**: Up to 160 MHz bandwidth, better performance, more spectrum

#### **Channel Bandwidth**
- **20 MHz**: Basic bandwidth, maximum compatibility
- **40 MHz**: 2x subcarriers, ~2x throughput potential
- **80 MHz**: 4x subcarriers, ~4x throughput potential  
- **160 MHz**: 8x subcarriers, ~8x throughput potential

#### **Access Category (QoS)**
| Category | AIFSN | CW Min | CW Max | Use Case |
|----------|-------|--------|--------|----------|
| VO (Voice) | 2 | 3 | 7 | Real-time voice |
| VI (Video) | 2 | 7 | 15 | Real-time video |
| BE (Best Effort) | 3 | 15 | 1023 | General data |
| BK (Background) | 7 | 15 | 1023 | Bulk transfers |

#### **Contention Window (CW)**
- **Lower Values**: Less delay, higher collision risk
- **Higher Values**: More delay, lower collision risk
- **Range**: Depends on access category
- **Input**: Average number of backoff slots

#### **Spatial Streams**
- **1 Stream**: Basic SISO configuration
- **2 Streams**: 2x2 MIMO, ~2x throughput
- **4 Streams**: 4x4 MIMO, ~4x throughput
- **8 Streams**: 8x8 MIMO, maximum throughput

#### **Guard Interval**
- **Legacy**: 0.8 μs (fixed)
- **HT/VHT**: 0.4 μs (short GI) or 0.8 μs (long GI)
- **HE**: 0.8 μs, 1.6 μs, or 3.2 μs
- **Trade-off**: Shorter GI = higher efficiency but requires better channel conditions

#### **Control Frame Rate**
- **6 Mbps**: Most reliable, maximum range
- **12-24 Mbps**: Balanced reliability/speed
- **48-54 Mbps**: Fastest but requires good signal

#### **MCS (Modulation and Coding Scheme)**
| MCS | Modulation | Coding Rate | Signal Quality Required |
|-----|------------|-------------|------------------------|
| 0 | BPSK | 1/2 | Poor (-82 dBm) |
| 1 | QPSK | 1/2 | Fair (-79 dBm) |
| 2 | QPSK | 3/4 | Fair (-77 dBm) |
| 3 | 16-QAM | 1/2 | Good (-74 dBm) |
| 4 | 16-QAM | 3/4 | Good (-70 dBm) |
| 5 | 64-QAM | 2/3 | Very Good (-66 dBm) |
| 6 | 64-QAM | 3/4 | Very Good (-65 dBm) |
| 7 | 64-QAM | 5/6 | Excellent (-64 dBm) |
| 8 | 256-QAM | 3/4 | Excellent (-59 dBm) |
| 9 | 256-QAM | 5/6 | Excellent (-57 dBm) |
| 10 | 1024-QAM | 3/4 | Perfect (-54 dBm) |
| 11 | 1024-QAM | 5/6 | Perfect (-52 dBm) |

#### **A-MPDU Size**
- **Small (64-1500 bytes)**: Lower latency, less efficiency
- **Medium (1500-4000 bytes)**: Balanced performance
- **Large (4000-65535 bytes)**: Maximum efficiency, higher latency

#### **RTS/CTS Protection**
- **Enabled**: Prevents hidden node collisions, adds overhead
- **Disabled**: Lower overhead, potential for collisions

#### **Users (OFDMA Only)**
Number of simultaneous users in multi-user transmission:
- **More Users**: Better spectrum efficiency, higher coordination overhead
- **Fewer Users**: Lower overhead, higher per-user throughput

---

## 3. Graph and Results Explanation

### 3.1 Results Table

The calculator provides two key metrics:

#### **Duration including DIFS & CW**
- **What it shows**: Complete transmission time including all overhead
- **Includes**: DIFS/AIFS + Backoff + Protection + Data + ACK
- **Use case**: Real-world performance analysis

#### **Duration excluding DIFS & CW**  
- **What it shows**: Transmission time without random access overhead
- **Includes**: Protection + Data + ACK (no DIFS/Backoff)
- **Use case**: Pure protocol efficiency analysis

#### **Throughput Calculation**
```
Throughput (Mbps) = (A-MPDU size × 8 bits) / (Total Duration × 10^-6 seconds) / 10^6
```

**Step-by-step verification:**
```
1. A-MPDU size × 8 = Total bits transmitted
2. Total Duration × 10^-6 = Duration in seconds (since duration is in microseconds)
3. Bits ÷ Seconds = Bits per second
4. Bits per second ÷ 10^6 = Megabits per second (Mbps)
```

**Example calculation:**
```
A-MPDU size = 1500 bytes
Total Duration = 100 microseconds

Step 1: 1500 × 8 = 12,000 bits
Step 2: 100 × 10^-6 = 0.0001 seconds  
Step 3: 12,000 ÷ 0.0001 = 120,000,000 bits/second
Step 4: 120,000,000 ÷ 10^6 = 120 Mbps
```

**✅ Formula is CORRECT** - This matches the implementation in the calculator code.

### 3.2 Airtime Bar Graph

The horizontal bar chart shows the duration breakdown of each component:

#### **Channel Access Components** (Only in "including DIFS & CW"):
- **DIFS/AIFS**: Inter-frame spacing before transmission
- **Backoff**: Random wait time for collision avoidance

#### **Protection Components** (If RTS/CTS enabled):
- **RTS Preamble**: Legacy preamble for RTS frame
- **RTS**: Request-to-Send frame transmission
- **SIFS**: Short inter-frame spacing
- **CTS Preamble**: Legacy preamble for CTS frame  
- **CTS**: Clear-to-Send frame transmission
- **SIFS**: Another short inter-frame spacing

#### **Data Transmission Components**:
- **Data Preamble**: PHY preamble (varies by scenario)
- **A-MPDU**: Actual data transmission time
- **SIFS**: Short inter-frame spacing

#### **Acknowledgment Components**:
- **ACK Preamble**: Legacy preamble for acknowledgment
- **ACK/B-ACK**: Acknowledgment frame transmission

### 3.3 Graph Interpretation

#### **Efficiency Analysis**:
- **Large Data Portion**: High efficiency
- **Large Overhead Portions**: Low efficiency, optimization needed

#### **Bottleneck Identification**:
- **Long Preambles**: Consider higher-order modulation
- **Long Protection**: Evaluate RTS/CTS necessity
- **Long Backoff**: Consider access category optimization

---

## 4. Calculations and Formulas

### 4.1 Timing Parameters (IEEE 802.11 Compliant)

#### **Basic Timing Values**
```
SIFS = 16 μs (5 GHz), 10 μs (2.4 GHz)
Slot Time = 9 μs
Legacy Symbol Duration = 4 μs
Legacy Preamble = 20 μs (L-STF + L-LTF + L-SIG = 8 + 8 + 4)
```

#### **Inter-Frame Spacing Calculations**
```
DIFS = SIFS + 2 × Slot Time = SIFS + 18 μs
AIFS = SIFS + AIFSN × Slot Time

Where AIFSN:
- VO: 2 → AIFS = SIFS + 18 μs  
- VI: 2 → AIFS = SIFS + 18 μs
- BE: 3 → AIFS = SIFS + 27 μs
- BK: 7 → AIFS = SIFS + 63 μs
```

#### **Backoff Calculation**
```
Backoff Duration = CW_avg × Slot Time

Where CW_avg = Average Contention Window slots (user input)
```

### 4.2 Preamble Duration Calculations

#### **Legacy OFDM (Scenario 1)**
```
Preamble Duration = 20 μs (fixed)
```

#### **HT/VHT (Scenario 2)**
```
Preamble Duration = Legacy Preamble + HT-SIG + HT-STF + HT-LTF
                  = 20 + 8 + 4 + (4 × NSS) μs

Where NSS = Number of Spatial Streams
```

#### **HE (Scenarios 3 & 4)**
```
Preamble Duration = Legacy + RL-SIG + HE-SIG-A + HE-SIG-B + HE-STF + HE-LTF
                  = 20 + 4 + 8 + HE-SIG-B + 4 + (6.4 × NSS) μs

HE-SIG-B Duration (OFDMA only):
= ceil(HE-SIG-B bits / 26) × 4 μs
```

### 4.3 Data Transmission Calculations

#### **Subcarrier Counts (IEEE Standards)**
```
Non-HE (802.11a/g/n/ac):
- 20 MHz: 52 data subcarriers
- 40 MHz: 108 data subcarriers  
- 80 MHz: 234 data subcarriers
- 160 MHz: 468 data subcarriers

HE (802.11ax):
- 20 MHz: 234 data subcarriers
- 40 MHz: 468 data subcarriers
- 80 MHz: 980 data subcarriers
- 160 MHz: 1960 data subcarriers
```

#### **Symbol Duration**
```
Non-HE Symbol Duration = 3.2 + GI μs
HE Symbol Duration = 12.8 + GI μs
```

#### **Data Rate Calculation**
```
Data Bits per Symbol = Subcarriers × Bits_per_Subcarrier × Coding_Rate × Spatial_Streams

Where:
- Bits_per_Subcarrier: From MCS table (1,2,4,6,8,10)
- Coding_Rate: From MCS table (1/2, 2/3, 3/4, 5/6)
```

#### **Data Duration Calculation**
```
Data Bits = SERVICE(16) + A-MPDU(bytes × 8) + TAIL(6)
Data Symbols = ceil(Data Bits / Data_Bits_per_Symbol) 
Data Duration = Data_Symbols × Symbol_Duration
```

### 4.4 Control Frame Calculations

#### **Control Frame Parameters**
```
RTS Frame: 20 bytes → 160 + 16 + 6 = 182 bits total
CTS Frame: 14 bytes → 112 + 16 + 6 = 134 bits total  
ACK Frame: 34 bytes → 272 + 16 + 6 = 294 bits total

Control Frame Bits per Symbol = 52 × Modulation_Bits × Coding_Rate
Control Frame Duration = ceil(Total_Bits / Bits_per_Symbol) × 4μs
```

### 4.5 OFDMA Resource Unit Calculations (Scenario 4)

#### **IEEE 802.11ax Resource Unit Concepts**
OFDMA (Orthogonal Frequency Division Multiple Access) allows multiple users to transmit simultaneously using different subcarriers. Resource Units (RUs) are predefined allocations of subcarriers assigned to each user.

#### **Resource Unit Types in 802.11ax:**
- **26-tone RU**: 26 subcarriers per user
- **52-tone RU**: 52 subcarriers per user  
- **106-tone RU**: 106 subcarriers per user
- **242-tone RU**: 242 subcarriers per user
- **484-tone RU**: 484 subcarriers per user
- **996-tone RU**: 996 subcarriers per user
- **2×996-tone RU**: 1992 subcarriers per user

#### **How RU Allocation Works in the Calculator**

The calculator uses predefined RU allocation tables based on IEEE 802.11ax specifications:

```javascript
const ofdma_map = {
    20: {
        1: {data_sub:234, bits_sigb:20},  // Single user = full bandwidth
        2: {data_sub:117, bits_sigb:40},  // 2 users = ~106-tone RUs each  
        4: {data_sub:52, bits_sigb:80},   // 4 users = 52-tone RUs each
        9: {data_sub:26, bits_sigb:180}   // 9 users = 26-tone RUs each
    },
    // ... similar for 40MHz, 80MHz, 160MHz
};
```

#### **Example: 80 MHz Channel with Different User Counts**

**Case 1: 2 Users in 80 MHz**
```
Total subcarriers available: 980 (80 MHz HE)
Allocation: 2 × 484-tone RUs (approximately)
Data subcarriers per user: 490
HE-SIG-B overhead: 40 bits
```

**Case 2: 4 Users in 80 MHz**  
```
Total subcarriers available: 980 (80 MHz HE)
Allocation: 4 × 242-tone RUs (approximately)
Data subcarriers per user: 245
HE-SIG-B overhead: 80 bits
```

**Case 3: 8 Users in 80 MHz**
```
Total subcarriers available: 980 (80 MHz HE)  
Allocation: 8 × 106-tone RUs (approximately)
Data subcarriers per user: 117
HE-SIG-B overhead: 160 bits
```

#### **Step-by-Step OFDMA Calculation Process**

**Step 1: RU Selection**
```
Based on (bandwidth, users), lookup predefined RU allocation:
- data_sub = subcarriers per user from ofdma_map
- bits_sigb = HE-SIG-B overhead bits
```

**Step 2: Data Rate per User**
```
Data_Bits_per_Symbol_per_User = data_sub × MCS_bits × Coding_Rate × Spatial_Streams

Example for MCS 7, 1 spatial stream:
- 2 users, 80MHz: 490 × 6 × (5/6) × 1 = 2450 bits/symbol/user
- 4 users, 80MHz: 245 × 6 × (5/6) × 1 = 1225 bits/symbol/user
```

**Step 3: Data Duration Calculation**
```
Per_User_Data_Bits = 16 + A-MPDU_bytes × 8 + 6
Per_User_Symbols = ceil(Per_User_Data_Bits / Data_Bits_per_Symbol_per_User)
Data_Duration = Per_User_Symbols × HE_Symbol_Duration

Note: All users transmit simultaneously, so total duration = individual user duration
```

**Step 4: HE-SIG-B Overhead Calculation**
```
HE-SIG-B encodes resource allocation information for all users:
- Which RUs are assigned to which users
- MCS information per user
- Power allocation details

HE-SIG-B_Duration = ceil(bits_sigb / 26) × 4μs
Where 26 = MCS0 bits per symbol for signaling
```

#### **Detailed Comparison: 2 Users vs 4 Users (80 MHz Example)**

**Scenario: 80 MHz, A-MPDU=1500 bytes, MCS 7, 1 spatial stream**

**2 Users Configuration:**
```
Resource Allocation:
- Each user gets: 490 subcarriers (≈484-tone RU)
- Data rate per user: 490 × 6 × (5/6) = 2450 bits/symbol
- HE-SIG-B overhead: 40 bits

Data Calculation per User:
- Total bits: 16 + (1500 × 8) + 6 = 12,022 bits
- Symbols needed: ceil(12,022 / 2450) = 5 symbols
- Data duration: 5 × (12.8 + GI) μs

HE-SIG-B Duration:
- ceil(40 / 26) × 4 = 2 × 4 = 8 μs

Total Preamble: 20 + 4 + 8 + 8 + 4 + (6.4 × NSS) = 44 + 6.4 = 50.4 μs
```

**4 Users Configuration:**
```
Resource Allocation:
- Each user gets: 245 subcarriers (≈242-tone RU)  
- Data rate per user: 245 × 6 × (5/6) = 1225 bits/symbol
- HE-SIG-B overhead: 80 bits

Data Calculation per User:
- Total bits: 16 + (1500 × 8) + 6 = 12,022 bits
- Symbols needed: ceil(12,022 / 1225) = 10 symbols  
- Data duration: 10 × (12.8 + GI) μs

HE-SIG-B Duration:
- ceil(80 / 26) × 4 = 4 × 4 = 16 μs

Total Preamble: 20 + 4 + 8 + 16 + 4 + (6.4 × NSS) = 52 + 6.4 = 58.4 μs
```

#### **Key OFDMA Observations:**

**Efficiency Trade-offs:**
- **2 Users**: Higher per-user throughput, less signaling overhead
- **4 Users**: Lower per-user throughput, more signaling overhead, better spectrum utilization

**Overhead Impact:**
- More users → More HE-SIG-B bits → Longer preamble
- Fewer subcarriers per user → More symbols needed → Longer data transmission

**Real-world Implications:**
- **Small Packets**: More users may be inefficient due to overhead
- **Large Packets**: More users can improve overall efficiency
- **Mixed Traffic**: Dynamic allocation based on queue lengths

### 4.6 Total Airtime Calculation

#### **Complete Formula**
```
Total Airtime = AIFS + Backoff + Protection_Overhead + Data_Transmission + ACK_Overhead

Where:
Protection_Overhead = 0 (if disabled) OR 
                     Legacy_Preamble + RTS + SIFS + Legacy_Preamble + CTS + SIFS

Data_Transmission = Data_Preamble + Data_Duration  

ACK_Overhead = SIFS + Legacy_Preamble + ACK_Duration
```

#### **Throughput Calculation**
```
Throughput_including_overhead = (A-MPDU_bytes × 8) / (Total_Airtime_μs × 10^-6) / 10^6 Mbps

Throughput_excluding_contention = (A-MPDU_bytes × 8) / (Airtime_without_AIFS_Backoff_μs × 10^-6) / 10^6 Mbps
```

### 4.7 MCS Parameter Table

| MCS | Modulation | Coding | Bits/Subcarrier | Coding Rate |
|-----|------------|--------|------------------|-------------|
| 0 | BPSK | 1/2 | 1 | 0.5 |
| 1 | QPSK | 1/2 | 2 | 0.5 |
| 2 | QPSK | 3/4 | 2 | 0.75 |
| 3 | 16-QAM | 1/2 | 4 | 0.5 |
| 4 | 16-QAM | 3/4 | 4 | 0.75 |
| 5 | 64-QAM | 2/3 | 6 | 0.667 |
| 6 | 64-QAM | 3/4 | 6 | 0.75 |
| 7 | 64-QAM | 5/6 | 6 | 0.833 |
| 8 | 256-QAM | 3/4 | 8 | 0.75 |
| 9 | 256-QAM | 5/6 | 8 | 0.833 |
| 10 | 1024-QAM | 3/4 | 10 | 0.75 |
| 11 | 1024-QAM | 5/6 | 10 | 0.833 |

---

## 5. IEEE Standards Compliance

This calculator implements calculations according to:
- **IEEE 802.11-2020**: Main standard for WiFi protocols
- **IEEE 802.11ax-2021**: WiFi 6 specific amendments
- **IEEE 802.11ac-2013**: WiFi 5 specific amendments  
- **IEEE 802.11n-2009**: WiFi 4 specific amendments

All timing parameters, subcarrier counts, preamble structures, and protocol behaviors match the official IEEE specifications for accurate real-world airtime prediction.

---

*This documentation provides complete technical details for understanding and using the WiFi Airtime Calculator effectively. For additional questions or advanced use cases, refer to the specific IEEE 802.11 standards documentation.*
