# 🐄 Understanding the Business Goals

The DG Collar solution monitors the biometrics of a cow through a smart collar that measures movement, temperature, and heartbeat with sensors.  
All data is streamed through a LoRaWAN gate. This is the base for all three architectures.

The data mainly comes in batches to avoid unnecessary costs. By using **Type 2 SCD with timestamp updates**, we can show the difference between data staying the same vs. data changing over time.  
We also need the ability to single out a specific device (cow) to monitor more closely — basically a **live stream mode** when needed.

The data is originally supposed to be presented in an app or website, but for this project we are going to make our user interface in **Power BI** as a simple proof of concept.

---

# 🎯 Purpose of the Project

1. **Maintain a clean database**  
   (Data is the new gold — quality and consistency matter.)

2. **Heat monitoring for cows**  
   Detecting behavior and temperature changes to support estrus/heat tracking.

3. **Health alerts**  
   Identifying fever, abnormal inactivity, sudden movement, or any irregular signs.

---

# 🧭 Architecture Principles

### **KISS Technique**  
Adding a feature can be costly, so we have to keep our eye on the goal and not let personal biases affect decisions in a way that might slow down the business or delay rollout.  
We keep it KISS.

### **YAGNI**  
Our future hopes and dreams live in another plan (YAGNI).  
We can pull ideas from it over time, but they do not belong in the MVP.

---

# 🖥 Local Server vs Cloud-Based

**Factors to compare:**

### **Cost**
- Local: cheaper to run but limited  
- Cloud: pay-as-you-go, can increase cost with scale  

### **Performance**
- Local: depends on on-prem hardware  
- Cloud: scalable, flexible, can handle burst loads  

### **Maintenance**
- Local: requires manual work and fixing hardware  
- Cloud: managed services, less manual effort  

### **Overall Effectiveness to the Business**
- Local: good for small farms or offline scenarios  
- Cloud: better long-term, supports expansion, remote access, and future AI features  
