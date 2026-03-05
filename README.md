# P2P-File-Sharing-System
CSC3002F - Networks [Group Project]

## 🌐 Mini BitTorrent-Like P2P File Sharing System
This project implements a simplified torrent-like peer-to-peer (P2P) file sharing system developed using Python sockets.

The system uses:
* TCP for reliable file chunk transfer
* UDP for tracker communication and peer discovery
  
It consists of three core components:
* Tracker – Registers and manages seeders, provides peer discovery for leechers.
* Seeder – Hosts and shares file chunks with requesting leechers.
* Leecher – Downloads file chunks in parallel from multiple seeders and reconstructs the file.

## 👥 Team Project
This system was developed as a group assignment for CSC3002 – Computer Networks.

#### Contributors:
* Sithokomele Nxumalo
* Banele Magobiyane
* Athenkosi Miya

The team collaborated on protocol design, socket implementation, multithreading, hashing, and system testing.

## 📦 Prerequisites
Before running the system, ensure:
* Python 3.x is installed
* The requested file exists in the same directory as the source code (for CLI version)

#### Required Libraries
* socket
* threading
* time
* os
* hashlib
* PyQt5 (for GUI version)

## 🚀 Running the System
### 1️⃣ Running the Tracker
The Tracker:
* Registers seeders
* Maintains active peer records
* Handles leecher requests
* Removes inactive seeders using a timeout mechanism

Steps:
1. Open a terminal
2. Navigate to the project directory
3. Run: python Tracker.py
The Tracker will begin listening for Seeder and Leecher requests.

### 2️⃣ Running a Seeder
A Seeder:
* Registers available files with the Tracker
* Shares file chunks over TCP
* Sends periodic heartbeat messages to remain discoverable

Steps:
1. Open a new terminal window
2. Navigate to the project directory
3. Run: python Seeder.py
4. Enter the file(s) you want to register
5. The Seeder will:
* Register with the Tracker
* Start sending periodic heartbeats
* Begin accepting Leecher connections
To run multiple seeders, open multiple terminal windows.

### 3️⃣ Running a Leecher
A Leecher:
* Requests available seeders from the Tracker
* Downloads file chunks in parallel (multi-threaded)
* Reconstructs the file
* Verifies integrity using SHA-256 hashing
* Automatically transitions into a Seeder after successful download

Steps:
1. Open another terminal window
2. Navigate to the project directory
3. Run: python Leecher.py
4. Enter the file name to download
5. The Leecher will:
* Receive a list of active seeders
* Download chunks in parallel
* Reassemble and verify the file

## 🖥️ Running the GUI Version
This project also includes a PyQt5-based graphical interface.

To run the GUI: python p2p_gui.py

The GUI provides:
* Tracker control
* Seeder control
* File download interface
* Real-time status updates

## 🧠 Key Features
* UDP-based tracker communication
* TCP-based reliable file transfer
* Multi-threaded parallel downloads
* Heartbeat mechanism for active seeder detection
* Automatic Leecher → Seeder transition
* Optional GUI interface

## 🛠 Troubleshooting

### 1. Leecher cannot find a Seeder
* Ensure the Seeder is registered and sending heartbeats
* Confirm the Tracker is running
* Verify the file name is correct

### 2. Connection Refused / Timeout
* Ensure Tracker, Seeder, and Leecher are running
* Verify correct IP and port configurations
* Ensure firewall settings allow communication

### 3. Seeder not sharing files
* Confirm the file exists in the Seeder directory
* Ensure successful registration with Tracker
* Check heartbeat messages are being sent

### 4. Multiple Seeders Conflict
* Ensure each seeder uses a unique port
* Confirm file sizes are correctly registered

### 5. Tracker Not Responding
* Confirm Tracker is running on correct IP and port
* Restart Tracker if needed
* Check firewall settings for UDP blocking

## 🔮 Future Enhancements
* Implement end-to-end encryption
* Add chunk-level hashing verification
* Improve error handling and connection recovery
* Implement bandwidth management
* Add progress bars and detailed statistics in GUI

