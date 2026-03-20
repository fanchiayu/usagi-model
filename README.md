# Usagi UAV Model

Gazebo Harmonic model for indoor autonomous drone with LiDAR and depth camera.

## Sensors

- **Livox Mid-360 LiDAR** - 360° non-repetitive scanning pattern
- **Intel RealSense D435i** - Depth camera with IMU
- **Downward Range Sensor** - For altitude estimation

## Structure

```
models/
├── usagi/          # Main UAV model (based on x500)
├── mid360/         # Livox Mid-360 LiDAR model
└── d435i/          # Intel RealSense D435i model
```

## Usage

Add to your Gazebo model path:

```bash
export GZ_SIM_RESOURCE_PATH=$GZ_SIM_RESOURCE_PATH:/path/to/usagi-model/models
```

## Requirements

- Gazebo Harmonic (gz-sim 8)
- PX4 Autopilot (for x500_base model)

## License

See individual model directories for license information.
