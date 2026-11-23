# Three.js AR - Hit Test Demo

A demonstration application showcasing **WebXR AR hit testing** functionality using Three.js. This project enables interactive augmented reality experiences on mobile devices by detecting and interacting with real-world surfaces through the WebXR API.

## Description

This application demonstrates how to use the WebXR HitTest API to detect physical surfaces in the real world and place virtual objects at those locations. The hit test feature allows your AR experience to understand where users are pointing or looking, enabling precise object placement and interaction with the environment.

The demo includes a reticle that follows the user's gaze through hit testing, providing visual feedback about which surfaces can be interacted with in the real world.

## Features

- **WebXR AR Support**: Full support for Augmented Reality on mobile devices
- **Hit Testing**: Detects and tracks physical surfaces in the real environment
- **Interactive Reticle**: Visual indicator that follows hit test results, showing where objects can be placed
- **Object Spawning**: Two controllers trigger cylinder spawning when selecting hit-test locations
- **Real-time Tracking**: Continuous tracking of environmental surfaces as users move around

## Setup Instructions

### Prerequisites

- A modern web browser with WebXR support (Chrome, Edge, Safari on iOS)
- Mobile device with AR capabilities (iOS devices with ARKit or Android devices with ARCore)
- HTTPS connection or localhost for security (required by WebXR API)

### Running the Application

1. **Open in a mobile browser**: Navigate to your local server URL on your mobile device
2. **Enable AR mode**: Tap the "AR" button that appears in the top-left corner
3. **Grant camera permissions**: Allow access to your device's camera when prompted
4. **Start exploring**: Move around and look at surfaces - the reticle will follow your gaze

### Development Setup

```bash
# Start a local server (required for WebXR)
python -m http.server 8000
# or use any other HTTP server
```

Then access `http://localhost:8000` in your mobile browser.

## Usage Examples

### Basic Hit Test Interaction

1. **Look around**: Move your device to scan the environment
2. **Point at surfaces**: The reticle will appear on detectable surfaces (walls, floors, tables)
3. **Select locations**: Tap or click when the reticle is positioned where you want to place an object
4. **Observe results**: Cylinders spawn at hit-test coordinates

### Controller Interaction

The application provides two controllers for interaction:
- **Controller 1**: Primary selection tool - tap to spawn objects
- **Controller 2**: Secondary selection tool - also spawns objects on select

Both controllers trigger the same behavior when selecting a hit-test location.

## Technical Details

### WebXR API Integration

This project uses the following WebXR features:

```javascript
// Enable hit testing in the XR session
xrSession.requestReferenceSpace('viewer').then((referenceSpace) => {
  // Use reference space for hit testing
});

// Perform hit test to find surfaces
hitTestSource.setReferenceSpace(referenceSpace);
hitTestSource.addEventListener('hittestresult', (event) => {
  // Handle detected surfaces
});
```

### Key Components

- **ARButton**: Located in `jsm/webxr/ARButton.js` - Provides the AR mode toggle button for mobile devices
- **Hit Test Source**: Manages hit testing results and surface detection
- **Reticle System**: Visual feedback component that follows hit-test coordinates
- **Object Spawner**: Places 3D objects at detected surface locations

### Import Structure

The project uses an import map to load Three.js modules:

```javascript
{
  "imports": {
    "three": "./build/three.module.js",
    "three/addons/": "./jsm/"
  }
}
```

### Supported Browsers and Devices

- **iOS**: Safari on iPhone/iPad with ARKit support (iOS 13+)
- **Android**: Chrome on Android devices with ARCore support
- **Desktop**: Not supported - WebXR requires mobile hardware

## Troubleshooting

### Camera Permission Denied
- Ensure you're using HTTPS or localhost
- Check browser settings for camera permissions
- Try a different browser if needed

### No Surfaces Detected
- Move to a well-lit environment
- Look at flat, textured surfaces (walls, floors, tables)
- Avoid reflective or transparent surfaces
- Ensure your device's AR capabilities are enabled in system settings

### Reticle Not Appearing
- Verify WebXR is properly initialized
- Check that hit testing is enabled in the XR session
- Ensure you're looking at detectable surfaces

## Browser Support

| Browser | Version | Status |
|---------|---------|--------|
| Chrome (Android) | 90+ | ✅ Supported |
| Safari (iOS) | 13+ | ✅ Supported |
| Edge (Android) | 90+ | ✅ Supported |
| Firefox | All versions | ❌ Not supported |

## License

This project is provided as a demonstration of WebXR AR hit testing capabilities.

## Resources

- [WebXR Hit Test API Documentation](https://developer.mozilla.org/en-US/docs/Web/API/XRHitTestSource)
- [Three.js WebXR Examples](https://threejs.org/examples/)
- [ARCore Developer Guide](https://developers.google.com/ar/dev-guide)
- [ARKit Documentation](https://developer.apple.com/augmented-reality/arkit/)

## Contributing

Feel free to fork this project and experiment with different hit test scenarios, object types, or interaction patterns. This demo serves as a foundation for building more complex AR experiences.
