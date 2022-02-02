# Guide to install OpenCV with GPU for python3

## Install OpenCV versi GPU

Navigasi direktori
```
cd ~/ext_pkg
```

Clone repository dari github opencv
```
git clone https://github.com/opencv/opencv opencv
git clone https://github.com/opencv/opencv_contrib opencv_contrib
```

Membuat folder *build*:
```
cd opencv
mkdir build
cd build
```

Memasukkan argumen untuk compile:
ubah CUDA ARCH BIN sesuai GPU yang dipakai
```
cmake -D CMAKE_BUILD_TYPE=RELEASE \
	-D CMAKE_INSTALL_PREFIX=/usr/local \
	-D INSTALL_PYTHON_EXAMPLES=ON \
	-D INSTALL_C_EXAMPLES=OFF \
	-D OPENCV_ENABLE_NONFREE=ON \
	-D WITH_CUDA=ON \
	-D WITH_CUDNN=ON \
	-D OPENCV_DNN_CUDA=ON \
	-D ENABLE_FAST_MATH=1 \
	-D CUDA_FAST_MATH=1 \
	-D CUDA_ARCH_BIN=7.5 \
	-D WITH_CUBLAS=1 \
	-D OPENCV_EXTRA_MODULES_PATH=~/ext_pkg/opencv_contrib/modules \
	-D HAVE_opencv_python3=OFF \
	-D PYTHON_EXECUTABLE=/usr/bin/env/python3 \
	-D BUILD_EXAMPLES=ON ..
```

Compile menggunakan *make*:
```
make -j4
```
(Note: j4 artinya compiler akan menggunakan 4 core cpu)
(Note lagi: Selamat menunggu selama 3 jam wkwkwkwk)

Setelah compile selesai, install opencv tersebut:
```
sudo make install
```
