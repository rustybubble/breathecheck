# BreatheCheck App

A comprehensive respiratory health monitoring application built with **Next.js 15**, **React 19**, and **TypeScript**. BreatheCheck helps users track their breathing patterns, monitor allergy risks, and improve their respiratory wellness through data-driven insights.

## 🌟 Features

### **1. Live Breathing Monitor**
- **Real-time audio analysis** using Web Audio API
- **5-second breathing pattern assessment**
- **Intelligent scoring system** (0-100) based on rhythm, depth, and consistency
- **Personalized insights** and breathing recommendations
- **Session history** tracking with progress monitoring
- **Privacy-first** - all processing happens locally on your device

### **2. Allergy Forecast**
- **Real-time weather data** integration with WeatherAPI.com
- **Intelligent allergy risk assessment** based on multiple environmental factors
- **5-day forecast** with daily risk predictions
- **Location-aware** with automatic detection or manual selection
- **Personalized recommendations** for different risk levels
- **Air quality monitoring** with PM2.5, ozone, and pollen data

### **3. Responsive Mobile Design**
- **Mobile-first** interface optimized for touch devices
- **Modern UI** using shadcn/ui component library
- **Smooth animations** and intuitive navigation
- **Progressive Web App** capabilities

## 🚀 Quick Start

### **Prerequisites**
- **Node.js 18+** 
- **npm** or **pnpm**
- **Modern browser** with Web Audio API support

### **Installation**
```bash
# Clone the repository
git clone <repository-url>
cd breathecheck-app

# Install dependencies
npm install --legacy-peer-deps

# Create environment file
cp .env.example .env.local

# Add your Weather API key (optional)
# Get free API key from https://www.weatherapi.com/
echo "WEATHER_API_KEY=your_api_key_here" >> .env.local

# Start development server
npm run dev
```

### **Access the App**
Open [http://localhost:3000](http://localhost:3000) in your browser

## 📱 Usage

### **Breathing Monitor**
1. Navigate to the **"Breathing Log"** tab
2. Enable microphone permissions when prompted
3. Click **"Start 5-Second Analysis"**
4. Breathe normally and review your results
5. Track progress over multiple sessions

### **Allergy Forecast**
1. Go to the **"Forecast"** tab
2. Allow location access for local weather data
3. View current conditions and 5-day outlook
4. Follow personalized recommendations based on risk levels

## 🛠️ Technology Stack

### **Frontend Framework**
- **Next.js 15** - React framework with App Router
- **React 19** - Latest React with concurrent features
- **TypeScript** - Type-safe development

### **UI Components**
- **shadcn/ui** - Modern component library
- **Radix UI** - Accessible primitive components
- **Tailwind CSS** - Utility-first styling
- **Lucide React** - Beautiful icon library

### **Data Visualization**
- **Recharts** - Interactive charts for weather trends
- **Custom animations** - Smooth breathing visualizations

### **Audio Processing**
- **Web Audio API** - Real-time audio analysis
- **MediaDevices API** - Microphone access
- **Custom algorithms** - Breathing pattern detection

### **External APIs**
- **WeatherAPI.com** - Weather and air quality data
- **Browser Geolocation** - Automatic location detection

## 📋 Project Structure

```
breathecheck-app/
├── app/                          # Next.js App Router
│   ├── api/weather/             # Weather API proxy
│   ├── layout.tsx               # Root layout
│   ├── page.tsx                 # Main application
│   └── globals.css              # Global styles
├── components/                   # React components
│   ├── ui/                      # shadcn/ui components
│   ├── allergy-forecast.tsx     # Weather & allergy forecast
│   ├── breathing-monitor.tsx    # Breathing analysis
│   └── theme-provider.tsx      # Theme management
├── lib/                         # Utility libraries
│   ├── utils.ts                 # General utilities
│   └── weather.ts               # Weather service & algorithms
├── public/                      # Static assets
└── docs/                        # Documentation
    ├── FORECAST_SETUP.md        # Allergy forecast guide
    └── BREATHING_MONITOR.md     # Breathing monitor guide
```

## 🔧 Configuration

### **Environment Variables**
```bash
# .env.local
WEATHER_API_KEY=your_weatherapi_key    # Optional - uses mock data if not provided
DEFAULT_LOCATION=San Francisco,CA      # Fallback location
```

### **API Configuration**
- **Weather API**: Free tier provides 1M calls/month
- **Mock data**: Realistic fallback when API unavailable
- **Security**: API key protected via server-side proxy

## 🎯 Features in Detail

### **Breathing Analysis Algorithm**
```typescript
// Scoring components (0-100 scale)
- Consistency (40%): Rhythm regularity
- Breathing Rate (35%): Compared to optimal 12 breaths/min
- Depth (25%): Volume range and breath intensity
```

### **Allergy Risk Calculation**
```typescript
// Risk factors considered
- Pollen levels (seasonal estimation)
- Temperature (15-25°C optimal)
- Humidity (40-60% ideal)
- Air quality (PM2.5, ozone, etc.)
```

### **Privacy & Security**
- **Local audio processing** - no data transmitted
- **API key protection** - server-side proxy
- **No user tracking** - privacy-first design
- **Secure HTTPS** - required for microphone access

## 🚧 Development

### **Available Scripts**
```bash
npm run dev          # Start development server
npm run build        # Build for production  
npm run start        # Start production server
npm run lint         # Run ESLint
```

### **Code Quality**
- **TypeScript** strict mode enabled
- **ESLint** for code quality
- **Prettier** for code formatting
- **Component-driven** architecture

## 📊 Performance

### **Optimizations**
- **Next.js App Router** for optimal performance
- **Component code splitting** with lazy loading
- **Image optimization** with Next.js Image component
- **API route caching** for weather data
- **Real-time processing** with minimal latency

## 🌐 Browser Support

### **Required Features**
- **Web Audio API** (Chrome 25+, Firefox 25+, Safari 14+)
- **MediaDevices API** (Chrome 53+, Firefox 36+, Safari 11+)
- **ES2020** language features
- **HTTPS** for microphone access

## 📈 Future Roadmap

### **Short Term**
- [ ] **Guided breathing exercises** with visual cues
- [ ] **Historical trend charts** for progress tracking
- [ ] **Export functionality** for health apps
- [ ] **Push notifications** for high allergy risk days

### **Long Term**
- [ ] **Machine learning** for personalized predictions
- [ ] **Health app integrations** (Apple Health, Google Fit)
- [ ] **Advanced biometrics** (heart rate variability)
- [ ] **Social features** for community support

## 🤝 Contributing

We welcome contributions! Please see our contributing guidelines for details on:
- **Code style** and conventions
- **Testing** requirements
- **Pull request** process
- **Issue** reporting

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- **WeatherAPI.com** for weather data services
- **shadcn/ui** for beautiful component library
- **Radix UI** for accessible primitives
- **Vercel** for deployment and hosting
- **Open source community** for amazing tools and libraries

## 📞 Support

For questions, issues, or feature requests:
- **GitHub Issues** for bug reports and features
- **Documentation** in `/docs` folder
- **Examples** in component source code

---

**Built with ❤️ for better respiratory health**
