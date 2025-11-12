# 🛰️ Red Sea GPS Jamming Detection 
### Rule-Based Jamming Detection, Hotspot Mapping & Track Cleaning Pipeline

This repository contains the complete analytical workflow for detecting **GPS jamming / spoofing** events in the **Red Sea maritime region**, based on vessel “meetings” data and AIS-derived tracks.

The project includes:

- **Part A — GPS Jamming Detection** (rule-based detection + hotspot clustering)
- **Part B — Vessel Track Cleaning** (Menifot datasets: cleaning, outlier removal, plotting)
- **Interactive HTML notebooks**, **PPT**, and the **final labeled CSV output**

The approach is transparent, auditable, and operationally aligned with maritime intelligence needs.

---

## 📌 1. Project Objective

The goal is to identify **high-confidence GPS jamming/spoofing** events using a blend of physics-based rules, data exploration, and spatial hotspot analysis.

Objectives:

- Flag **impossible or unrealistic vessel speeds**
- Detect **repeat interference hotspots** in small grid cells
- Produce an **explainable, labeled dataset** with reasons per event
- Deliver **clean vessel tracks** for reliable upstream analysis

## 📁 2. Repository Structure

📁 project-root/

RedSea_GPS_Jamming_Final_Analysis.ipynb

RedSea_GPS_Jamming_Final_Analysis.html

RedSea_GPS_Jamming_Final_Analysis.pptx

RedSea_GPS_Jamming_Classified_analysis.csv

PartB_Menifot_CleanTracks_Final_Updated.ipynb

PartB_Menifot_CleanTracks_Final_Updated.html

menifot1.csv

menifot2.csv

meetings_red_sea.csv

README.md

## ⚙️ 3. Methodology

### **A) Rule-Based GPS Jamming Detection**

#### **1. Implausible Speed Rule**
Meeting-level implied speed is calculated using geodesic distance and time.  
If speed > realistic limits → the meeting is flagged as *suspected jamming*.

#### **2. Spatial Hotspot Rule**
- Coordinates rounded to **0.02° (~2 km grid)**
- Meeting counts aggregated by grid
- High-density grid cells → potential GNSS interference zones

#### **3. Combined Decision**
If *either* rule triggers:  
`is_jamming_meeting = TRUE`

Each flag includes a clear textual reason.

---

### **B) Exploratory Data Analysis (EDA)**

The notebook contains:

- Speed distributions  
- Distance/time anomaly checks  
- Heatmaps and hotspot clusters  
- Scatter & geographic plots  
- Statistical summary of meetings  

These insights informed threshold selection and hotspot detection.

---

### **C) Part B — Track Cleaning Pipeline**

The Menifot notebook performs:

- Lat/lon jump detection  
- Speed spike removal  
- Heading/bearing anomaly checks  
- Duplicate/stale point detection  
- Visualization of **Original vs Cleaned Tracks**

Reliable cleaned tracks form the foundation for accurate jamming detection.

---

## 📊 4. Key Deliverables

### ✔️ **1. Labeled Jamming CSV**
`RedSea_GPS_Jamming_Classified_analysis.csv`

Contains:

- `meeting_id`
- `is_jamming_meeting`
- `jamming_reason`
- `speed_flag`
- `hotspot_flag`
- distance, duration, implied speed, coordinates, timestamps

Perfect for dashboards, ML training, or intelligence review.

---

### ✔️ **2. Interactive HTML Notebooks**
No Jupyter installation needed — open directly in browser:

- `RedSea_GPS_Jamming_Final_Analysis.html`  
- `PartB_Menifot_CleanTracks_Final_Updated.html`

---

### ✔️ **3. Presentation Deck**
`RedSea_GPS_Jamming_Final_Analysis.pptx`  
Contains a stakeholder-ready summary of:

- Objective  
- Rule design  
- Hotspots  
- Findings  
- Recommendations  

---

## 🧪 5. Reproduce the Analysis

### **Requirements**
```bash
python 3.9+
pandas
numpy
matplotlib
seaborn
scikit-learn
geopy
jupyter
