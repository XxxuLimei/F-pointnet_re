# F-pointnet_re  
## 0615:  
1. 下载了F-Pointnet的pytorch版本，进行复现。
2. 首先运行`python kitti/prepare_data.py --demo`命令，可视化了2d和3d的gtbox:
![3D](https://github.com/XxxuLimei/F-pointnet_re/blob/main/doc/tmpd76gnlda.PNG)
![2D](https://github.com/XxxuLimei/F-pointnet_re/blob/main/doc/tmpsr6ja4vc.PNG)
- Note: 这里修改数据集路径是在`kitti/prepare_data.py`文件的117行，将实例化的kitti_object里的`root_dir`修改为kitti数据集路径即可；
