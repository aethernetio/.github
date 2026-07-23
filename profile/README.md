# Æthernet

Æthernet is a managed connectivity layer for embedded devices, web, mobile, and desktop applications. It provides secure real-time messaging without requiring every product team to build and operate its own device backend.

The protocol is designed for unstable and bandwidth-constrained networks. Each request carries the information needed for authentication, encryption, and delivery, while clients can switch endpoints when network conditions change.

[Website](https://aethernet.io) · [Documentation](https://aethernet.io/documentation) · [Tutorials](https://aethernet.io/tutorial) · [Examples](https://github.com/aethernetio/aethernet-examples)

## SDKs

| Platform | Repository | Status |
| --- | --- | --- |
| C++ | [aether-client-cpp](https://github.com/aethernetio/aether-client-cpp) | CMake, desktop, ESP-IDF, PlatformIO |
| Arduino / ESP32 | [aether-client-arduino-library](https://github.com/aethernetio/aether-client-arduino-library) | Arduino library |
| Java | [client-java](https://github.com/aethernetio/client-java) | Gradle |
| TypeScript | [client-ts](https://github.com/aethernetio/client-ts) | Node.js and browser |

## What Æthernet handles

- device self-provisioning and identity;
- end-to-end encrypted messaging;
- endpoint selection, retry, and recovery on unstable networks;
- request-response and fire-and-forget communication;
- access control and device-to-device messaging;
- bandwidth-aware operation for cellular IoT and constrained devices.

## Start with an example

The [examples repository](https://github.com/aethernetio/aethernet-examples) contains runnable integrations for C++, Arduino/ESP32, Java, and TypeScript. Each SDK repository also documents its own build and installation requirements.

## Related libraries

- [Æthernet Numeric](https://github.com/aethernetio/aethernet-numeric): compact numeric types for constrained C++ systems.
- [Æthernet Compression](https://github.com/aethernetio/aethernet-compression): experimental small-message dictionary modeling.
- [Æthernet Gateway](https://github.com/aethernetio/aether-gateway): bridge for non-IP clients.

Questions and bug reports belong in the issue tracker of the relevant repository.
