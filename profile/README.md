**Æthernet** is designed as a ready-to-use cloud infrastructure service that acts as a secure transport layer, allowing developers to focus entirely on their application's business logic rather than building and maintaining backend systems

Here is a list of the complex engineering and operational tasks that Æthernet handles out-of-the-box, eliminating the need for you to develop them yourself:
*   **Infrastructure Maintenance and Scaling (Zero Ops)**
*   **Device Onboarding and Registration**
*   **Security and Cryptography**
*   **Dynamic Routing and Failover**
*   **Power and Energy Management**
*   **Session Management in Unstable Networks**
*   **Offline Message Buffering**
*   **DDoS Protection and Abuse Prevention**
# Main technical points of Æthernet

**1. Client Architecture and Resource Optimization**

*   **Thick Client:** On-device logic autonomously manages multi-transport switching and AP-specific power-saving (e.g., Wi-Fi DTIM, TWT) without relying on a central broker
*   **Object System and Distillation:** Dev-time pre-serialization eliminates runtime constructors, enabling zero-allocation deserialization and a minimal <300 KB binary footprint
*   **Specialized Numeric Types:** Custom types (TieredInt, Fixed, Exponent) deliver overflow-safe, zero-FPU arithmetic and logarithmic compression to drastically save RAM
*   **Zero-overhead Telemetry:** Compile-time macros physically strip string identifiers, logging execution metrics with zero CPU overhead and minimal flash consumption

**2. Network Protocol and Data Transmission**

*   **Native Stateless Protocol:** A handshake-free protocol embeds per-request cryptographic authentication, completely eliminating session states for high-loss networks
*   **Anti-Queue Paradigm:** Stateless relays buffer E2E-encrypted payloads for a strict 10-second maximum, rejecting traditional stateful store-and-forward brokers
*   **Repeat Message Optimization:** Recurring payloads use a secure 4-byte hash of the previous request, replacing easily spoofed TCP keep-alives and minimizing bandwidth

**3. Cloud Architecture and Routing**

*   **Personal Cloud and Hot Swapping:** Clients dynamically balance traffic across a personalized, geo-distributed relay subset, executing millisecond-level hot-swapping upon latency spikes
*   **Two Cloud Environment and Lightweight Relays:** Segregating registration nodes from stateless data planes enables cost-effective scaling and zero-downtime rolling updates

**4. Security and Identity Management**

*   **Self-Provisioning with Adaptive Proof-of-Work:** Headless devices autonomously register via an adaptively scaled, MCU-friendly bcrypt challenge (4 KB RAM) to thwart Sybil attacks
*   **Zero-Trust Cryptography and Key Derivation:** Local Master Keys utilize HKDF to derive ephemeral ChaCha20-Poly1305 keys per server, ensuring Perfect Forward Secrecy without vulnerable TLS certificates
*   **Hierarchical Management and Monetary Quotas:** Routing and abuse mitigation are governed natively by a protocol-level parent-child tree using automated monetary quotas instead of REST APIs

# System requirements and capabilities

OS and architecture support

- Compilers: C++17-compliant: GCC, LLVM, MSVC
- OS and CPU:
  - Windows (x86, x64)
  - macOS (x86_64)
  - Ubuntu/Debian (x86, x64, RISC-V)
  - Raspberry Pi OS (Pi 3, 5), Orange Pi OS (RISC-V)
  - OpenWrt (MIPS Linkit Smart 7688)
  - FreeBSD (x64)
  - Debian on IBM s390x
  - RHEL9 on IBM POWER
  - Solaris (x64)
  - QNX
- Toolchains: Arduino (ARM, Xtensa, RISC-V), ESP-IDF (Xtensa, RISC-V), MSBuild, Xcode, CMake (*nix-based, windows)

## Communication technologies and adapters

- Ethernet: Wired, full real-time, no credentials
- Wi-Fi: SSID+password, power saving (TWT Wi-Fi 6, DTIM)
- LAN: UDP/TCP direct, broadcast discovery, buffer-role for offline
- GSM: BG95, BG77, BG770, SIM7070A/SIM7000A, nRF9151; NB-IoT/LTE-M/2G
- Satellite - GSM NTN-IoT (Skylo)
- LoRa: SX1262 (client / gateway), SX1303 (gateway)
  1. Via LoRaWAN
  2. Through our own real-time protocol over LoRa
- BLE/Zigbee/Z-Wave: Via gateway
- 2.4 GHz proprietary protocol similar to BLE, but for real-time
- Iridium satellite: For extreme remote

## Microcontrollers and ecosystems

- MCU: ESP32, Raspberry Pi, Orange Pi, STM32, Nordic (nRF9151), ARM ARM/Xtensa/RISC-V, MIPS Links Smart 7688
- Min requirements for C++:
  - RAM 30 KB
  - ROM 1 Kb bytes
  - Binary 300 KB (Windows)
- Wrappers:
  - C-interface (simplified API),
  - Objective-C
  - Swift
  - Java-JNI
  - WASM
- Ecosystems: CMake, Arduino Studio, VS Code+PlatformIO, Microsoft Visual Studio 2026

# How to start
**1. You can learn more about our technology on our [website](https://aethernet.io/technology)**  
**2. To integrate our library into your project, follow our [tutorials](https://aethernet.io/tutorial) or the guidelines in the related repositories:**
* [C/C++](https://github.com/aethernetio/aether-client-cpp)
* [Arduino (C/C++)](https://github.com/aethernetio/aether-client-arduino-library)
* [Java](https://github.com/aethernetio/client-java)
* [TypeScript](https://github.com/aethernetio/client-ts)

**3. For a deeper understanding of the platform and additional integration help, see our [developer documentation](https://aethernet.io/documentation)**
