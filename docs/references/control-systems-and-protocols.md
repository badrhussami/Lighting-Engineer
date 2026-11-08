# Control systems and protocols

This guide is a planning and verification aid for lighting control. Exact behavior depends on protocol edition, device implementation, console/node firmware, configuration, network design, and manufacturer documentation.

## Control-system planning sequence

1. Inventory console/controller, gateways/nodes, fixtures, dimmers, network switches, wireless components (if any), software/firmware, and venue infrastructure by exact model and revision.
2. For each fixture, record the selected personality/mode, channel footprint, start address, universe, control protocol, refresh/fallback behavior, and relevant control settings from that fixture's manual/personality file.
3. Draw the signal path from source to endpoint. Identify physical DMX links separately from Ethernet/IP transport, gateways, network boundaries, and redundant paths. Label connectors, port modes, universe mappings, addresses, and ownership.
4. Confirm protocol and device compatibility at both ends. “Supports DMX,” “supports RDM,” or “supports Art-Net/sACN” is not enough to prove a particular feature or interoperability behavior.
5. Define addressing, naming, discovery, network/IP plan, multicast/unicast expectations, VLAN/QoS/security policy where applicable, backup/failover behavior, and commissioning tests with the responsible controls/network teams.
6. Test from the source outward with known-good configurations and devices. Change one variable at a time; save configuration and show-file backups; record observations and restore known-good state after tests.

## Common fault-isolation prompts

- **Fixture absent from control:** verify power/status, physical path, output/node configuration, universe mapping, protocol selection, and whether the endpoint is configured for the expected source.
- **Wrong fixture/parameters:** verify patch, fixture personality/mode, channel footprint, start address, offsets, and console/library version before changing wiring.
- **Intermittent or corrupted response:** check topology, connector/cable condition, termination and splitters for the physical DMX segment; for IP transport, check endpoint addressing, network policy, multicast/unicast configuration, packet/source behavior, and switch/network-team observations. Use protocol-appropriate instrumentation and vendor guidance.
- **RDM discovery/control issue:** confirm every device, splitter, gateway, and controller in the path supports the relevant RDM operation and that the product configuration permits it. RDM compatibility is not guaranteed by a DMX label.
- **Unexpected look on loss of control:** consult the exact device manual for data-loss/fallback behavior. Do not assume all fixtures hold, black out, or use the same timeout.

These are diagnostic categories, not a substitute for a site-specific test plan. Do not work on energized equipment or alter safety-critical network/electrical configurations unless qualified and authorized.

## Protocol and software references

### ESTA Technical Standards Program (ESTA TSP)
- [ESTA published documents catalogue](https://tsp.esta.org/tsp/documents/published_docs.php) — live source of current and historical published documents; verify status before citing. Relevant document families include:
  - **ANSI E1.11 (DMX512-A):** serial data link for entertainment lighting control.
  - **ANSI E1.20 (RDM):** bidirectional device management over DMX512; ESTA announced the 2025 edition.
  - **ANSI E1.17 (ACN):** architecture and protocols for networked control; catalogue lists reaffirmations/revisions.
  - **ANSI E1.31 (sACN):** streaming protocol for transport of DMX512 data using ACN; check catalogue for current revision.
  - **ANSI E1.33 (RDMnet):** networked RDM; check catalogue for current revision and device support.
  - **ANSI E1.27-1:** portable control cable guidance for E1.11/DMX512-A products.
- [ESTA TSP documents portal](https://tsp.esta.org/tsp/documents/index.html) — published documents, public reviews, and program information.
- [ESTA TSP news on ANSI E1.20-2025](https://tsp.esta.org/tsp/news/news_details.php?newsID=803) — publication notice and scope summary; use the standard itself for technical requirements.

### Art-Net
- [Art-Net overview and specification access](https://artisticlicence.com/pages/art-net-overview) — Artistic Licence is the protocol owner and provides the specification subject to its stated terms. Consult the current specification, not an informal summary.

### Open Lighting Architecture
- [OLA developer documentation](https://docs.openlighting.org/ola/doc/latest/) — project documentation for OLA APIs and supported control protocols. Check the documentation version against the installed OLA release.

## Documentation to produce

For a control package, include a device inventory, fixture/personality schedule, patch/universe map, network and physical topology diagrams, configuration backups, firmware/software versions, fallback behavior, test results, open issues, and named handover owner. Do not include passwords, secrets, or sensitive network details in public repository files.
