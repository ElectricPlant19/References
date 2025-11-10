### 🏥 Health Status Determination
        
        The **Overall Score** (0-100) is calculated using weighted components:
        
        #### 📊 Score Components:
        - **Inclination Score (35%)**: Deviation from target inclination
          - Penalty for deviation from target
          - Additional penalty for unstable inclination (high std deviation)
        
        - **Maintenance Score (25%)**: **🆕 Dynamic Pattern-Based Assessment**
          - **Individual Learning**: Each satellite's maneuver pattern is analyzed from historical data
          - **Pattern Detection**: Calculates median interval between maneuvers (e.g., 30 days, 60 days, etc.)
          - **Adaptive Scoring**: 
            - ✅ **On Schedule**: Last maneuver within expected window → Score: 100
            - ⏱️ **Due Soon**: Approaching next window (1.0-1.5x interval) → Score: 90
            - ⚠️ **Overdue**: Beyond 1.5x expected interval → Score: 60
            - 🔴 **Critical**: Beyond 2x expected interval → Score: 30
            - 💀 **Severe**: Beyond 3x expected interval → Score: 0
          - **Confidence Weighting**: Score adjusted based on pattern consistency
        
        - **Drift Score (25%)**: Longitudinal drift analysis
          - GSO satellites: Should maintain minimal drift (<0.05°/day)
          - IGSO satellites: Higher drift tolerance (up to 2°/day normal)
          - Penalties for unstable drift patterns
        
        - **Uniformity Score (15%)**: Maneuver spacing regularity
          - Regular spacing → Better planning and control
          - Irregular spacing → Reactive corrections
        
        #### 🎯 Health Status Thresholds:
        - **🟢 Healthy**: Score ≥ 80
        - **🟡 Fair**: Score 60-79
        - **🟠 Degraded**: Score 40-59
        - **🔴 Critical**: Score < 40
        
        #### 🔍 Dynamic Pattern Analysis Features:
        - **No Hard-Coded Intervals**: Each satellite defines its own correction cadence
        - **Pattern Confidence**: High/Medium/Low based on consistency of historical intervals
        - **Predictive Alerts**: Estimates when next maneuver is expected
        - **Overdue Detection**: Flags satellites missing their expected correction window
        - **Adaptive to Changes**: Automatically adjusts to new operational patterns
        
        #### 📈 Additional Factors:
        - Drift trend analysis (increasing/decreasing)
        - Altitude monitoring (graveyard orbit detection)
        - Maneuver type distribution (EW vs NS)
        - Orbital stability metrics
      
