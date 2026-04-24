# SDN-Based Network Utilization Monitoring using Throughput and Latency Observation

## Problem Statement
The objective of this project is to monitor network utilization in a Software Defined Networking (SDN) environment using Mininet and a POX controller.

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

Single switch with two hosts:

h1 ---- s1 ---- h2

Created using:

sudo mn --topo single,2 --controller remote

---

## Controller Used

POX learning switch controller:

python3 pox.py forwarding.l2_learning

Controller module used in execution:

forwarding.l2_learning

This handles:
- packet_in events
- dynamic forwarding decisions
- match-action flow installation

---

## Test Scenario 1: Connectivity and Packet Loss

Command:

pingall

Observation:
- Hosts communicate successfully
- 0% packet loss observed
- Baseline network behavior verified

---

## Test Scenario 2: Latency Monitoring

Command:

h1 ping -c 5 h2

Observation:
- Round-trip time (RTT) observed
- Latency measured using ping
- Used as a performance metric for network behavior

---

## Test Scenario 3: High Utilization

Commands:

h2 iperf -s &
h1 iperf -c 10.0.0.2

Observation:
- Heavy traffic generated
- Throughput measured as utilization metric

Example Result:
42.9 Gbits/sec

---

## Performance Analysis

Observed metrics:
- Packet loss (0% dropped)
- Latency (ping round-trip time)
- Throughput (iperf bandwidth)

Comparison performed between:
- Baseline traffic
- High utilization traffic

Higher utilization was observed under iperf-generated load.

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

h1 ping -c 5 h2

h2 iperf -s &

h1 iperf -c 10.0.0.2

---

## Expected Output
- Successful host connectivity
- Packet loss observation
- Latency measurement displayed
- Throughput measurement displayed
- Controller-managed forwarding behavior

---

## Proof of Execution

Screenshots included:
- Controller log
- pingall result
- iperf throughput output

Additional metric observed:
- Latency using ping

---

## References
- Mininet Documentation
- POX Documentation
- OpenFlow Concepts
