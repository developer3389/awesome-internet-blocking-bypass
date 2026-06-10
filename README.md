# Awesome Censorship-DPI-Bypass

A curated list of censorship-DPI-bypass tools.
 
> [!NOTE]
> **Scope**  
> This list is focused on censorship circumvention and traffic resilience. While some included tools (e.g., Tor, Whonix) provide strong anonymity and privacy, their primary inclusion here is based on their effectiveness in bypassing network-level filtering.

# Table of Contents
- 🟢[Foundation: Minimalist 200-Line Core](#foundation-minimalist-200-line-core)🟢
- [VPN Industry Standards](#vpn-industry-standards)
- [About DNS](#about-dns)
- [Proxy-based Anti-Censorship](#proxy-based-anti-censorship)
- [QUIC-based Proxy Tools](#quic-based-proxy-tools)
- [XRAY Ecosystem](#xray-ecosystem)
- [Overlay Networks](#overlay-networks)
  - [Tor](#tor)
  - [Tor Pluggable Transports](#tor-pluggable-transports)
  - [I2P](#i2p)
- [Encrypted Mesh Networks](#encrypted-mesh-networks)
- [Content-Addressed & P2P Storage Networks](#content-addressed--p2p-storage-networks)
- [Decentralized Messaging Networks](#decentralized-messaging-networks)
- [Isolated Operations Systems](#isolated-operating-systems)
- [HTTP-based DPI Evasion](#http-based-dpi-evasion)
- [SSH-based tunneling](#ssh-based-tunneling)
- [ICMP-based Tunneling](#icmp-based-tunneling)
- [DNS-based Tunneling](#dns-based-tunneling)
- [Contributing](#contributing)

## Foundation: Minimalist 200-Line Core
* [**simplest-vpn**](https://github.com/developer3389/simplest-vpn) – A minimalist Go-based PoC for custom tunneling. It allows users to modify packet structures directly, focusing on the core mechanism: routing traffic between TUN interfaces.

> [!TIP]  
> **The Key to the Future**
>
> The analysis of DPI failure is clear: the only way to win is to control your own transport.  
> `simplest-vpn` is not just a demo — it is the **implementation of the strategy**. 
> 
> * **[Read our Strategic Analysis](https://github.com/developer3389/network-censorship-analysis)** to understand why custom tunneling is the only way forward.
> * **[Explore the 200-line skeleton](https://github.com/developer3389/simplest-vpn)** to start building your own infrastructure today.

## VPN Industry Standards
*Established protocols that are widely supported but often heavily targeted by DPI due to their standardized traffic signatures.*

* [**OpenVPN**](https://github.com/OpenVPN/openvpn) – The traditional industry standard. Highly secure but notoriously difficult to hide from DPI because of its distinct handshake and packet patterns.
* [**WireGuard**](https://github.com/WireGuard) – Modern, high-performance, and significantly faster than OpenVPN. While it is harder to detect, its fixed packet sizes and constant headers have made it a common target for newer DPI filtering rules.
* [**SoftEther**](https://github.com/SoftEtherVPN/SoftEtherVPN) – Complex, multi-protocol VPN software with HTTPS-mimicry capabilities.
* [**IPsec**](https://github.com/strongswan/strongswan) – A foundational enterprise VPN standard widely used for site-to-site and corporate remote-access deployments. While highly interoperable, its standardized IKE/IPsec negotiation patterns are easily recognized by DPI systems.

## About DNS
*Third-party DNS services used to bypass ISP-controlled DNS resolution and reduce manipulation of DNS queries.*

* [**Cloudflare DNS (1.1.1.1)**](https://1.1.1.1/) — Privacy-focused recursive DNS resolver with global Anycast network.
* [**Google Public DNS (8.8.8.8)**](https://developers.google.com/speed/public-dns) — High-performance global DNS resolution service.
* [**Quad9 (9.9.9.9)**](https://quad9.net/) — Security-oriented DNS blocking malicious domains via threat intelligence feeds.
* [**OpenDNS**](https://www.opendns.com/) — Long-running DNS provider with filtering and security features.

* [**DoH (DNS over HTTPS)**](https://datatracker.ietf.org/doc/html/rfc8484) – Encrypts DNS queries inside HTTPS traffic, preventing ISP visibility and tampering.

* [**DoT (DNS over TLS)**](https://datatracker.ietf.org/doc/html/rfc7858) – Encrypts DNS queries using TLS, typically over a dedicated port (853), protecting against interception and modification.

## Proxy-based Anti-Censorship
*Proxy-based tools that route traffic through encrypted tunnels or protocol-mimicking channels to bypass network filtering and DPI-based blocking. These systems typically operate at the application or transport layer and focus on disguising traffic patterns as legitimate web activity.*

* [**Shadowsocks**](https://github.com/shadowsocks/shadowsocks-libev) – A lightweight encrypted SOCKS5 proxy designed to bypass network censorship. It wraps traffic in a simple encrypted stream that resembles TLS-like data flow. Originally created as a response to heavy DPI filtering, it remains a foundational building block for many modern anti-censorship systems.
* [**Trojan**](https://github.com/p4gefau1t/trojan-go) – A proxy protocol that fully imitates HTTPS traffic. This Go-based implementation is widely used for its ability to blend into normal web browsing via TLS and resist advanced DPI-based detection.
* [**NaïveProxy**](https://github.com/klzgrad/naiveproxy) – A proxy tool that tunnels traffic through real HTTPS by embedding it into standard browser TLS behavior (based on the Chromium networking stack). It aims to make traffic indistinguishable from normal web traffic by reusing genuine TLS fingerprints and HTTP/2 behavior.

## QUIC-based Proxy Tools
*Modern QUIC-based transport protocols designed to improve performance and resist traffic fingerprinting.*
* [**Hysteria**](https://github.com/apernet/hysteria) – A high-performance, QUIC-based proxy protocol built on top of UDP and TLS 1.3 (HTTP/3 ecosystem). It leverages QUIC to improve performance under packet loss and disguises traffic as modern HTTP/3 patterns, making it highly effective against DPI-based traffic shaping.
* [**TUIC**](https://github.com/tuic-protocol/tuic) – A QUIC-based proxy protocol focused on low-latency encrypted transport and resistance to packet loss and DPI analysis.

## XRAY Ecosystem
*Modern proxy framework and protocol ecosystem focused on traffic obfuscation and routing flexibility*

* [**Xray-core**](https://github.com/XTLS/Xray-core) – A high-performance network engine supporting multiple transport protocols and complex routing configurations.
* [**Reality**](https://github.com/XTLS/REALITY) – A cutting-edge security extension that allows traffic to perfectly mimic legitimate TLS connections to reputable websites. By borrowing the identity of existing, trusted servers, it eliminates the need for domain management and effectively neutralizes DPI signature analysis.
* [**VLESS**](https://github.com/XTLS/Xray-core/blob/main/docs/transport/internet/security/reality.md) – A stateless, lightweight transport protocol that minimizes packet overhead and eliminates predictable handshake patterns, serving as the foundation for modern stealth configurations.

## Overlay Networks
*Routing systems designed to resist censorship, traffic analysis, and network surveillance.*

### Tor
* [**Tor**](https://www.torproject.org/) – A decentralized anonymity network that routes traffic through multiple volunteer-operated relays using layered encryption ("onion routing"). Widely used for censorship circumvention and privacy protection.

#### Tor Pluggable Transports
* [**obfsproxy**](https://gitlab.torproject.org/legacy/trac/-/wikis/doc/obfsproxy) – A traffic obfuscation framework that transforms Tor traffic into unidentifiable noise, forming the basis for later pluggable transports.

* [**Snowflake**](https://snowflake.torproject.org/) – A WebRTC-based pluggable transport that routes traffic through ephemeral browser proxies, making blocking significantly harder.

* [**meek**](https://gitlab.torproject.org/legacy/trac/-/wikis/doc/meek) – A domain-fronting-based transport that disguises Tor traffic as HTTPS to major cloud providers.

### I2P
* [**I2P**](https://geti2p.net/) – An anonymous peer-to-peer overlay network optimized for internal hidden services and decentralized communication. Uses garlic routing and dynamically built tunnels to reduce traffic correlation and improve censorship resistance.

## Encrypted Mesh Networks
*Self-configuring encrypted overlay networks that provide peer-to-peer IP connectivity without traditional centralized routing.*

* [**Yggdrasil**](https://github.com/yggdrasil-network/yggdrasil-go) – An IPv6-based encrypted mesh network with automatic routing and end-to-end encryption designed to self-assemble across various network topologies.
* [**Tailscale**](https://tailscale.com/) — A zero-configuration mesh VPN built on top of WireGuard. It provides automatic NAT traversal and peer-to-peer networking with centralized coordination for key exchange and device discovery. While not designed specifically for censorship resistance, it can be used as a resilient encrypted overlay network in restrictive environments.
* [**ZeroTier**](https://github.com/zerotier/ZeroTierOne) – A software-defined virtual networking platform enabling L2/L3 mesh connectivity, utilizing a sophisticated decentralized control plane for secure peer-to-peer routing.
* [**Nebula**](https://github.com/slackhq/nebula) – A scalable overlay networking tool developed by Slack, focusing on secure, high-performance peer-to-peer connectivity using certificate-based authentication.
* [**cjdns**](https://github.com/cjdelisle/cjdns) – An IPv6 encrypted mesh routing protocol that implements cryptographic addressing and distributed routing to ensure end-to-end security by default.

## Content-Addressed & P2P Storage Networks
*Distributed systems for decentralized storage, content distribution, and persistent data availability using cryptographic addressing or replication-based P2P models.*

* [**IPFS**](https://github.com/ipfs/kubo) – The reference implementation (Kubo) of the InterPlanetary File System, a P2P protocol for content-addressed data storage and retrieval.
* [**Filecoin**](https://github.com/filecoin-project/lotus) – The Lotus implementation of the Filecoin network, an incentivized storage layer built on top of IPFS.
* [**Hypercore Protocol**](https://github.com/hypercore-protocol/hypercore) – A secure, distributed append-only log, serving as the foundational data structure for fast P2P replication.
* [**BitTorrent**](https://github.com/webtorrent/bittorrent-protocol) – A foundational P2P protocol implementation for swarming and chunk-based file distribution.
* [**Sia**](https://github.com/SiaFoundation/siad) – The core implementation of the Sia decentralized cloud storage platform, focusing on redundancy and peer-to-peer storage contracts.
* [**Storj**](https://github.com/storj/storj) – The distributed cloud storage network architecture, featuring S3-compatible API and client-side encrypted object storage.
* [**Arweave**](https://github.com/ArweaveTeam/arweave) – The protocol implementation for permanent, immutable data storage using a blockweave structure.

## Decentralized Messaging Networks
*Peer-to-peer and federated messaging systems designed to reduce reliance on centralized infrastructure. These systems prioritize architectural resilience, data sovereignty, and metadata minimization, utilizing varied transport layers to ensure connectivity in diverse network conditions.*

* [**Matrix (Synapse)**](https://github.com/element-hq/synapse) – A federated real-time communication protocol with end-to-end encryption. Uses a decentralized server model and supports extensive bridging.
* [**Session**](https://github.com/oxen-io/session-desktop) – A privacy-focused messenger built on the Oxen network, using onion routing to hide metadata and remove reliance on central servers.
* [**Briar**](https://github.com/briar/briar) – A peer-to-peer messenger designed for high-censorship environments. Synchronizes over Tor, Bluetooth, or Wi-Fi for offline resilience.
* [**SimpleX Chat**](https://github.com/simplex-chat/simplex-chat) – A messaging system with no persistent user identifiers. Messages are routed through temporary relays, minimizing metadata exposure.
* [**Jami**](https://github.com/savoirfairelinux/jami-client-qt) – A fully decentralized P2P platform using distributed hash tables (DHT) for peer discovery and secure media transport.
* [**Tox**](https://github.com/TokTok/c-toxcore) – An end-to-end encrypted P2P messenger focusing on direct user-to-user connections and built-in multimedia support.
* [**Delta Chat**](https://github.com/deltachat/deltachat-core-rust) – An email-based messenger that uses existing SMTP/IMAP infrastructure as a transport layer, providing encrypted chat semantics without dedicated proprietary servers.

## Isolated Operating Systems
*Operating systems designed to route all traffic through anonymizing or secure network layers, providing strong isolation against leaks and traffic correlation.*

* [**Whonix**](https://github.com/Whonix) — A privacy-focused operating system that forces all network traffic through Tor using a split-VM architecture (Gateway + Workstation). Designed to prevent IP leaks and isolate applications from direct network access.
* [**Tails**](https://tails.net/) — A live operating system that routes all traffic through Tor and leaves no trace on the host machine after shutdown. Designed for high-risk environments and portable anonymity.
* [**Qubes OS**](https://github.com/QubesOS) — A security-oriented operating system based on compartmentalization via lightweight VMs. Supports network isolation by routing different security domains through separate proxies (including Tor-based VMs).

## HTTP-based DPI Evasion
*Legacy techniques that exploit weaknesses in HTTP parsing, request handling, and proxy interpretation. These methods operate by manipulating HTTP semantics rather than encrypting traffic, and were widely used before modern TLS-based censorship resistance systems.*

* [**GreenTunnel**](https://github.com/SadeghHayeri/GreenTunnel) – A tool that attempts to bypass DPI by fragmenting and manipulating HTTP requests to evade signature-based detection systems that inspect HTTP payload structure.

## SSH-based Tunneling
*Legacy encrypted tunneling method using SSH as a transport layer. It provides simple SOCKS proxying and port forwarding capabilities and is still widely used as a fallback bypass method.*

* [**OpenSSH**](https://github.com/openssh/openssh-portable) – A widely used implementation of the SSH protocol that supports built-in tunneling features such as SOCKS proxying (-D), local (-L), and remote (-R) port forwarding.

## ICMP-based Tunneling
*Legacy tunneling methods that encapsulate data inside ICMP (Internet Control Message Protocol) packets. ICMP is primarily used for diagnostics (e.g., ping), but can be abused as a covert transport channel in restricted networks.*

* [**ptunnel**](https://github.com/lnslbrty/ptunnel) – A TCP-over-ICMP tunneling tool that encapsulates TCP traffic inside ICMP echo request/reply packets, enabling basic connectivity in networks where only ICMP is allowed.
* [**icmptunnel**](https://github.com/DhavalKapil/icmptunnel) – A lightweight tool that creates a virtual network interface and tunnels IP traffic over ICMP packets, effectively forming a simple VPN-like connection over ping.
* [**icmptx**](https://github.com/jakkarth/icmptx) – A minimal ICMP tunneling tool designed to transmit IP packets over ICMP echo requests, often used for experimental or restricted-network scenarios.

## DNS-based Tunneling
*Legacy network tunneling methods that encapsulate arbitrary data inside DNS traffic. These techniques were widely used in early censorship circumvention and penetration testing scenarios, especially in environments where DNS is one of the few allowed protocols.*

* [**iodine**](https://github.com/yarrick/iodine) – A DNS tunneling tool that encapsulates IPv4 data inside DNS queries, enabling traffic to pass through restrictive networks where only DNS is allowed.
* [**dnscat2**](https://github.com/iagox86/dnscat2) – A DNS tunneling tool that creates an encrypted command-and-control channel over DNS requests and responses.
* [**dns2tcp**](https://github.com/alex-sector/dns2tcp) – A lightweight tool that tunnels TCP connections through DNS traffic.

# Contributing

Contributions are welcome! Please follow these guidelines:

* **Open-Source:** Only open-source projects will be considered.
* **Architectural Resilience:** Focus on tools that provide structural resistance to censorship, rather than simple commercial VPN clients.
* **Explanation:** When submitting a new tool, please include a brief explanation of the underlying mechanism used to evade DPI-based blocking.
