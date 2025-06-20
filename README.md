# **Glass Crane Operation Assistance**

![System Concept](project_img_1.png)
*Proposal concept: Using ArUco marker detection and BIM integration to guide panel alignment.*

---

## **📌 Description**

A ROS2-based robotic assistance system for precise, joystick-controlled glass panel placement using a mini crane. The system combines:

- **OpenCV + ArUco marker pose detection**  
- **BIM-based target pose extraction**  
- **ROS2 visualization and joystick control**

Developed during Winter 2022 CR Prototyping, it enhances construction safety and precision by providing real-time alignment feedback.

---

## **📸 Project Result Preview**

![RVIZ Visualization](project_img_2.png)
*Final prototype with panel pose in RVIZ compared to BIM target.*

---

## **🛠 Getting Started**

### Requirements

- [ROS2 Humble](https://docs.ros.org/en/humble/Installation.html)
- V4L-compatible USB camera driver
- Joystick for crane control

### Setup

```bash
mkdir -p ptp_ws/src/
cd ptp_ws/src

git clone https://github.com/ros-drivers/usb_cam
git clone https://git.rwth-aachen.de/prototypingproject20222023/ros2_aruco.git
git clone https://git.rwth-aachen.de/prototypingproject20222023/ros2_aruco_interfaces.git
git clone <your-repo-url>  # this package
```

- Update camera device in `usb_cam/params.yaml`  
- Use ArUco marker ID 1 (generate at https://chev.me/arucogen/)  
- Copy this repository into `ptp_ws/src/`

### Build & Source

```bash
cd ptp_ws
colcon build
source install/setup.bash
```

---

## **⚙️ Running**

### Option 1: Terminal Launch

1. Start camera:
   ```bash
   ros2 launch usb_cam demo_launch.py
   ```
2. Connect joystick and configure `robot.py` accordingly  
3. Launch ArUco pose detection and crane control:
   ```bash
   ros2 launch ros2_aruco myrobot_launch.py
   ```

### Option 2: Desktop Shortcut

- Edit `desktop_icon/launch_script/pkg_launch.sh` and `robot.png` paths:
  ```text
  Exec=/home/<user>/ptp_ws/src/ros2_aruco/launch_script/pkg_launch.sh
  Icon=/home/<user>/ptp_ws/src/ros2_aruco/launch_script/robot.png
  ```
- Copy `.desktop` files to your desktop and launch with a click

---

## **📈 Contribution & Future Work**

This is a prototype; planned improvements include:

- IFC/OpenBIM support for target pose extraction  
- Depth-camera integration for 3D accuracy  
- Automated crane control using transform computations  
- Live feedback UI (Dash/Plotly)  
- Digital twin for crane–panel placement  

Feel free to fork, open issues, or submit PRs!

---

## **👥 Authors**

- Yasmin Ragab  
- Radwa Abdelhafez  
- Noureldeen Nagm  

---
