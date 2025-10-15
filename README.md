# 7-Day Weather Forecast & Air Quality Dashboard

> **Power BI Project** — Interactive dashboard visualizing 7-day weather forecast and air quality for Gurgaon.

---

## 🌦️ Project Overview

This Power BI report presents a **7-day weather forecast** combined with **air quality indicators** to monitor environmental conditions in Gurgaon. The dashboard provides detailed insights on temperature trends, humidity, wind speed, pressure, UV index, precipitation, sunrise/sunset times, and pollutant readings (PM10, PM2.5, CO, NO2, SO2), along with an overall AQI status indicator.

---

## 📸 Dashboard Screenshot

![Weather Dashboard](https://github.com/Ritesh7370/Weather_Report/blob/main/assets/Screenshot_WeatherDashboard.png)

> *(If the image doesn’t appear, check that the screenshot file is uploaded to the `/assets` folder in your GitHub repo.)*

---

## 🔑 Key Features

* 🌡️ **Current weather conditions** — temperature, humidity, visibility, pressure, wind speed, and UV index.
* 📈 **7-day forecast** with temperature trend line and weather icons.
* 🌅 **Sunrise & sunset timing** panel.
* 💨 **Air quality visualization** with pollutant details (PM10, PM2.5, CO, NO2, SO2).
* ☔ **Chance of rain** chart for all forecasted days.
* 🎨 **Modern dark-themed UI** with responsive card design and smooth layout.

---

## 🧠 Tools & Techniques

* **Power BI Desktop** — dashboard design and data modeling.
* **DAX** — for custom calculations and AQI classifications.
* **Power Query** — for data cleaning and transformation.
* **APIs** — to fetch weather and air quality data (e.g., OpenWeatherMap, AirVisual).

---

## 🧩 Example DAX Measures

```dax
Current Temperature =
CALCULATE(
    AVERAGE(CurrentConditions[Temperature]),
    LASTDATE(CurrentConditions[Timestamp])
)

AQI_Status =
SWITCH(
    TRUE(),
    MAX(AirQuality[AQI]) <= 50, "Good",
    MAX(AirQuality[AQI]) <= 100, "Moderate",
    MAX(AirQuality[AQI]) <= 200, "Unhealthy",
    "Hazardous"
)
```

---

## ⚙️ How to Use

1. Clone this repository:

   ```bash
   git clone https://github.com/Ritesh7370/Weather_Report.git
   ```
2. Open the `.pbix` file in **Power BI Desktop**.
3. Connect your weather and air quality data sources.
4. Refresh the data and publish the report to **Power BI Service**.

---

## 🌍 Live Demo

🔗 [View on GitHub](https://github.com/Ritesh7370/Weather_Report)

> *(Add Power BI Service link here if published online)*

---

## 👨‍💻 Author

**Ritesh Kumar**
📧 [ritesh@example.com](mailto:ritesh@example.com) *(replace with your actual contact)*
📂 [GitHub Profile](https://github.com/Ritesh7370)

---

## 📜 License

This project is open-source and available under the **MIT License**.

---

### ⭐ If you like this project, don’t forget to star the repo on GitHub!
