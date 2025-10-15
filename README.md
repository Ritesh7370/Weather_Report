Project Overview

This Power BI report presents a 7-day weather forecast combined with air quality indicators to help monitor local environmental conditions. The dashboard displays temperature trends, humidity, wind speed, pressure, UV index, chance of rain, sunrise/sunset times, and pollutant readings (PM10, PM2.5, CO, NO2, SO2), along with a consolidated AQI card.

Screenshot




 **Live Dashboard:** [View on Power BI Service](https://app.powerbi.com/links/your-dashboard-link)



Key Features

7-day temperature trend line with daily high/low values.

KPI cards for current temperature, humidity, wind speed, visibility, pressure, UV index, and precipitation.

Air quality ring chart and detailed pollutant counts (PM10, PM2.5, CO, NO2, SO2).

Chance-of-rain bar chart for each of the seven days.

Sunrise and sunset times panel.

Dark theme with clean, card-based layout for quick insights.

Interactive tooltips, slicers, and filters for exploring date ranges and locations.

Data Sources

Weather forecast API (e.g., OpenWeatherMap, Weatherbit) — historical and forecast data.

Air quality API (e.g., OpenAQ, AirVisual) — pollutant concentrations and AQI.

Local CSV or Excel files for static datasets.

Note: Replace the example APIs above with the actual data providers you used. Save API keys securely (do not commit them to GitHub).

Data Model (recommended)

WeatherForecast (Date, Location, TempMax, TempMin, TempAvg, Precipitation, RainProbability, WeatherIcon)

CurrentConditions (Timestamp, Location, Temperature, Humidity, WindSpeed, Visibility, Pressure, UVIndex)

AirQuality (Timestamp, Location, PM10, PM2_5, CO, NO2, SO2, AQI)

Relationships:

WeatherForecast[Date] → AirQuality[Date] (many-to-many via a Date table)

Location as a lookup table if multiple cities are supported

Power Query & ETL

Use Power Query to:

Normalize date/time fields and convert to local timezone.

Pivot/unpivot pollutant measurements when necessary.

Merge API responses into clean tables.

Cache API responses into local files during development.

Example DAX Measures
Current Temperature =
CALCULATE(
    AVERAGE(CurrentConditions[Temperature]),
    LASTDATE(CurrentConditions[Timestamp])
)


SevenDayAvgTemp =
CALCULATE(
    AVERAGE(WeatherForecast[TempAvg]),
    DATESINPERIOD(DateTable[Date], LASTDATE(DateTable[Date]), -7, DAY)
)


AQI_Status =
SWITCH(
    TRUE(),
    MAX(AirQuality[AQI]) <= 50, "Good",
    MAX(AirQuality[AQI]) <= 100, "Moderate",
    MAX(AirQuality[AQI]) <= 200, "Unhealthy",
    "Hazardous"
)
Visuals & Design

Use built-in KPI cards for top-line metrics.

Line chart for temperature trends (use markers for daily highs/lows).

Donut or radial gauge for overall AQI with center KPI.

Bar chart for rain probabilities with percent labels.

Small multiples or card grids for pollutant details.

Apply consistent font sizing and spacing; keep the dark theme accessible (contrast ratios).

Deployment

Save the .pbix file and assets (images) in the repo.

Publish to Power BI Service (workspace) and configure scheduled data refresh (use gateway if on-prem data).

Share report/dashboard with stakeholders and set row-level security if needed.

Usage

Open the report and use slicers to change the location or date range.

Hover over charts for tooltips with source timestamps and raw values.

Security & Best Practices

Store API keys in a secure store (Azure Key Vault, environment variables) — never include them in the repository.

Document refresh frequency and data retention policies.

Credits

Built with Power BI, DAX, and Power Query. Icons and visuals courtesy of open-source icon packs (if used).

License

This repository is released under the MIT License. See LICENSE for details.

Contact

Maintainer: Your Name — rraaz73700@gmail.com

If you want, I can also:

Generate a short one-line README for the repo home.

Create a ready-to-paste .md file with your actual repo name, screenshot, and contact details.

Add a LICENSE file (MIT/Apache/GPL) and a sample .gitignore for Power BI files.

Done — I created a README for your GitHub repo in the canvas (titled README.md - 7-Day Weather Dashboard).

Open the document on the left and tell me if you want it shortened, translated, or tailored with your repo name, screenshot file, or contact details.
