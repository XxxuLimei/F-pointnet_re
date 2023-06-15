# F-pointnet_re  
## 0615:  
1. 下载了F-Pointnet的pytorch版本，进行复现。
2. 首先运行`python kitti/prepare_data.py --demo`命令，获得了一系列可视化结果：  
- 可视化了2d和3d的gtbox（设置`show_images`参数为True）:  
![3D](https://github.com/XxxuLimei/F-pointnet_re/blob/main/doc/tmpd76gnlda.PNG)
![2D](https://github.com/XxxuLimei/F-pointnet_re/blob/main/doc/tmpsr6ja4vc.PNG)
- **Note**: 这里修改数据集路径是在`kitti/prepare_data.py`文件的117行，将实例化的kitti_object里的`root_dir`修改为kitti数据集路径即可；
- 可视化了Lidar下的Gtbox（设置`show_lidar`参数为True）:  
![](https://github.com/XxxuLimei/F-pointnet_re/blob/main/doc/lidar.png)  
打印的信息如下：
```
Type, truncation, occlusion, alpha: Pedestrian, 0, 0, -0.200000
2d bbox (x0,y0,x1,y1): 712.400000, 143.000000, 810.730000, 307.920000
3d bbox h,w,l: 1.890000, 0.480000, 1.200000
3d bbox location, ry: (1.840000, 1.470000, 8.410000), 0.010000
frustum_angle: -1.3547251976663919
('Image shape: ', (370, 1224, 3))
 -------- LiDAR points and 3D boxes in velodyne coordinate --------
('All point num: ', 115384)
('FOV point num: ', 20285)
```  
- 将Lidar点投影到图像上（设置`show_lidar_2d`参数为True）:
![]()  
打印的信息如下：
```
Type, truncation, occlusion, alpha: Pedestrian, 0, 0, -0.200000
2d bbox (x0,y0,x1,y1): 712.400000, 143.000000, 810.730000, 307.920000
3d bbox h,w,l: 1.890000, 0.480000, 1.200000
3d bbox location, ry: (1.840000, 1.470000, 8.410000), 0.010000
frustum_angle: -1.3547251976663919
('Image shape: ', (370, 1224, 3))
 -------- LiDAR points projected to image plane --------
get_lidar_in_image_fov cost 7.70 ms
```  
