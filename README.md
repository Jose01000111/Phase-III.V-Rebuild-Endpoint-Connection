# 🖥️ Phase-III.V-Rebuild-Endpoint-Connection (Redo)

## Lab Overview
During my initial setup of the Splunk server VM, I realized the disk size I allocated was too small, which caused performance issues and prevented proper installation of Splunk Enterprise. To fix this, I rebuilt the lab with sufficient memory and disk space for both the Splunk server and the endpoint VM. This lab documents the full setup, endpoint configuration, log forwarding, network verification, and Splunk Web validation.

---

## 🚀 Install Splunk Universal Forwarder on Endpoint
I downloaded and installed the Universal Forwarder for AMD64 Linux on my endpoint VM. After installation, I started the forwarder and enabled boot-start so it automatically runs on system startup. This prepares the endpoint to send logs to the Splunk server.

<img width="804" height="539" alt="vtkSkdN" src="https://github.com/user-attachments/assets/d796b24f-7bd6-40d2-bab3-67822e3cf064" />

<img width="807" height="507" alt="XCs1Nkr" src="https://github.com/user-attachments/assets/763af829-32cb-43ee-bb71-882878ff42ae" />

<img width="793" height="374" alt="0Joyqm8" src="https://github.com/user-attachments/assets/fc4d5f7c-e7d4-438d-bf30-cc94ccf3b673" />

**Code/Configuration Explanation:**  
- Installs the Splunk Universal Forwarder so the endpoint can collect logs.  
- Configures the forwarder to start automatically on boot.  
- Prepares the system to send logs to the Splunk server for monitoring.

---

## 📤 Configure Forwarder to Send Logs
I configured the forwarder to monitor the `/var/log` directory and forward all logs to the Splunk server on port 9997. After restarting the forwarder, logs began flowing to the server successfully.

<img width="810" height="136" alt="Sme84XB" src="https://github.com/user-attachments/assets/acd4abd2-6891-41c6-a948-079e638a8c44" />

**Code/Configuration Explanation:**  
- Sets the forwarder to send logs from the endpoint to the server.  
- Monitors system logs in `/var/log` for collection.  
- Restarts the forwarder to apply the configuration and ensure log transmission.

---

## 🖧 Install Splunk Enterprise on Server
I downloaded and installed the AMD64 version of Splunk Enterprise on the server VM. I started Splunk, accepted the license, and configured admin credentials. This ensures the server is ready to receive logs from the endpoint.

<img width="808" height="314" alt="vBveTL4" src="https://github.com/user-attachments/assets/93535ace-2424-4397-a769-9909c84be7b7" />

<img width="650" height="38" alt="zB1XtuT" src="https://github.com/user-attachments/assets/928d189e-6062-4199-8d54-61d1dc98c4ee" />

**Code/Configuration Explanation:**  
- Installs Splunk Enterprise on the server to receive and process logs.  
- Starts the Splunk service and accepts the license agreement.  
- Sets up admin credentials for accessing the Splunk Web interface.

---

## 🔗 Enable Receiving on Splunk Server
I enabled the Splunk server to listen on port 9997 to accept incoming logs. After restarting, the server was fully ready to receive data from the endpoint.

<img width="807" height="194" alt="LPYK7fA" src="https://github.com/user-attachments/assets/6f8f4424-69b3-4b49-a0af-2be3d00793d1" />

<img width="662" height="35" alt="ClEhDrQ" src="https://github.com/user-attachments/assets/d2280a20-f553-44f0-9bcc-e77759cde94c" />

**Code/Configuration Explanation:**  
- Opens a port on the server to receive forwarded logs from endpoints.  
- Restarts the Splunk service to apply the receiving configuration.  
- Confirms that the server is ready to ingest incoming log data.

---

## 🌐 Verify Network Connectivity Between Server and Endpoint
I verified the IP addresses on both the server and endpoint VMs and successfully pinged each machine from the other. This confirmed proper connectivity and ensures logs can flow without interruption.

<img width="637" height="223" alt="RhzqiZ0" src="https://github.com/user-attachments/assets/828edbcd-93ce-4d2d-a29d-ab465fc8c208" />

<img width="667" height="220" alt="ZGBGWro" src="https://github.com/user-attachments/assets/a5e1a32c-14b2-4128-a6ac-2241ef73b70e" />

**Code/Configuration Explanation:**  
- Checks IP configuration on both VMs to ensure proper addressing.  
- Uses ping to verify network connectivity between server and endpoint.  
- Confirms that logs can successfully travel from endpoint to server.

---

## 🖥️ Access Splunk Web
I opened a browser on the host machine, logged into the Splunk Web interface using my admin credentials, and navigated to the Search & Reporting app. I confirmed that logs from the endpoint were visible and updating in real time.

<img width="1251" height="274" alt="sDO4hsB" src="https://github.com/user-attachments/assets/c4495f2d-ab84-4ce7-85fa-95c95683e03c" />

---

## 📝 Summary
In this lab, I rebuilt my Splunk environment after discovering that my initial server disk was too small. I installed Splunk Enterprise on the server and the Universal Forwarder on the endpoint. I verified network connectivity between the two VMs and confirmed that logs were successfully forwarded and visible in Splunk Web. This setup ensures a fully functional SOC lab environment for monitoring and analysis.
