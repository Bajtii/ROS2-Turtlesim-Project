# 🐢 TurtleSim Catch Them All

![IMG_1290](https://github.com/user-attachments/assets/78f01164-34d1-44a0-aed3-2fdcf2c4e20c)


This project implements an **interactive simulation game** using ROS 2 and `turtlesim`. The main turtle (`turtle1`) automatically searches for and “catches” randomly spawned turtles on the screen, demonstrating ROS 2 concepts like subscription, publishing, and service calls.

> 🚀 This system is designed for learning basic mobile robot control in ROS 2 and working with custom messages and services.

---

## 🎯 Project Goals

- ✅ Randomly spawn new turtles in the `turtlesim` environment  
- ✅ Publish a list of alive turtles (their positions and names)  
- ✅ Automatically control the main turtle to pursue and “catch” others  
- ✅ Call a service to remove caught turtles from the simulation  
- ✅ Configurable behavior (catch the closest turtle first or the first one in the list)

---

## 🧠 How It Works

The project consists of two ROS 2 nodes:

### 🐢 `turtle_spawner`

- Periodically spawns new turtles at random positions and orientations  
- Publishes the current list of alive turtles on the `alive_turtles` topic  
- Provides a `catch_turtle` service to remove turtles by name  

### 🐢 `turtle_controller`

- Subscribes to the main turtle’s pose and the alive turtles list  
- Selects a target turtle to catch (closest or first in the list)  
- Commands `turtle1` to move toward the target turtle  
- Calls the service to remove the turtle upon reaching it  


## ⚙️ Requirements

- ROS 2 (e.g., Foxy, Galactic, or newer)  
- The `turtlesim` package  
- Custom message package `my_robot_interfaces` with `Turtle`, `TurtleArray` messages and `CatchTurtle` service  
- Python 3

## 🔧 Parameters

| Node                | Parameter                    | Type   | Default  | Description                                                     |
| ------------------- | ---------------------------- | ------ | -------- | --------------------------------------------------------------- |
| `turtle_controller` | `catch_closest_turtle_first` | bool   | true     | Catch the closest turtle first instead of the first in the list |
| `turtle_spawner`    | `turtle_name_prefix`         | string | "turtle" | Prefix for the names of newly spawned turtles                   |
| `turtle_spawner`    | `spawn_frequency`            | float  | 1.0      | Frequency at which new turtles spawn (Hz)                       |

