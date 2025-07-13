# Breathing Monitor Feature

## Overview

The BreatheCheck app includes an advanced **Breathing Monitor** that analyzes your breathing patterns in real-time using your device's microphone. This feature provides:

- **5-second breathing analysis** with real-time audio processing
- **Intelligent scoring system** (0-100) based on multiple breathing metrics
- **Personalized insights** and breathing recommendations
- **Session history** tracking your progress over time
- **Privacy-first design** - all processing happens locally

## How It Works

### **Audio Analysis Process**

1. **Microphone Access**: Requests permission to access your device microphone
2. **Real-time Processing**: Analyzes audio frequency and volume patterns
3. **Breathing Detection**: Identifies inhale, hold, and exhale phases
4. **Pattern Analysis**: Calculates rhythm, depth, and consistency metrics
5. **Score Generation**: Combines metrics into a comprehensive breathing score

### **Scoring Algorithm**

The breathing score (0-100) is calculated using:

- **Consistency (40%)**: How regular your breathing rhythm is
- **Rhythm Score (35%)**: Compared to optimal 12 breaths per minute
- **Depth Score (25%)**: Based on volume range and breath depth

## Features

### **Real-time Monitoring**
- **Live audio level indicator** showing microphone input
- **Breathing phase detection** (inhale/hold/exhale)
- **Visual feedback** with animated breathing guide
- **5-second countdown** with progress tracking

### **Intelligent Analysis**
- **Volume spike detection** for breath identification
- **Frequency analysis** for breathing quality assessment
- **Consistency scoring** based on rhythm regularity
- **Noise filtering** with echo cancellation

### **Quality Ratings**

| Score | Quality | Description |
|-------|---------|-------------|
| 85-100 | Excellent | Outstanding breathing pattern with optimal rhythm and depth |
| 70-84 | Good | Well-controlled breathing with minor areas for improvement |
| 50-69 | Fair | Acceptable pattern but could benefit from practice |
| 0-49 | Poor | Irregular pattern - consider breathing exercises |

### **Personalized Insights**

Each analysis provides specific recommendations:
- **Technique improvements** (depth, rhythm, consistency)
- **Breathing exercises** (4-7-8 technique, box breathing)
- **Environmental adjustments** (microphone positioning)
- **Practice suggestions** based on your specific patterns

## Privacy & Security

### **Data Protection**
- **Local processing only** - audio never leaves your device
- **No audio storage** - data is processed in real-time and discarded
- **Session data only** - only scores and insights are saved locally
- **No cloud transmission** - complete privacy protection

### **Permissions**
- **Microphone access** required for breathing analysis
- **Graceful degradation** if permission denied
- **Clear permission prompts** explaining data usage

## Usage Instructions

### **Getting Started**
1. Navigate to **"Breathing Log"** tab in the bottom navigation
2. Click **"Enable Microphone Access"** when prompted
3. Allow microphone permissions in your browser
4. Position yourself in a quiet environment

### **Running Analysis**
1. Click **"Start 5-Second Analysis"**
2. Breathe normally and naturally
3. Watch the real-time breathing phase indicator
4. Wait for analysis completion
5. Review your score and insights

### **Best Practices**
- **Quiet environment** for accurate detection
- **Natural breathing** - don't force or change your pattern
- **Consistent positioning** relative to microphone
- **Regular practice** to track improvement over time

## Technical Implementation

### **Audio Processing**
```typescript
// Web Audio API integration
const audioContext = new AudioContext()
const analyser = audioContext.createAnalyser()
analyser.fftSize = 256
analyser.smoothingTimeConstant = 0.8
```

### **Real-time Analysis**
- **RequestAnimationFrame** for smooth 60fps analysis
- **Frequency domain analysis** using FFT
- **Volume normalization** for consistent scoring
- **Peak detection** algorithm for breath counting

### **Browser Compatibility**
- **Modern browsers** with Web Audio API support
- **HTTPS required** for microphone access
- **Mobile responsive** design for phone/tablet use
- **Progressive enhancement** with graceful fallbacks

## Files Structure

### **Components**
- **`components/breathing-monitor.tsx`** - Main breathing monitor component
- **`app/page.tsx`** - Integration with main navigation
- **Existing UI components** - Leverages shadcn/ui system

### **Key Dependencies**
- **Web Audio API** - Native browser audio processing
- **MediaDevices API** - Microphone access
- **React hooks** - State management and effects
- **TypeScript** - Type-safe audio analysis

## Customization Options

### **Adjusting Scoring Algorithm**
```typescript
// Modify weights in calculateBreathingScore()
const finalScore = Math.round(
  (consistency * 0.4) +     // Consistency weight
  (rhythmScore * 0.35) +    // Rhythm weight  
  (depthScore * 0.25)       // Depth weight
)
```

### **Recording Duration**
```typescript
const RECORDING_DURATION = 5000 // Change to desired milliseconds
```

### **Analysis Sensitivity**
```typescript
// Adjust peak detection threshold
const peakThreshold = avgVolume * 1.2 // Increase for less sensitive
```

## Future Enhancements

### **Planned Features**
1. **Guided breathing exercises** with audio/visual cues
2. **Historical trend analysis** with charts and progress tracking
3. **Export functionality** for health app integration
4. **Custom session lengths** (10s, 30s, 1min options)
5. **Advanced metrics** (heart rate variability estimation)

### **Potential Integrations**
- **Health apps** (Apple Health, Google Fit)
- **Meditation apps** integration
- **Stress monitoring** correlation
- **Sleep quality** analysis
- **Exercise performance** optimization

## Troubleshooting

### **Common Issues**

**Microphone not working:**
- Check browser permissions in settings
- Ensure HTTPS connection (required for mic access)
- Try different browser if issues persist
- Check system microphone settings

**Low or no audio detection:**
- Move closer to microphone
- Check system audio levels
- Ensure quiet environment
- Try breathing more audibly (not forced)

**Inconsistent scores:**
- Maintain consistent environment
- Use same device/microphone
- Keep steady position during analysis
- Practice regular breathing patterns

**Browser compatibility:**
- Use modern browsers (Chrome, Firefox, Safari, Edge)
- Update browser to latest version
- Enable Web Audio API if disabled
- Check for browser extensions blocking audio

The breathing monitor provides professional-grade breathing analysis with consumer-friendly simplicity, helping users improve their respiratory health through data-driven insights and personalized recommendations.
