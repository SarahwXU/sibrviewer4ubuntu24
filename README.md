# SIBR Viewers for ubuntu24.04

Only tested for local viewer!
### environment
```
python 3.10.18
torch  2.6.0+cu126
gcc    13.3.0
```

### install
```
sudo apt install -y libglew-dev libassimp-dev libboost-all-dev libgtk-3-dev libopencv-dev libglfw3-dev libavdevice-dev libavcodec-dev libeigen3-dev libxxf86vm-dev libembree-dev
# Project setup
cd SIBR_viewers
cmake -Bbuild . -DCMAKE_BUILD_TYPE=Release # add -G Ninja to build faster
cmake --build build -j24 --target install
```
if cmake has error, 
extlibs/CudaRasterizer/CudaRasterizer/cuda_rasterizer/rasterizer_impl.h, has to add
```
#include <cstdint>
```

Most code coming from https://github.com/graphdeco-inria/gaussian-splatting/issues/923#issue-2447623144. However, on ubuntu24.04, the export video cannot be used. Thus, I further modified src/core/video/FFmpegVideoEncoder.cpp. The patch file is [sibr_diff.patch](https://github.com/SarahwXU/sibrviewer4ubuntu24/blob/948ef34cd8c407a87fbc007bd1b7b29238001f54/sibr_diff.patch).

```
git apply sibr_diff.patch
```



