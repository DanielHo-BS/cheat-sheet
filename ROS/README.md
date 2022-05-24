# ROS

Here shows some cheat about ROS.

# Usage

1. Create workspace

```bash
mkdir -p ~/test_ws/src
```

2. Get the code

```bash
cd test_ws/src
# download the code to here
```

3. Build

```bash
cd ~/test_ws
rosdep install --from-paths src --ignore-src -r -y
colcon build --symlink-install
source install/local_setup.bash
```

4. Lanuch

```bash
ros2 launch <Package> <launch-file>
```