```
#!/usr/bin/env python

import rospy
from sensor_msgs.msg import LaserScan, PointCloud2, PointField
import sensor_msgs.point_cloud2 as pc2
import numpy as np

# Publisher Global
pub = None

def lidar_callback(msg):
    global pub

    # Leer los datos
    ranges = np.array(msg.ranges) 
    angles = np.linspace(msg.angle_min, msg.angle_max, len(ranges)) 
    # Filtrar los datos
    valid_indices = np.isfinite(ranges) & (ranges <= 1.5)
    filtered_ranges = ranges[valid_indices]
    filtered_angles = angles[valid_indices]
    # Convertir los datos a cartesianos
    x = filtered_ranges * np.cos(filtered_angles)
    y = filtered_ranges * np.sin(filtered_angles)
    # Colocarlos en formato columnas
    points = np.column_stack((x, y, np.zeros_like(x)))

    # Definir los campos
    fields = [
        PointField(name="x", offset=0, datatype=PointField.FLOAT32, count=1),
        PointField(name="y", offset=4, datatype=PointField.FLOAT32, count=1),
        PointField(name="z", offset=8, datatype=PointField.FLOAT32, count=1)
    ]

    # Crear mensaje
    cloud_msg = pc2.create_cloud(msg.header, fields, points)
    # Publicar Mensaje
    pub.publish(cloud_msg)
    
    #print(filtered_ranges.shape)
    #print(filtered_angles.shape)
    #print(" --------------------------------------------- ")

def lidar_listener():
    global pub
    rospy.init_node('lidar_deteciton', anonymous=True)
    # Crear Publisher
    pub = rospy.Publisher('/filtered_scan', PointCloud2, queue_size=1)
    rospy.Subscriber('/scan', LaserScan, lidar_callback)
    rospy.spin()

if __name__ == '__main__':
    lidar_listener()
```