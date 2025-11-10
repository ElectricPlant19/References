# 🏥 Health Status Determination

The **Overall Score (0–100)** is calculated using weighted components.

## 📊 Score Components

### **1. Inclination Score (35%)**
Measures how well the satellite maintains its target inclination.

- Penalty for deviation from target  
- Additional penalty for unstable inclination (high standard deviation)

---

### **2. Maintenance Score (25%) — 🆕 Dynamic Pattern-Based Assessment**
Uses historical maneuver data to estimate expected correction intervals.

#### ✅ Key Features
- **Individual Learning**: Each satellite’s maneuver pattern is learned from historical intervals.  
- **Pattern Detection**: Detects typical maneuver spacing (e.g., 30 days, 60 days).  

#### **Adaptive Scoring**
| Condition | Meaning | Score |
|----------|----------|--------|
| ✅ **On Schedule** | Last maneuver within expected window | **100** |
| ⏱️ **Due Soon** | 1.0–1.5× expected interval | **90** |
| ⚠️ **Overdue** | >1.5× expected interval | **60** |
| 🔴 **Critical** | >2× expected interval | **30** |
| 💀 **Severe** | >3× expected interval | **0** |

- **Confidence Weighting**: Score scaled based on pattern consistency.

---

### **3. Drift Score (25%)**
Analyzes longitudinal drift.

- **GSO satellites**: Maintain minimal drift (< **0.05°/day**)  
- **IGSO satellites**: Higher tolerance (up to **2°/day**)  
- Penalties for unstable or increasing drift

---

### **4. Uniformity Score (15%)**
Evaluates regularity of maneuver spacing.

- Regular spacing → Planned station-keeping  
- Irregular spacing → Reactive corrections  

---

## 🎯 Health Status Thresholds

| Status | Score Range |
|--------|--------------|
| 🟢 **Healthy** | ≥ 80 |
| 🟡 **Fair** | 60–79 |
| 🟠 **Degraded** | 40–59 |
| 🔴 **Critical** | < 40 |

---

## 🔍 Dynamic Pattern Analysis (Detailed)

- **No Hard-Coded Intervals**: Each satellite defines its own cadence.  
- **Pattern Confidence**: High / Medium / Low based on interval variance.  
- **Predictive Alerts**: Forecasts next expected maneuver.  
- **Overdue Detection**: Flags missed correction windows.  
- **Adaptive Behavior**: Adjusts automatically if patterns change.

---

## 📈 Additional Factors

- Drift trend (increasing, decreasing, stable)  
- Altitude monitoring (graveyard orbit detection)  
- Maneuver type distribution (EW vs NS)  
- Orbital stability metrics  
