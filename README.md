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

## Requirements

- Gazebo Harmonic (gz-sim 8)
- PX4 Autopilot (for x500_base model)

## Installation

Clone this repository and copy the models into PX4's model directory:

```bash
git clone https://github.com/fanchiayu/usagi-model.git
cp -r usagi-model/models/* ~/PX4-Autopilot/Tools/simulation/gz/models/
```

Or use symlinks so updates to this repo take effect immediately:

```bash
git clone https://github.com/fanchiayu/usagi-model.git
ln -s ~/usagi-model/models/usagi  ~/PX4-Autopilot/Tools/simulation/gz/models/usagi
ln -s ~/usagi-model/models/mid360 ~/PX4-Autopilot/Tools/simulation/gz/models/mid360
ln -s ~/usagi-model/models/d435i  ~/PX4-Autopilot/Tools/simulation/gz/models/d435i
```

## Usage

### Launch with PX4 SITL

```bash
cd ~/PX4-Autopilot
make px4_sitl gz_usagi
```

To use a specific world:

```bash
make px4_sitl gz_usagi_indoor
```

### Add to a Gazebo World

To spawn the usagi model inside a `.sdf` world file, add the following inside the `<world>` tag:

```xml
<include>
  <uri>model://usagi</uri>
  <name>usagi</name>
  <pose>0 0 0.2 0 0 0</pose>
</include>
```

The `<pose>` format is `x y z roll pitch yaw` (in meters and radians).
Set `z` to at least `0.2` so the drone spawns slightly above the ground.

### Standalone Gazebo (without PX4)

```bash
export GZ_SIM_RESOURCE_PATH=$GZ_SIM_RESOURCE_PATH:~/PX4-Autopilot/Tools/simulation/gz/models
gz sim your_world.sdf
```

## License

See individual model directories for license information.
