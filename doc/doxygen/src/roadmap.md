# Roadmap     {#roadmap}

The aim of the roadmap is to identify priority areas of RIOT development & enhancements.
For each area, some near-future plans and concrete next steps are indicated.
The text and items below are tentative, up for discussion, to be updated by regular pull requests.


# Network Stack High layers
(contact/steering: [Martine](https://github.com/miri64))

- ICN stack support clean-up
- discuss mid- and long-term plans for network stack maintenance & development (GNRC vs other supported stacks)
- revisit network time synchronization



# Network Stack Low layers
(contact/steering: [Peter](https://github.com/PeterKietzmann))

- Point-to-Point Protocol (PPP): finalize and merge `gnrc_ppp`



# Power Modes
(contact/steering: [Hauke](https://github.com/haukepetersen))

- concept to fix shell usage issue while LPM activated
- integrate generic power management functions in device driver APIs (netdev, SAUL, ...)
- more advanced LPM concepts:
  - sleeping for short periods (in cases where it is not feasible to switch to the idle thread and back) -> mitigate active waiting



# Peripheral drivers
(contact/steering: [Hauke](https://github.com/haukepetersen))

- cleanup and unification of low-level timer interfaces (`timer`, `rtt`, `rtc`)
- introduction of `spi_slave` interface
- introduction of `i2c_slave` interface



# Software Updates
(contact/steering: [Emmanuel](https://github.com/emmanuelsearch))

- Modularize to provide toolbox supporting other image storing (e.g. support external flash), transport (other than CoAP), crypto (e.g. secure element).
- riotboot support for architectures other than Cortex-M



# Documentation
(contact/steering: [Emmanuel](https://github.com/emmanuelsearch))

- Write and publish more RDMs



# Low-level Hardware Support
(contact/steering: [Alex](https://github.com/aabadie))

- radio support for TI SensorTag
- radio support for Silab Thunderboard



# Testing
(contact/steering: [Kaspar](https://github.com/kaspar030))

- automated network functionality tests (e.g. RPL + UDP/PING tests through border router, multi-hop) in IoTLAB dev sites?



# Security
(contact/steering: [Kaspar](https://github.com/kaspar030))

- RNG unified (secure, or basic), seeding
- RIOT default configuration = secure configuration (that's our goal/motto)


## 802.15.4 link layer security
(contact/steering: [chrysn](https://github.com/chrysn))

Current status: RIOT supports application provided keys,
with no guidance on how to (and no practical ways to) use that securely
(see [CVE-2021-41061](https://nvd.nist.gov/vuln/detail/CVE-2021-41061)).

Goal: Usably secure defaults.

- Figure out applicability of [RFC9031](https://www.rfc-editor.org/rfc/rfc9031) ("CoJP") to non-6TiSCH scenarios.
- Implement RFC9031 with any extensions needed for the MACs RIOT has.
- Provide tools to set up a recommended JRC, and to provision keys between it and the device at flash time.
  This may entail extensions to the build process, as CoJP requires per-device secrets.
