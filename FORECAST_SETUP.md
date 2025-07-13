# Allergy Forecast Feature

## Overview

The BreatheCheck app now includes a comprehensive allergy forecast feature that provides:

- **Current weather conditions** with air quality data
- **Today's allergy risk assessment** based on multiple factors
- **5-day forecast** with daily allergy risk predictions
- **Personalized recommendations** based on risk levels
- **Real-time location detection** or manual location selection

## Setup Instructions

### 1. Weather API Configuration

The forecast feature uses [WeatherAPI.com](https://www.weatherapi.com/) for weather data:

1. **Sign up for a free account** at https://www.weatherapi.com/
2. **Get your API key** from the dashboard
3. **Create environment file**:
   ```bash
   cp .env.example .env.local
   ```
4. **Add your API key** to `.env.local`:
   ```
   WEATHER_API_KEY=your_actual_api_key_here
   ```

### 2. Default Behavior

- **Without API key**: The app uses realistic mock data for demonstration
- **With API key**: Real weather data from WeatherAPI.com
- **API calls**: Routed through `/api/weather` to protect your API key
- **Location**: Auto-detects user location or falls back to San Francisco

## Features

### Allergy Risk Calculation

The app calculates allergy risk scores (0-100) based on:

- **Pollen levels** (estimated from season and temperature)
- **Temperature** (15-25°C optimal, extremes increase risk)
- **Humidity** (40-60% optimal, dry/humid air problematic)
- **Air quality** (PM2.5, ozone, etc. when available)

### Risk Levels

| Score | Level | Color | Meaning |
|-------|-------|-------|---------|
| 0-30 | Low | Green | Great for outdoor activities |
| 31-50 | Moderate | Yellow | Some precautions recommended |
| 51-70 | High | Orange | Limit outdoor exposure |
| 71-100 | Very High | Red | Avoid outdoor activities |

### Recommendations

Each risk level provides specific advice:

- **Outdoor activity suggestions**
- **Window and air filtration guidance** 
- **Medication reminders**
- **Peak time avoidance**

## Usage

### Navigation

1. Open the BreatheCheck app
2. Tap the **"Forecast"** tab in bottom navigation
3. View current conditions and 5-day forecast

### Features Available

- **Auto-refresh** current conditions
- **Location detection** with fallback options
- **Detailed weather metrics** (temp, humidity, UV, air quality)
- **Interactive forecast cards** for each day
- **Risk factor breakdown** showing what's affecting your score
- **Personalized recommendations** for each risk level

### Mobile Optimization

- **Touch-friendly interface** designed for mobile
- **Responsive design** adapts to screen size
- **Fast loading** with optimized API calls
- **Offline graceful degradation** with cached data

## Technical Implementation

### Files Added/Modified

1. **`lib/weather.ts`** - Weather service and risk calculation
2. **`components/allergy-forecast.tsx`** - Main forecast component
3. **`app/api/weather/route.ts`** - Server-side API proxy
4. **`app/page.tsx`** - Integration with main app
5. **`next.config.mjs`** - Environment variable config
6. **`.env.example`** - Configuration template

### API Architecture

```
Client → /api/weather → WeatherAPI.com
```

- **Benefits**: API key protection, rate limiting, caching
- **Fallback**: Mock data when API unavailable
- **Error handling**: Graceful degradation

### Data Flow

1. **Location detection** via browser geolocation
2. **Weather API call** through internal route
3. **Risk calculation** using proprietary algorithm
4. **UI updates** with real-time data
5. **Recommendations** based on calculated risk

## Customization

### Modifying Risk Calculation

Edit `calculateAllergyRisk()` in `lib/weather.ts`:

```typescript
// Adjust temperature sensitivity
if (tempC >= 15 && tempC <= 25) {
  factors.temperature = 20; // Modify this value
}

// Add new factors
factors.windSpeed = weather.current.wind_kph * 0.5;
```

### Adding New Recommendations

Extend the recommendations array:

```typescript
if (score <= 30) {
  recommendations = [
    'Great day for outdoor activities',
    'Perfect for morning jogs', // Add custom advice
    'Ideal for picnics and sports'
  ];
}
```

### Styling Modifications

The component uses Tailwind CSS classes. Key areas:

- **Risk badges**: `getRiskColor()` function
- **Weather icons**: `getWeatherIcon()` function  
- **Card layouts**: Standard shadcn/ui components

## Performance Considerations

- **API rate limiting**: Free tier allows 1M calls/month
- **Caching**: Consider adding Redis for production
- **Error boundaries**: Graceful handling of API failures
- **Loading states**: Smooth UX during data fetching

## Security

- **API key protection**: Never exposed to client
- **Environment variables**: Properly configured
- **Error messages**: Don't leak sensitive information
- **Rate limiting**: Prevent API abuse

## Future Enhancements

Potential improvements:

1. **Historical data** tracking and trends
2. **Push notifications** for high risk days
3. **User preferences** for custom thresholds
4. **Integration** with health apps
5. **Pollen count APIs** for more accurate data
6. **Machine learning** for personalized predictions

## Troubleshooting

### Common Issues

**"Module not found: Can't resolve 'react-is'" error:**
- Install the missing dependency: `npm install react-is --legacy-peer-deps`
- This is required by the Recharts library for the chart visualization
- Clear Next.js cache if needed: `Remove-Item -Recurse -Force .next` (Windows)

**"Using mock data" warning:**
- Check `.env.local` file exists
- Verify `WEATHER_API_KEY` is set correctly
- Restart development server

**Location not detected:**
- Enable location permissions in browser
- Falls back to San Francisco automatically
- Can manually specify location in future updates

**API errors:**
- Check API key validity
- Verify network connectivity
- Mock data provides fallback functionality

### Development

```bash
# Install dependencies
npm install --legacy-peer-deps

# Start development server
npm run dev

# Check environment variables
echo $WEATHER_API_KEY
```

### Package Dependencies

The forecast feature requires these key packages:
- `recharts` - For data visualization charts
- `react-is` - Required by Recharts for React component detection
- Standard React 19 and Next.js 15 dependencies

The forecast feature is now fully integrated and ready for production use!
