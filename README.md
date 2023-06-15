# F-pointnet_re  
## 0615:  
1. 下载了F-Pointnet的pytorch版本，进行复现。
2. 首先运行`python kitti/prepare_data.py --demo`命令，获得了一系列可视化结果：  
- 可视化了2d和3d的gtbox（设置`show_images`参数为True）:  
![3D](https://github.com/XxxuLimei/F-pointnet_re/blob/main/doc/tmpd76gnlda.PNG)
![2D](https://github.com/XxxuLimei/F-pointnet_re/blob/main/doc/tmpsr6ja4vc.PNG)
- **Note**: 这里修改数据集路径是在`kitti/prepare_data.py`文件的117行，将实例化的kitti_object里的`root_dir`修改为kitti数据集路径即可；
打印的信息如下：
```
Type, truncation, occlusion, alpha: Pedestrian, 0, 0, -0.200000
2d bbox (x0,y0,x1,y1): 712.400000, 143.000000, 810.730000, 307.920000
3d bbox h,w,l: 1.890000, 0.480000, 1.200000
3d bbox location, ry: (1.840000, 1.470000, 8.410000), 0.010000
frustum_angle: -1.3547251976663919
('Image shape: ', (370, 1224, 3))
 -------- 2D/3D bounding boxes in images --------
```  
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
![](https://github.com/XxxuLimei/F-pointnet_re/blob/main/doc/lidar_2d.PNG)  
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
- 仅将位于Gtbox内的Lidar点可视化（设置`show_lidar_box`参数为True）:
![](https://github.com/XxxuLimei/F-pointnet_re/blob/main/doc/gtbox_lidar.png)  
打印的信息如下：  
```
Type, truncation, occlusion, alpha: Pedestrian, 0, 0, -0.200000
2d bbox (x0,y0,x1,y1): 712.400000, 143.000000, 810.730000, 307.920000
3d bbox h,w,l: 1.890000, 0.480000, 1.200000
3d bbox location, ry: (1.840000, 1.470000, 8.410000), 0.010000
frustum_angle: -1.3547251976663919
('Image shape: ', (370, 1224, 3))
 -------- LiDAR points in a 3D bounding box --------
('Number of points in 3d box: ', 376)
```  
- 对Lidar点云进行可视化（设置`show_project`参数为True）:  
![](https://github.com/XxxuLimei/F-pointnet_re/blob/main/doc/project.png)    
打印的信息如下：
```
Type, truncation, occlusion, alpha: Pedestrian, 0, 0, -0.200000
2d bbox (x0,y0,x1,y1): 712.400000, 143.000000, 810.730000, 307.920000
3d bbox h,w,l: 1.890000, 0.480000, 1.200000
3d bbox location, ry: (1.840000, 1.470000, 8.410000), 0.010000
frustum_angle: -1.3547251976663919
('Image shape: ', (370, 1224, 3))
 -------- LiDAR points in a frustum from a 2D box --------
[[1.8324e+01 4.9000e-02 8.2900e-01]
 [1.8344e+01 1.0600e-01 8.2900e-01]
 [5.1299e+01 5.0500e-01 1.9440e+00]
 [1.8317e+01 2.2100e-01 8.2900e-01]
 [1.8352e+01 2.5100e-01 8.3000e-01]
 [1.5005e+01 2.9400e-01 7.1700e-01]
 [1.4954e+01 3.4000e-01 7.1500e-01]
 [1.5179e+01 3.9400e-01 7.2300e-01]
 [1.8312e+01 5.3800e-01 8.2900e-01]
 [1.8300e+01 5.9500e-01 8.2800e-01]
 [1.8305e+01 6.2400e-01 8.2800e-01]
 [1.8305e+01 6.8200e-01 8.2900e-01]
 [1.8307e+01 7.3900e-01 8.2900e-01]
 [1.8301e+01 7.9700e-01 8.2900e-01]
 [1.8300e+01 8.5400e-01 8.2900e-01]
 [1.8287e+01 9.1100e-01 8.2800e-01]
 [1.8288e+01 9.6900e-01 8.2800e-01]
 [1.8307e+01 9.9900e-01 8.2900e-01]
 [1.8276e+01 1.0540e+00 8.2800e-01]
 [2.1017e+01 1.3490e+00 9.2100e-01]]
[[18.32401052  0.05322839  0.83005286]
 [18.34401095  0.11021263  0.83005313]
 [51.29900945  0.50918573  1.94510349]
 [18.31701048  0.22518075  0.83005276]
 [18.35201031  0.25517254  0.83105295]
 [15.00501117  0.29814455  0.71803507]
 [14.95401151  0.34412858  0.71603479]
 [15.17901091  0.39811201  0.72403614]
 [18.31201118  0.5420929   0.83005269]
 [18.30001012  0.59907705  0.82905281]
 [18.30501118  0.62806903  0.82905288]
 [18.30501115  0.68605293  0.83005259]
 [18.30701003  0.74303719  0.83005261]
 [18.30101139  0.80102102  0.83005253]
 [18.30001001  0.85800518  0.83005251]
 [18.28701141  0.91498924  0.82905263]
 [18.28801083  0.97297313  0.82905264]
 [18.30700992  1.00296512  0.83005261]
 [18.27600976  1.0579494   0.82905247]
 [21.01701075  1.35291567  0.92206282]]
```  
- 将一个frustum里的点云进行可视化（设置`show_lidar_frustum`参数为True）:
![](https://github.com/XxxuLimei/F-pointnet_re/blob/main/doc/frustum.png)  
打印的信息如下：
```
Type, truncation, occlusion, alpha: Pedestrian, 0, 0, -0.200000
2d bbox (x0,y0,x1,y1): 712.400000, 143.000000, 810.730000, 307.920000
3d bbox h,w,l: 1.890000, 0.480000, 1.200000
3d bbox location, ry: (1.840000, 1.470000, 8.410000), 0.010000
frustum_angle: -1.3547251976663919
('Image shape: ', (370, 1224, 3))
 -------- LiDAR points in a frustum from a 2D box --------
('2d box FOV point num: ', 1483)
```  

