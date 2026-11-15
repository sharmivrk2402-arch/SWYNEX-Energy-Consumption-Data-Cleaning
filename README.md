
# ⚡ Smart Energy Consumption Dashboard

## 📌 Project Overview

The Smart Energy Consumption Dashboard is an interactive data analytics project developed using Python and Streamlit. It helps analyze energy consumption patterns and understand how different factors such as temperature, humidity, occupancy, HVAC usage, and lighting usage influence energy consumption.

The dashboard provides interactive visualizations, statistical summaries, and filtering options to explore energy usage data.

## 🎯 Objectives

- Analyze overall energy consumption patterns.
- Identify daily and weekly energy usage trends.
- Understand the relationship between temperature and energy consumption.
- Analyze the impact of occupancy on energy usage.
- Monitor HVAC and lighting usage.
- Explore renewable energy usage.
- Present useful insights through interactive visualizations.

## 🛠️ Technologies Used

- Python
- Pandas
- Streamlit
- Plotly

## 📂 Dataset Description

The project uses a cleaned energy consumption dataset containing 1,000 records and 11 columns.

### Dataset Features

| Column | Description |
|---|---|
| Timestamp | Date and time of the record |
| Temperature | Recorded temperature |
| Humidity | Humidity level |
| SquareFootage | Building area |
| Occupancy | Number of occupants |
| HVACUsage | HVAC operating status |
| LightingUsage | Lighting operating status |
| RenewableEnergy | Renewable energy usage |
| DayOfWeek | Day of the week |
| Holiday | Holiday status |
| EnergyConsumption | Energy consumed |

## 📊 Dashboard Features

1. Key Performance Indicators (KPIs)
2. Daily Energy Consumption Trends
3. Day-wise Energy Consumption Analysis
4. HVAC Usage Distribution
5. Lighting Usage Distribution
6. Temperature vs Energy Consumption
7. Occupancy vs Energy Consumption
8. Renewable Energy Analysis
9. Interactive Date and Category Filters
10. Filtered Dataset Preview and Download

## 🖥️ Dashboard Preview

![Smart Energy Dashboard](screenshots/dashboard.png)

## ⚙️ Installation and Setup

### Step 1: Clone the Repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

### Step 2: Navigate to the Project Folder

```bash
cd Smart-Energy-Dashboard
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 4: Run the Dashboard

```bash
streamlit run app.py
```

## 📁 Project Structure

```text
Smart-Energy-Dashboard/
│
├── app.py
├── cleaned_energy_data.csv
├── requirements.txt
├── README.md
│
└── screenshots/
    └── dashboard.png
```

## 💡 Expected Outcomes

- Better understanding of energy consumption patterns.
- Identification of factors associated with higher energy usage.
- Interactive exploration of energy-related data.
- Clear visualization of energy consumption trends.

## 👩‍💻 Author

**Sharmila R**

B.Tech Artificial Intelligence and Data Science

## 🏷️ Project Category

Data Analytics | Python | Data Visualization | Streamlit
