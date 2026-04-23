# SDN-Based Network Utilization Monitor using Mininet and POX

## Problem Statement
The objective of this project is to monitor network utilization in a Software Defined Networking (SDN) environment using Mininet and a POX OpenFlow controller.

The project demonstrates:
- Controller-switch interaction
- Flow-rule based forwarding
- Traffic generation and utilization monitoring
- Performance observation under different traffic conditions

---

## Tools Used
- Ubuntu Virtual Machine
- Mininet
- POX Controller
- OpenFlow
- iperf
- pingall

---

## Topology Used

Single switch, two hosts:

h1 ---- s1 ---- h2

Created using:

sudo mn --topo single,2 --controller remote

---

## Controller Used

POX learning switch controller:

python3 pox.py forwarding.l2_learning

This handles:
- packet_in events
- dynamic forwarding decisions
- match-action flow installation

---

## Test Scenario 1: Normal Traffic

Command:

pingall

Observation:
- Hosts communicate successfully
- 0% packet loss
- Baseline connectivity verified

---

## Test Scenario 2: High Utilization

Commands:

h2 iperf -s &
h1 iperf -c 10.0.0.2

Observation:
- High traffic generated
- Throughput measured

Example Result:
42.9 Gbits/sec

---

## Performance Analysis

Observed metrics:
- Connectivity (ping)
- Throughput (iperf)
- Network utilization under load

Higher utilization was observed under iperf compared to normal traffic.

---

## Setup and Execution Steps

Install Mininet:

sudo apt install mininet -y

Clone POX:

git clone https://github.com/noxrepo/pox.git

Run Controller:

cd pox
python3 pox.py forwarding.l2_learning

Open second terminal:

sudo mn --topo single,2 --controller remote

Run tests:

pingall

h2 iperf -s &
h1 iperf -c 10.0.0.2

---

## Expected Output
- Successful host connectivity
- Throughput measurement displayed
- Controller-managed forwarding behavior

---

## Proof of Execution

Screenshots included:
- Controller log
- pingall result
- iperf throughput output

---

## References
- Mininet Documentation
- POX Documentation
- OpenFlow Concepts
