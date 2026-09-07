# Security Detection Labs

A small collection of hands-on home-lab write-ups focused on **network intrusion
detection** — building a monitored environment with [Suricata](https://suricata.io/)
as the IDS and [Wazuh](https://wazuh.com/) for centralized alerting and
visualization, then generating hostile traffic against it and confirming the
detections fire.

Each lab runs the same core stack (Ubuntu VMs on VMware for the endpoints, a
Wazuh manager on Google Cloud) and is documented end to end: objectives, network
topology, the tools involved, the attack or test procedure, the resulting Suricata
alerts in the Wazuh dashboard, and takeaways.

## Labs

- **[Network Scanning Probe Attack and Detection](labs/nmap-scan-detection/)** —
  run Nmap SYN and version scans from an attacker VM against a Wazuh-agent target,
  and verify Suricata's ET ruleset flags the reconnaissance in the Wazuh
  Security Events view.
- **[Testing NIDS with tmNIDS](labs/nids-testing-tmnids/)** — use the
  [tmNIDS](https://github.com/3CORESec/testmynids.org) framework to fire a battery
  of known-malicious patterns (suspicious User-Agent, Tor connection, and the full
  test suite) at Suricata and analyze the alerts it raises in Wazuh.

On the published site these are served at `/labs/nmap-scan-detection/` and
`/labs/nids-testing-tmnids/`.
