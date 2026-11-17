# LoRaWAN Network Scalability, Collision & Energy Efficiency Simulator (AU915)

A discrete-event simulation model developed in **Python** (based on `LoRaSim` and `SimPy`) to evaluate the scalability, packet collision behavior, Data Extraction Rate (DER), and energy consumption of LoRa/LoRaWAN wireless sensor networks operating in the **AU915 (915 MHz)** regional band.

## Technical Highlights & Calibration
* **Propagation Model:** Log-distance path loss calibrated with empirical **Radio Mobile** parameters ($d_0 = 40\text{ m}$, $\gamma = 2.08$, $L_{pl}(d_0) = 70.1\text{ dB}$, $P_{tx} = 10\text{ dBm}$, $G_L = 6.5\text{ dBi}$).
* **Multi-Domain Collision Engine:** Evaluates simultaneous packet arrivals across frequency channels, Spreading Factors (`SF7`–`SF12`), capture effect power thresholds (`6 dB`), and preamble timing overlaps.
* **Energy Consumption Profiling:** Computes precise energy expenditure per node and per transmitted packet (in Joules) across transceiver current states (`3.3V` supply).
* **Automated KPI Logging:** Generates structured experiment datasets (`expX.dat`) tracking total transmissions, collisions, lost packets, and **Data Extraction Rate (DER)**.

## Simulation Experiments Included
* **Experiment 0:** Baseline single-frequency ALOHA-style transmission (`SF10`, `BW 125 kHz`).
* **Experiment 1:** Multi-channel random frequency hopping across 3 AU915 channels (`902.3`, `903.3`, `904.6 MHz`).
* **Experiment 2:** Higher data rate configuration (`SF9`, `BW 125 kHz`).
* **Experiment 3:** Dynamic Spreading Factor (`SF7`–`SF12`) and bandwidth (`125`/`250`/`500 kHz`) optimization based on node-to-gateway distance.
* **Experiment 4:** Standard LoRaWAN profile (`SF8`, `BW 125 kHz`, `CR 4/5`).
* **Experiment 5:** Joint Spreading Factor and Adaptive Transmit Power (`Ptx`) optimization.

## Tech Stack
* **Language:** Python
* **Libraries:** `SimPy` (discrete-event simulation), `NumPy` (matrix & RF sensitivity calculations), `Matplotlib` (2D spatial network topology visualization)

## Usage
```bash
python loraDir.py <nodes> <avgsend_ms> <experiment_id> <simtime_ms> [full_collision]
Example running 50 nodes with a 60,000 ms average interval under Experiment 3:
python loraDir.py 50 60000 3 3600000 1
