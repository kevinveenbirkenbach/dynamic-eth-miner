# Dynamic Miner - Proof of Concept 🚀

## About This Project 📖
This project was created by [Kevin Veen-Birkenbach](https://www.veen.world/) as a proof of concept to explore whether unused hardware resources could be leveraged to mine cryptocurrencies. 💻

During the development process, it became evident that the energy costs required to run the mining operations were higher than the potential revenue generated from mining cryptocurrencies. 💸 Due to this, mining with this tool is **not profitable** and **not recommended**.

This project was generated with the help of [ChatGPT 🤖](https://chatgpt.com/share/6798eaf6-efa0-800f-bb25-92d74a63f1e2) to demonstrate the automation of mining tasks using Docker and hardware monitoring.

---

## How It Works ⚙️

The tool dynamically starts and stops mining operations based on hardware usage thresholds:

- **NVIDIA GPU Miner**: Monitors NVIDIA GPUs and starts mining if GPU usage is below a threshold. Stops mining if GPU usage is too high.
- **Intel GPU Miner**: Monitors Intel GPUs and works similarly to the NVIDIA miner.
- **CPU Miner**: Monitors CPU usage and starts/stops mining accordingly.

The tool uses Docker containers to run the mining operations and a Bash script (`miner_control.sh`) to monitor resource usage and control the miners. Systemd is used to manage the monitoring service.

### Features 🌟
- Automatic monitoring of NVIDIA GPUs, Intel GPUs, and CPUs.
- Dynamic start/stop of mining containers based on resource usage thresholds.
- Easy setup and configuration through environment variables (`.env` file).
- Includes a Docker Compose configuration for miner containers.

---

## Setup Instructions 🛠️

### Prerequisites 📋
1. A Linux machine with:
   - **NVIDIA GPU** (and `nvidia-smi` installed).
   - **Intel GPU** (with `intel_gpu_top` installed).
   - Docker and Docker Compose installed.
2. Basic command-line knowledge.
3. An active internet connection.
4. Wallet addresses and mining pool URLs for the cryptocurrencies you wish to mine.

### Installation 🖥️

1. Clone the repository:
   ```bash
   git clone https://github.com/kevinveenbirkenbach/dynamic-eth-miner.git
   cd dynamic-eth-miner
   ```

2. Run the setup script:
   ```bash
   bash setup.sh
   ```
   - If a `.env` file is not found, the script will prompt you to enter values for mining pool addresses, wallet addresses, and thresholds.
   - If a `.env` file exists, it will load the existing configuration.

3. The script will:
   - Pull the required Docker images.
   - Build the containers.
   - Create a Systemd service to monitor and manage mining tasks.

4. Check the service status:
   ```bash
   sudo systemctl status miner-monitor.service
   ```

### Stopping the Service ✋
To stop the mining service, run:
```bash
sudo systemctl stop miner-monitor.service
```

---

## Profitability Tools 📊
Before mining, you can check the profitability of mining different cryptocurrencies using these tools:
- [WhatToMine](https://whattomine.com/)
- [NiceHash Profitability Calculator](https://www.nicehash.com/profitability-calculator)

These tools can help you estimate if mining is worth the effort based on your hardware and energy costs.

---

## Important Notes ⚠️
- Mining profitability heavily depends on electricity costs, hardware efficiency, and cryptocurrency market prices.
- This tool is for **educational purposes only** and is not intended for production use.
- **Do not use this tool** unless you fully understand the financial and environmental costs associated with cryptocurrency mining.

---

## Contact 📬
For more information or to check out other projects, visit [Kevin Veen-Birkenbach's website](https://www.veen.world/).

---

## License 📜
This project is licensed under the [GNU Affero General Public License v3.0](./LICENSE).