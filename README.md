# JacAssignment1
# AI-Enhanced Weather Advisor - Usage Guide

## Overview
A simple weather advisor that demonstrates:
- *Step 5*: Scale agnostic deployment (local CLI → cloud API)
- *Step 6*: AI-powered outfit suggestions, activity recommendations, and health tips

## Step 5: Scale Agnostic Approach

### Local Mode
bash
# Run locally
jac run weather_advisor.jac


*Sample Output:*

=== AI-Enhanced Weather Advisor - Local Mode ===

--- Weather for New York ---
🌤  Weather in New York:
   Temperature: 15°C
   Condition: sunny
   Humidity: 45%
   Air Quality: good

--- AI Recommendations for New York ---
👔 Outfit Recommendation: Perfect weather for a light jacket and comfortable jeans! 
   The sunny skies call for sunglasses too. ☀
🎯 Activity Suggestions: Great day for a walk in Central Park or outdoor café hopping! 
   The pleasant temperature is perfect for sightseeing.

--- Health Tips for New York ---
🏥 Health Tips: With good air quality and mild temperature, it's perfect for outdoor 
   exercise! Stay hydrated and enjoy the sunshine for vitamin D.


### Cloud Deployment
bash
# Deploy as web service
jac serve weather_advisor.jac


*Auto-generated API endpoints:*
- GET /WeatherAdvisor/get_weather
- GET /WeatherAdvisor/get_recommendations
- GET /WeatherAdvisor/get_health_advice
- POST /WeatherAPI/handle_request
- GET /LocationWeather/quick_check
- GET /SystemStatus/check

## Step 6: AI-Enhanced Features

### 1. Smart Outfit Suggestions
jac
def suggest_outfit(temp: int, condition: str, humidity: int) -> str by llm();


*AI analyzes:*
- Temperature for layering advice
- Weather conditions for appropriate materials
- Humidity for comfort recommendations

### 2. Activity Recommendations
jac
def suggest_activities(temp: int, condition: str, location: str) -> str by llm();


*AI considers:*
- Weather suitability for activities
- Location-specific attractions
- Temperature-appropriate options

### 3. Health & Wellness Tips
jac
def health_tips(temp: int, condition: str, air_quality: str) -> str by llm();


*AI provides:*
- Air quality-based exercise advice
- Temperature-related health warnings
- Weather-specific wellness tips

## API Usage Examples

### Basic Weather Check
bash
curl -X GET "http://localhost:8000/WeatherAdvisor/get_weather?location=London"


*Response:*
json
{
  "location": "London",
  "temperature": 8,
  "condition": "cloudy",
  "humidity": 75,
  "air_quality": "moderate",
  "timestamp": "2025-01-16 10:00"
}


### AI Recommendations
bash
curl -X GET "http://localhost:8000/WeatherAdvisor/get_recommendations?location=London"


*Response:*
json
{
  "location": "London",
  "outfit_recommendation": "Layer up! A warm sweater under a waterproof jacket would be perfect. Don't forget an umbrella! ☂",
  "activity_suggestions": "Perfect weather for museum visits or cozy pub time. Maybe catch a West End show!",
  "based_on": {
    "temperature": 8,
    "condition": "cloudy",
    "humidity": 75
  }
}


### Comprehensive Report
bash
curl -X POST "http://localhost:8000/WeatherAPI/handle_request" \
  -H "Content-Type: application/json" \
  -d '{
    "location": "Tokyo",
    "action": "full_report"
  }'


### Quick Location Check
bash
curl -X GET "http://localhost:8000/LocationWeather/quick_check?city=Tokyo"


### System Status
bash
curl -X GET "http://localhost:8000/SystemStatus/check"


*Response:*
json
{
  "service": "AI Weather Advisor",
  "status": "operational",
  "version": "1.0.0",
  "data": {
    "weather_locations": 3,
    "user_preferences": 1,
    "locations_tracked": ["New York", "London", "Tokyo"]
  }
}


## Key Demonstrations

### Step 5 Benefits:
1. *Zero Code Changes*: Same WeatherAdvisor walker works locally and as API
2. *Automatic REST API*: Each walker method becomes an HTTP endpoint
3. *Flexible Deployment*: Choose between CLI tool or web service
4. *Consistent Behavior*: AI features work identically in both modes

### Step 6 Benefits:
1. *Context-Aware AI*: Considers location, weather, and user context
2. *Natural Language Output*: Human-friendly recommendations
3. *Easy LLM Switching*: Toggle between OpenAI and Gemini
4. *Enhanced UX*: Transforms raw data into actionable insights

## Real-World Applications

This pattern works for:
- *Weather apps* with personalized recommendations
- *Travel advisors* with location-specific tips
- *Health apps* with environmental awareness
- *Fashion apps* with weather-appropriate styling

## Testing Both Steps

1. *Local Development:*
   bash
   jac run weather_advisor.jac
   
   See AI recommendations in terminal

2. *Cloud Deployment:*
   bash
   jac serve weather_advisor.jac
   
   Same AI features via REST API

3. *API Integration:*
   bash
   # Get weather + AI recommendations in one call
   curl -X POST "http://localhost:8000/WeatherAPI/handle_request" \
     -H "Content-Type: application/json" \
     -d '{"location": "Paris", "action": "full_report"}'
   

The same AI-enhanced weather logic seamlessly transitions from local CLI tool to cloud-ready API service!
