#!/usr/bin/env python

import rospy

from sensor_msgs.msg import LaserScan

import numpy as np

  

def lidar_callback(msg):

ranges = np.array(msg.ranges) # Convert to NumPy array

angles = np.linspace(msg.angle_min, msg.angle_max, len(ranges)) # Compute angles

  

# Ignore invalid readings and those beyond 4 meters

valid_indices = np.isfinite(ranges) & (ranges <= 4.0)

filtered_ranges = ranges[valid_indices]

filtered_angles = angles[valid_indices]

  

if len(filtered_ranges) == 0:

rospy.logwarn("No obstacles within 4 meters detected.")

return

  

# Step 1: Cluster objects based on distance gaps

threshold = 0.2 # Distance gap threshold for object separation

clusters = []

current_cluster = []

  

for i in range(len(filtered_ranges) - 1):

current_cluster.append((filtered_ranges[i], filtered_angles[i]))

  

if abs(filtered_ranges[i] - filtered_ranges[i + 1]) > threshold:

clusters.append(current_cluster)

current_cluster = []

  

if current_cluster:

clusters.append(current_cluster)

  

# Step 2: Find two largest objects

clusters.sort(key=len, reverse=True)

if len(clusters) < 2:

rospy.logwarn("Less than two objects detected within 4 meters.")

return

  

obj1 = np.array(clusters[0])

obj2 = np.array(clusters[1])

  

# Step 3: Compute distance between object centroids

centroid1 = np.mean(obj1[:, 0]) # Average distance of object 1

centroid2 = np.mean(obj2[:, 0]) # Average distance of object 2

  

angle1 = np.mean(obj1[:, 1]) # Average angle of object 1

angle2 = np.mean(obj2[:, 1]) # Average angle of object 2

  

# Convert to Cartesian coordinates

x1, y1 = centroid1 * np.cos(angle1), centroid1 * np.sin(angle1)

x2, y2 = centroid2 * np.cos(angle2), centroid2 * np.sin(angle2)

  

# Euclidean distance between objects

distance = np.sqrt((x2 - x1) ** 2 + (y2 - y1) ** 2)

rospy.loginfo(f"Distance between objects: {distance:.3f} meters")

  

def lidar_listener():

rospy.init_node('lidar_object_detection', anonymous=True)

rospy.Subscriber('/scan', LaserScan, lidar_callback)

rospy.spin()

  

if __name__ == '__main__':

lidar_listener()



nodo
<launch>

<!-- Inicia el nodo -->

<node pkg="task_system" type="prueba.py" name="prueba" output="screen" launch-prefix="python3" />

</launch>


INSTALE PAQUETES CON GIT CLONE

borrar carpeta rm -r dir