# coupon-acceptance-analysis
An exploratory data analysis of the UCI driver coupon dataset. This project investigates the factors distinguishing drivers who accept coupons from those who reject them, with a deep dive into Bar and Coffee House coupons.

---

# Will the Customer Accept the Coupon?

### Project Context

Imagine driving through town and receiving a coupon on your cell phone for a nearby business. What factors determine whether you accept it? This project analyzes data from the UCI Machine Learning repository to distinguish between customers who accepted a driving coupon versus those who did not.

The goal is to use data visualization and statistical analysis to determine the characteristics of drivers who are most likely to accept coupons for specific venues, with a focus on **Bars** and **Coffee Houses**.

---

### Data Description

The dataset contains survey responses describing driving scenarios (destination, time, weather, passenger, etc.) and user attributes (gender, age, marital status, income, habit frequencies).

* **Target Variable (`Y`)**: 1 (Accepted), 0 (Rejected).
* **Total Observations**: 12,684
* **Attributes Analyzed**: Coupon type, age, income, passenger type, time of day, and frequency of visits to various venues (Bar, CoffeeHouse, etc.).

---

### 1. General Findings (Overall)

* The overall acceptance rate across all coupons in the dataset is approximately **56.8%**.
* **"Carry out & Take away"** coupons have the highest acceptance rate (~73%).
* **"Bar"** coupons have the lowest acceptance rate (~41%).
* **"Coffee House"** coupons have a moderate acceptance rate (~50%).

---

### 2. Specific Analysis: Bar Coupons

#### Problem Statement

Bar coupons have the lowest general acceptance rate (41%). The objective was to identify the specific demographic and behavioral profiles that result in a high likelihood of acceptance to improve marketing efficiency.

#### Key Findings & Statistics

Through exploring the data, we identified that **habit** is the strongest predictor of acceptance, followed by **social context** and **age**.

1. **Frequency of Visits**:
* Drivers who go to a bar **fewer than once a month** accept the coupon only **37%** of the time.
* Drivers who go to a bar **more than 3 times a month** accept the coupon **76.9%** of the time.
* *Interpretation:* Acceptance is driven by existing habits; the coupon incentivizes a behavior the user already engages in.


2. **Age & Maturity**:
* Drivers **over the age of 25** who visit bars more than once a month have an acceptance rate of **69.5%**.
* This contradicts the assumption that bar coupons are primarily for college-aged drivers; settled adults with established habits are better targets.


3. **Social Context (Passengers)**:
* Drivers who visit bars >1/month and have **no child passengers** have an acceptance rate of **71.3%**.
* Conversely, the presence of children drastically reduces acceptance, regardless of habit.



#### Visualizations Used

* **Bar Plot of Acceptance by Frequency**: Demonstrated the steep jump in acceptance for frequent visitors.
* **Grouped Analysis**: Compared acceptance rates between the "Target Group" (Frequent goers, >25, No Kids) vs. "All Others," visually proving the target group is 2x more likely to accept.

#### Actionable Insights

* **Target Audience**: Focus marketing efforts on drivers who already visit bars at least once a month.
* **Demographic Filter**: Prioritize drivers aged 25+.
* **Contextual Filter**: Suppress bar coupons if the driver has passengers classified as "Kid(s)".

---

### 3. Specific Analysis: Coffee House Coupons

#### Problem Statement

Coffee House coupons are the most abundant in the dataset but only have a 50% acceptance rate. The goal was to distinguish the context (time, company) that transforms a "maybe" into a "yes."

#### Key Findings & Statistics

1. **Habitual Drivers**:
* Similar to bars, habit is critical. Frequent visitors (1+ times a month) accept at **66%**, while infrequent visitors accept at only **35%**.


2. **Time of Day**:
* Acceptance peaks at **10 AM** and **2 PM**.
* Acceptance is lowest at **7 AM** and **10 PM**.
* *Interpretation:* Coffee is viewed as a "break" or social activity mid-morning/afternoon, rather than a pre-work necessity (where drivers might be rushing) or late-night activity.


3. **The "Social Facilitator" Effect**:
* Drivers with **Friends** or **Partners** in the car have significantly higher acceptance rates (~60%) compared to those driving alone (~45%).
* Unlike bars, the presence of passengers (adults) is a positive catalyst.


4. **Age Demographics**:
* Drivers **under the age of 21** have the highest acceptance rate (~70% for frequent visitors).
* Acceptance generally declines as age increases, dropping below 45% for those over 50.



#### Visualizations Used

* **Acceptance by Time**: A bar chart revealing the clear 10 AM / 2 PM peaks.
* **Acceptance by Passenger**: highlighted the boost in acceptance when "Friend(s)" are present.
* **Acceptance by Age**: Showed a negative correlation between age and coffee coupon acceptance.

#### Actionable Insights

* **Timing**: Schedule push notifications for **10:00 AM** and **2:00 PM** to align with natural break times.
* **Target Audience**: Prioritize users under the age of 30.
* **Social Targeting**: If passenger data is available, prioritize drivers who are not alone (specifically with friends or partners).

---

### Next Steps and Recommendations

1. **Investigate "Carry Out" Coupons**: Since this category has the highest overall acceptance, analyzing it could reveal baseline behaviors for the "general" population that aren't tied to specific vices (alcohol/caffeine).
2. **Develop a Prediction Model**:
* Use the features identified (Frequency, Age, Passenger, Time) to build a Logistic Regression or Random Forest classifier.
* This would allow for real-time probability scoring of a user accepting a coupon.


3. **Refine Data Collection**:
* The "car" column had too much missing data to be useful. Future surveys should ensure vehicle type or condition is captured, as this might influence "Drive-thru" vs. "Dine-in" behavior.
