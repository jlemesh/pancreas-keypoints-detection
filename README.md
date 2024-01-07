# pancreas-keypoints-detection

## Download the datasets

- [Medical Segmentation Decathlon](http://medicaldecathlon.com/)
- [Pancreas-CT](https://wiki.cancerimagingarchive.net/display/public/pancreas-ct)

## Build OpenCV

```
conda create --name opencv_built
conda activate opencv_built

conda install python=3.9

export CPLUS_INCLUDE_PATH=<conda_env_path>/lib/python3.9

cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D OPENCV_EXTRA_MODULES_PATH=<opencv_path>/opencv_contrib/modules \
    -D PYTHON3_LIBRARY=<conda_env_path>/lib/libpython3.9.dylib \
    -D PYTHON3_INCLUDE_DIR=<conda_env_path>/include/python3.9 \
    -D PYTHON3_EXECUTABLE=<conda_env_path>/bin/python3 \
    -D PYTHON3_PACKAGES_PATH=<conda_env_path>/lib/python3.9/site-packages \
    -D BUILD_opencv_python2=OFF \
    -D BUILD_opencv_python3=ON \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D INSTALL_C_EXAMPLES=OFF \
    -D OPENCV_ENABLE_NONFREE=ON \
    -D BUILD_EXAMPLES=ON ../opencv

make -j4

sudo make install

cd <conda_env_path>/lib/python3.9
ln -s /usr/local/python/cv2 cv2
```

Resources:
 - https://docs.opencv.org/4.x/d0/db2/tutorial_macos_install.html
 - https://jayrobwilliams.com/files/html/OpenCV_Install.html
 - https://pyimagesearch.com/2018/08/17/install-opencv-4-on-macos/
