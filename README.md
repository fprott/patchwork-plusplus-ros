# patchwork-plusplus-ros

This is ROS package of Patchwork++ (@ IROS'22), which is a fast and robust ground segmentation method.

<p align="center"><img src=pictures/patchwork++.gif alt="animated" /></p>

> If you are not familiar with ROS, please visit the [original repository][patchwork++link].

> If you follow the [repository][patchwork++link], you can run Patchwork++ in Python and C++ easily.

[patchwork++link]: https://github.com/url-kaist/patchwork-plusplus

## :open_file_folder: What's in this repository

* ROS based Patchwork source code ([patchworkpp.hpp][codelink])
* Demo launch file ([demo.launch][launchlink]) with sample rosbag file. You can execute Patchwork++ simply!

[codelink]: https://github.com/url-kaist/patchwork-plusplus-ros/blob/master/include/patchworkpp/patchworkpp.hpp
[launchlink]: https://github.com/url-kaist/patchwork-plusplus-ros/blob/master/launch/demo.launch

## :package: Prerequisite packages
You may need to install ROS, PCL, Eigen, ...

## :gear: How to build Patchwork++
To build Patchwork++, you can follow below codes.

```bash
$ mkdir -p ~/ros2_ws/src
$ cd ~/ros2_ws
$ colcon build --packages-select patchworkpp --symlink-install
```

## :runner: To run the demo codes
There is a demo which executes Patchwork++ but there is **no** sample rosbag file for ROS 2. You can download a the raw data set and use a converter.

You will find the [raw data set here](https://www.cvlibs.net/datasets/kitti/raw_data.php) (use the synced+rectified data, you may need the calibration deppending on your use case).

Now we need to [use a converter](https://github.com/tomas789/kitti2bag) to create the ROS 2 bag. 

The convert will output the lidar data by default under the topic ```/kitti/velo``` using the frame ```velo_link```. Change the ```demo.launch.py``` file accordingly. 

Then, you can run demo as follows.
```bash
# Start Patchwork++ (make sure to adjust demo.launch.py to fit with your bag)
$ ros2 launch patchworkpp demo.launch.py
# Start the bag file (change the name to fit the file you downloaded)
$ ros2 bag play kitti_00_sample.db3
```

## :pushpin: TODO List
- [ ] Update additional demo codes processing data with .bin file format
- [ ] Generalize point type in the source code
- [ ] Add visualization result of demo codes in readme

## Citation
If you use our codes, please cite our [paper][patchwork++arXivLink].

In addition, you can also check the paper of our baseline(Patchwork) [here][patchworkarXivlink].

[patchwork++arXivLink]: https://arxiv.org/abs/2207.11919
[patchworkarXivlink]: https://arxiv.org/abs/2108.05560

```
@inproceedings{lee2022patchworkpp,
    title={{Patchwork++: Fast and robust ground segmentation solving partial under-segmentation using 3D point cloud}},
    author={Lee, Seungjae and Lim, Hyungtae and Myung, Hyun},
    booktitle={Proc. IEEE/RSJ Int. Conf. Intell. Robots Syst.},
    year={2022},
    note={{Submitted}} 
}
```
```
@article{lim2021patchwork,
    title={Patchwork: Concentric Zone-based Region-wise Ground Segmentation with Ground Likelihood Estimation Using a 3D LiDAR Sensor},
    author={Lim, Hyungtae and Minho, Oh and Myung, Hyun},
    journal={IEEE Robotics and Automation Letters},
    year={2021}
}
```

## :postbox: Contact
If you have any question, don't be hesitate let us know!

* [Seungjae Lee][sjlink] :envelope: (sj98lee at kaist.ac.kr)
* [Hyungtae Lim][htlink] :envelope: (shapelim at kaist.ac.kr)

[sjlink]: https://github.com/seungjae24
[htlink]: https://github.com/LimHyungTae

