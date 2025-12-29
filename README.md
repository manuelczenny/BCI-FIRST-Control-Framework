# BCI-FIRST Control Framework

An open-source software framework for controlling FIRST Robotics Competition (FRC) robots using a Neural Impulse Actuator (NIA). This project aims to provide a robust and extensible interface between brain-computer interface (BCI) hardware and the FRC control system.

## Overview

The goal of this project is to allow operators to control a FIRST robot through brain signals captured by a Neural Impulse Actuator. The framework processes raw NIA signals, translates them into robot commands, and communicates those commands to the robot via the standard FRC NetworkTables protocol.

### High-Level Architecture

```
+----------------+     +-------------------+     +---------------------+     +------------------------+
|   NIA Driver   | --> |  Signal Processor | --> |  Command Translator | --> | FRC Network Communicator |
+----------------+     +-------------------+     +---------------------+     +------------------------+
        |                        |                         |                           |
   Raw EEG/EMG            Filtering, Feature        Mapping to robot            Send commands to
   signal stream          extraction, analysis      commands (forward,          robot over NetworkTables
                                               turn, arm up, etc.)
```

### Components

1. **NIA Driver** – Interfaces with the NIA hardware, handles connection, raw data acquisition, and disconnection.
2. **Signal Processor** – Applies digital filters, extracts relevant features (e.g., power bands, event detection), and normalizes signals.
3. **Command Translator** – Maps processed signals to predefined robot actions (e.g., "forward" when a specific thought pattern is detected).
4. **FRC Network Communicator** – Sends translated commands to the robot's roboRIO using the FRC NetworkTables protocol.

## Getting Started

### Prerequisites

- Python 3.8 or later
- [FRC NetworkTables](https://robotpy.readthedocs.io/en/stable/install/networktables.html) library (`pip install pynetworktables`)
- Access to a Neural Impulse Actuator (NIA) device and its SDK/driver (simulated for development)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/manuelczenny/BCI-FIRST-Control-Framework.git
   cd BCI-FIRST-Control-Framework
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Run the example calibration script (once implemented):
   ```bash
   python examples/calibrate.py
   ```

### Development Environment Setup

1. Create a virtual environment (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

2. Install development dependencies:
   ```bash
   pip install -r requirements-dev.txt
   ```

3. Run tests:
   ```bash
   pytest
   ```

## Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on submitting pull requests, reporting issues, and coding standards.

## License

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.

## Roadmap

- **v0.1 (Alpha)** – Basic NIA driver and NetworkTables communication.
- **v0.2 (Beta)** – Signal processing pipeline and simple command mapping.
- **v1.0 (Stable)** – Full calibration GUI, robust error handling, and comprehensive documentation.

## Acknowledgments

- FIRST Robotics Competition for the amazing platform.
- The open‑source BCI community for inspiration and tools.
- Contributors and testers who help improve this framework.