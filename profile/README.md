# Æthernet

**Cloud connectivity infrastructure for IoT devices and connected applications.**

Æthernet provides a secure transport layer between devices, applications, and backends. It handles the network infrastructure and protocol logic so product teams can keep their business logic and databases in their own stack instead of building and operating a device backend from scratch.

It is designed for embedded, desktop, mobile, and web clients, including systems that operate over unstable, high-latency, or bandwidth-constrained networks.

[Website](https://aethernet.io) · [Technology](https://aethernet.io/technology) · [Documentation](https://aethernet.io/documentation) · [Integration tutorials](https://aethernet.io/tutorial) · [Examples](https://github.com/aethernetio/aethernet-examples)

## What Æthernet handles

- infrastructure maintenance, scaling, replication, and failover;
- device onboarding, registration, identity, and hierarchy management;
- end-to-end encrypted messaging and access control;
- routing, endpoint selection, retries, and recovery after network changes;
- session and connection logic for unstable networks;
- delivery policies and short-term buffering for offline clients;
- traffic quotas and protection against registration abuse;
- transport-specific connectivity and power-saving behavior.

## How it works

### Stateless, no-handshake requests

After registration, a normal request is a single message containing the information required for authentication, encryption, and delivery. It does not require a preliminary session handshake. This reduces connection overhead and allows a client to recover quickly after packet loss, a transport change, or an unavailable endpoint.

### Thick client

Connectivity logic runs in the client library. The client can select endpoints, retry or duplicate requests, switch transports, and react to conditions that only the device can observe. Application code uses the same messaging model while the client handles the network path.

### Personal Cloud and endpoint switching

Each client receives a dynamically selected subset of geographically distributed Æthernet servers. The client can contact these endpoints sequentially or simultaneously and switch when latency or availability changes. The cloud can be reconfigured for location, load balancing, maintenance, or failure recovery.

### Separate registration and working clouds

New clients register through a dedicated registration cloud. Registered clients exchange operational traffic through the working cloud. Keeping these roles separate limits registration-specific state and allows the data plane to remain lightweight.

### Self-provisioning and identity

Clients can register without manual credential installation. Registration uses a three-step stateless flow and an adaptive Proof-of-Work challenge intended to reduce automated registration abuse while remaining practical for constrained devices. Each client receives a permanent UID, a master key, and its initial Personal Cloud.

### End-to-end security

Payloads are encrypted between clients. Master keys are not transferred to working servers; server-specific keys are derived from the client master key. Æthernet uses established cryptographic libraries and keeps application data encrypted while relays route it.

### Hierarchical management

Every client belongs to a parent-child hierarchy. An application server is itself an Æthernet client and can register children, assign quotas, control messaging permissions, and receive lifecycle events through the same protocol instead of maintaining a separate device-management API.

## SDKs

| Platform | Repository | Integration |
| --- | --- | --- |
| C / C++ | [aether-client-cpp](https://github.com/aethernetio/aether-client-cpp) | CMake, desktop, embedded, ESP-IDF, PlatformIO |
| Arduino / ESP32 | [aether-client-arduino-library](https://github.com/aethernetio/aether-client-arduino-library) | Arduino library |
| Java | [client-java](https://github.com/aethernetio/client-java) | Java / Gradle |
| TypeScript | [client-ts](https://github.com/aethernetio/client-ts) | Node.js and browser |

For runnable integrations, see [aethernet-examples](https://github.com/aethernetio/aethernet-examples). Detailed build requirements and supported environments are documented in the relevant SDK repository and in the [client environment documentation](https://aethernet.io/documentation).

## Networks and transports

Æthernet uses one messaging model across different network paths. Available integrations include:

- UDP / DTLS;
- TCP / TLS;
- HTTP / HTTPS;
- WebSocket / WSS;
- Ethernet and Wi-Fi;
- NB-IoT, LTE-M, 2G, and NTN cellular;
- LoRa and LoRaWAN;
- gateway-connected BLE, Zigbee, and Z-Wave networks.

Transport and hardware availability depends on the client library and adapter. Check the relevant repository before selecting a production target.

## Open-source components

- [Æthernet Examples](https://github.com/aethernetio/aethernet-examples): runnable client and device integrations.
- [Æthernet Numeric](https://github.com/aethernetio/aethernet-numeric): compact numeric types for constrained C++ systems.
- [Æthernet Compression](https://github.com/aethernetio/aethernet-compression): experimental compression for small structured messages.
- [Æthernet Gateway](https://github.com/aethernetio/aether-gateway): connectivity bridge for non-IP and constrained clients.
- [Temperature Sensor](https://github.com/aethernetio/temperature-sensor): an ESP32-based reference device.

## Get started

1. Choose a client library from the table above.
2. Follow the corresponding [integration tutorial](https://aethernet.io/tutorial).
3. Run an example from [aethernet-examples](https://github.com/aethernetio/aethernet-examples).
4. Use the [developer documentation](https://aethernet.io/documentation) for architecture and API details.

Questions and bug reports belong in the issue tracker of the relevant repository.
