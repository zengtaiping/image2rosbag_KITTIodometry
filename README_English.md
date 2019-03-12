image2rosbag_KITTIodometry
======
We convert KITTI datasets to a rosbag file in Python. Only grayscale datasets have been tested. Detail information can be found in
http://git.oschina.net/taiping.z.git/image2rosbag_KITTIodometry If you don't speak English, please [click here](./README_Chinese.md).


### 1. Download KITTI datasets[odometry dataset (grayscale, 22GB)](http://www.cvlibs.net/datasets/kitti/eval_odometry.php), and then unzip

### 2. Set path image files, rosbag name, times, and then run
```
python img2bag_kitti_odo.py /your directory/KITTI/dataset/sequences/00/image_0 kitti_00_l.bag /your directory/KITTI/dataset/sequences/00/times.txt
```
### 3. Check rosbag
**Check rosbag**
```
rosbag info image_0 kitti_00_l.bag
--------
path:        kitti_00_l.bag
version:     2.0
duration:    7:50s (470s)
start:       Jan 01 1970 08:00:00.00 (0.00)
end:         Jan 01 1970 08:07:50.58 (470.58)
size:        2.0 GB
messages:    4541
compression: none [2271/2271 chunks]
types:       sensor_msgs/Image [060021388200f6f0f447d0fcd9c64743]
topics:      camera/image_raw   4541 msgs    : sensor_msgs/Image
```
**Test on ORBSLAM2**
```
rosbag play --pause kitti_00_l.bag
rosrun ORB_SLAM2 Mono Vocabulary/ORBvoc.txt Examples/Monocular/KITTI00-02.yaml 
```
Note that we have set rostopic as ```camera/image_raw```.

