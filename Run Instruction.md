---

# Run Instructions (Lab 4: Reactive Obstacle Avoidance / Follow-the-Gap)

## Prerequisites

* ROS 2 Humble installed
* The F1TENTH gym simulation (same as Lab 2 / Lab 3) is working
* Your `roboracer_ws` contains the Lab 4 package (the one that includes `reactive_node.py`, typically named `gap_follow`)

---

## Terminal 1 — Start the simulation (same as Lab 2 / Lab 3)

Open a terminal and launch the F1TENTH gym simulation exactly the same way you did in Lab 2 / Lab 3.

Example environment sourcing:

```bash
cd ~/sim_ws
source ~/sim_ws/.venv/bin/activate
source /opt/ros/humble/setup.bash
source ~/sim_ws/install/local_setup.bash
```

Then launch the simulator/bridge:

```bash
ros2 launch f1tenth_gym_ros gym_bridge_launch.py
```

---

## Terminal 2 — Build only the Lab 4 package and run reactive driving

Open a second terminal:

### 1) Build only the Lab 4 package

```bash
cd ~/roboracer_ws
source /opt/ros/humble/setup.bash
colcon build --symlink-install --packages-select gap_follow
source install/local_setup.bash
```

### 2) Run the Python reactive node (IMPORTANT: include `.py`)

```bash
ros2 run gap_follow reactive_node.py
```

---

## Notes

* This package is intended to be run as a **Python script** using:

  ```bash
  ros2 run gap_follow reactive_node.py
  ```

* If you modify only Python code and you built with `--symlink-install`, you typically **do not need to rebuild** every time.
  However, if you changed package setup files / dependencies, or the system isn’t picking up updates, rebuild with:

  ```bash
  cd ~/roboracer_ws
  rm -rf build/gap_follow install/gap_follow log/
  colcon build --symlink-install --packages-select gap_follow
  source install/local_setup.bash
  ```

---


