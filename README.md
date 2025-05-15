# React Native Responsive Kit 📱 📊

<div align="center">
  <img src="https://img.shields.io/npm/v/react-native-responsive-kit" alt="npm version" />
  <img src="https://img.shields.io/npm/dt/react-native-responsive-kit" alt="downloads" />
  <img src="https://img.shields.io/github/license/SaeculumSolutions/react-native-responsive-kit" alt="license" />
</div>

A lightweight, powerful toolkit for creating truly responsive React Native applications that adapt beautifully to any device size or orientation.

## ✨ Features

- 📐 **Responsive Dimensions** - Scale components dynamically based on screen size
- 🔤 **Font Scaling** - Maintain readable text across all devices
- 🔄 **Orientation Handling** - Adapt layouts dynamically when devices rotate
- 📱 **Device Detection** - Optimize UIs for phones and tablets
- 📏 **Flexible Breakpoints** - Create adaptive designs with customizable breakpoints

## 📦 Installation

```bash
npm install react-native-responsive-kit
# or
yarn add react-native-responsive-kit
```

## 🚀 Quick Start Guide

Import the utilities you need:

```javascript
import {
  wp,
  hp,
  pxToDpWidth,
  pxToDpHeight,
  responsiveWidth,
  responsiveHeight,
  scaleFont,
  useOrientation,
  isTablet,
  BREAKPOINTS,
  getBreakpoint,
} from "react-native-responsive-kit";
```

## 📚 Documentation

### Responsive Dimensions

#### Percentage-based scaling:

```javascript
// Width: 80% of screen width
// Height: 50% of screen height
<View style={{
  width: wp(80),
  height: hp(50),
  padding: wp(5)
}}>
```

#### Pixel-to-device conversion (from design files):

Easily convert your Figma/Sketch designs (in pixels) to responsive units:

```javascript
// Convert 120px width and 50px height from Figma to device-specific dimensions
<Button style={{
  width: pxToDpWidth(120),
  height: pxToDpHeight(50),
  borderRadius: pxToDpWidth(8)
}}>
```

#### Flexible dimensions API:

```javascript
// Choose between percentage or pixel-based units
<Header style={{
  width: responsiveWidth(100, 'percent'),  // Full width
  height: responsiveHeight(60, 'pixel')    // 60px converted to responsive units
}}>
```

### Font Scaling

Keep text readable on all screen sizes:

```javascript
<Text
  style={{
    fontSize: scaleFont(16),
    lineHeight: scaleFont(24),
  }}
>
  This text scales proportionally on all devices
</Text>
```

### Orientation Handling

Adapt layouts when device orientation changes:

```javascript
function ResponsiveLayout() {
  const orientation = useOrientation(); // 'portrait' or 'landscape'

  return (
    <View
      style={{
        flexDirection: orientation === "landscape" ? "row" : "column",
      }}
    >
      <Sidebar />
      <Content />
    </View>
  );
}
```

### Device Detection

Create device-specific layouts:

```javascript
<View style={{
  padding: isTablet() ? wp(8) : wp(4),
  // Apply different styling for tablets
}}>
```

### Breakpoint System

Define layouts based on screen size categories:

```javascript
function AdaptiveComponent() {
  const screenWidth = Dimensions.get("window").width;
  const breakpoint = getBreakpoint(screenWidth);

  return (
    <View>
      {breakpoint === "small" && <MobileLayout />}
      {breakpoint === "medium" && <TabletLayout />}
      {breakpoint === "large" && <DesktopLayout />}
    </View>
  );
}
```

## 🌟 Complete Example

```javascript
import React from "react";
import { View, Text, StyleSheet, TouchableOpacity } from "react-native";
import {
  wp,
  hp,
  pxToDpWidth,
  pxToDpHeight,
  scaleFont,
  useOrientation,
  isTablet,
} from "react-native-responsive-kit";

const ResponsiveCard = () => {
  const orientation = useOrientation();
  const tablet = isTablet();

  return (
    <View style={styles.container}>
      <Text style={styles.title}>Welcome to Your App</Text>

      <View
        style={[
          styles.card,
          // Adapt card layout based on orientation and device type
          orientation === "landscape" && styles.cardLandscape,
          tablet && styles.cardTablet,
        ]}
      >
        <Text style={styles.cardText}>
          This card adapts to your device's size and orientation
        </Text>

        <TouchableOpacity style={styles.button}>
          <Text style={styles.buttonText}>Get Started</Text>
        </TouchableOpacity>
      </View>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    padding: wp(5),
    alignItems: "center",
    justifyContent: "center",
  },
  title: {
    fontSize: scaleFont(24),
    fontWeight: "bold",
    marginBottom: hp(2),
    textAlign: "center",
  },
  card: {
    width: wp(90),
    padding: pxToDpWidth(16),
    borderRadius: pxToDpWidth(8),
    backgroundColor: "#f0f0f0",
    alignItems: "center",
  },
  cardLandscape: {
    width: wp(60),
    flexDirection: "row",
    justifyContent: "space-between",
  },
  cardTablet: {
    maxWidth: 500, // Cap max width on tablets
    shadowColor: "#000",
    shadowOffset: { width: 0, height: 2 },
    shadowOpacity: 0.2,
    elevation: 3,
  },
  cardText: {
    fontSize: scaleFont(16),
    textAlign: "center",
    marginBottom: hp(2),
  },
  button: {
    backgroundColor: "#007AFF",
    paddingVertical: pxToDpHeight(12),
    paddingHorizontal: pxToDpWidth(24),
    borderRadius: pxToDpWidth(8),
  },
  buttonText: {
    color: "white",
    fontSize: scaleFont(16),
    fontWeight: "600",
  },
});

export default ResponsiveCard;
```

## 💪 Why Use React Native Responsive Kit?

- **Design Fidelity**: Precisely translate designs into responsive interfaces
- **Developer Productivity**: Focus on features rather than screen adaptation logic
- **Future-Proof**: Handles new device sizes automatically
- **Lightweight**: Minimal impact on bundle size and performance
- **Type Safety**: Full TypeScript support

### ⚡ Performance Optimized

React Native Responsive Kit is carefully optimized to have minimal impact on your app's performance:

- No external dependencies
- Efficient calculations
- Minimal re-renders
- Small bundle size

<!-- ## 🛠️ Contributing

We welcome contributions! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request -->

## 📄 License

This project is licensed under the ISC License - see the LICENSE file for details.

---

<div align="center">
  <sub>Built with ❤️ by <a href="https://github.com/SaeculumSolutions">Saeculum Solutions</a></sub>
</div>
