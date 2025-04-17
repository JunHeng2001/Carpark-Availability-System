# Carpark-Availability-System


With the increasing demand for efficient urban mobility and the growth of smart city technologies, optimizing parking availability has become a critical focus for both city planners and drivers. As parking costs fluctuate and carpark availability varies based on location, time, and environmental factors, traditional approaches to parking management often fall short in providing real-time, accurate recommendations.

To address this challenge, we propose the use of machine learning (ML) to predict parking lot availability and provide users with optimized parking solutions.

# We want to:
**Predict the relationship between weather and lot availability:** Weather can significantly influence parking patterns, with sheltered carparks becoming more popular during rainy conditions. The ML model will analyze weather data alongside carpark availability to predict which carparks are likely to have available spots based on current or forecasted weather. The system will then recommend carparks with availability, taking into account whether they are sheltered or unsheltered, depending on user preferences and the weather.

# Expected Output

### Nearby Carparks Sorted by Forecasted Availability

| Location                           | Distance (m) | Car Park Type       | Short Term Parking | Free Parking               | Night Parking | Shelter | Forecasted Availability |
|------------------------------------|--------------|---------------------|--------------------|----------------------------|---------------|---------|-------------------------|
| BLK 426/428 CLEMENTI AVENUE 3      | 2713         | SURFACE CAR PARK    | WHOLE DAY          | NO                         | YES           | 0       | 1.000000                |
| 2A Dover Rd, Singapore 131002      | 2415         | MULTI-STOREY CAR PARK | WHOLE DAY          | SUN & PH FR 7AM-10.30PM    | YES           | 1       | 0.719254                |
| NORTH BUONA VISTA ROAD             | 2573         | SURFACE CAR PARK    | WHOLE DAY          | SUN & PH FR 7AM-10.30PM    | YES           | 0       | 0.402585                |
| BLK 426/427 CLEMENTI AVENUE 3      | 2713         | SURFACE CAR PARK    | 7AM-7PM            | NO                         | NO            | 0       | 0.267004                |
| BLK 416A CLEMENTI AVENUE 1         | 2581         | MULTI-STOREY CAR PARK | WHOLE DAY          | SUN & PH FR 7AM-10.30PM    | YES           | 1       | 0.244189                |

# For the application of this system:
User input destination will be the **Time of arrival** and **Weather condition**

# We will be using:
Google maps API to find closest 5 carparks
ML predicts availability with weather data
Output: The 5 closest locations sorted according to availability and user preference

# Using data on carparks
From dataset on carpark information
* Key: Carpark address
* Values:
  * Carpark No.
  * Car park type
    * Surface Car Park
    * Multi-Storey Car Park
    * Basement Car Park
    * Surface/Multi-Storey Car Park
    * Covered Car Park
    * Mechanised and Surface Car Park
    * Mechanised Car Park
  * If there is short term parking (cheaper parking charges)
    - Whole day
    - 7AM-10.30PM
    - 7AM-7PM
  - If there is free parking
    - SUN & PH FR 7AM-10.30PM
    - SUN & PH FR 1PM-10.30PM
  - If there is night parking (10:30pm to 7:00am the following day)

- Other values:
  - If carpark is sheltered
  - Closest weather station

Function
- Takes in user input: destination
- Use Google Maps to find carparks near destination (Get a Google Maps API key from Google Cloud Platform

Backend function: Train ML
- MLP Models trained on time and rain events for availability of every carpark
- From dataset on carpark availability and dataset on weather

Forecast hourly carpark availability given a future time and weather condition
- Takes in user input: eta, weather
- ML model: MLP regressor

Frontend function: Take in user input
- Destination
- Use google maps to check if destination is in Singapore
- Estimated time of arrival (ETA) at destination
- Estimated weather condition upon arrival
- Clear
- Rainy
