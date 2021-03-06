# buildOpenCVTX1
Build and install OpenCV for the NVIDIA Jetson TX1

These scripts build OpenCV version 3.3 for the Jetson TX1.

JetPack gives the option of installing OpenCV4Tegra (OpenCV 2.4) with accelerated CPU functions. OpenCV4Tegra is now deprecated. Here is a recipe for building OpenCV from source.

OpenCV is a rich environment which can be configured in many different ways. You should configure OpenCV to fit your needs by modifying the build file "buildOpenCV.sh". Note that selecting different options in OpenCV may also have additional library requirements which are not included in these scripts.

To run the the build file

$ ./buildOpenCV.sh

The build system has been known at times to have issues. It's worth doing a sanity check after the build is complete:

$ cd $HOME/opencv/build

$ make

This should ensure that everything has been built.

After this, you can install the new build:

$ cd $HOME/opencv/build

$ sudo make install

## Notes
There may be issues if have both OpenCV4Tegra and a regular OpenCV build installed at the same time. Most people do not install OpenCV4Tegra on their machine if using the OpenCV build.

The Jetson is an aarch64 machine, which means that the OpenCV configuration variable ENABLE_NEON is ignored. The compiler includes NEON support for all machines with aarch64 architecture.

When running the OpenCV tests, currently several of the tests fail.  

With L4T 28.1, there is an issue with the stock install that does not allow the GStreamer examples to work. (9/4/17). The issue is discussed here: https://devtalk.nvidia.com/default/topic/1019986/jetson-tx1/getting-errors-in-using-onboard-camera-jetpack-3-1-/post/5203796/#5203796

## References

Most of this information is derived from:

http://docs.opencv.org/3.2.0/d6/d15/tutorial_building_tegra_cuda.html

https://devtalk.nvidia.com/default/topic/965134/opencv-3-1-compilation-on-tx1-lets-collect-the-quot-definitive-quot-cmake-settings-/?offset=3

## Release Notes
September 2017
* Initial Release
* L4T 28.1
* OpenCV 3.3

## License
MIT License

Copyright (c) 2017 Jetsonhacks

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
 
