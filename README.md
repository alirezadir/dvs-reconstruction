# DVS Denoising
This repository provides software to our publication "Real-Time Intensity-Image Reconstruction for Event Cameras Using Manifold Regularisation", BMVC 2016.

If you use this code please cite the following publication:
~~~
@inproceedings{reinbacher_bmvc2016,
  author = {Christian Reinbacher and Gottfried Graber and Thomas Pock},
  title = {{Real-Time Intensity-Image Reconstruction for Event Cameras Using Manifold Regularisation}},
  booktitle = {2016 British Machine Vision Conference (BMVC)},
  year = {2016},
}
~~~

## Compiling
To compile this code, make sure you first install ImageUtilities with the `iugui`, `iuio` and `iumath` module. Furthermore, this software requires:
 - GCC >= 4.9
 - CMake >= 3.2
 - Qt >= 5.6
 - Boost (program_options, filesystem, system)
 - libcaer >=2.0 (https://github.com/inilabs/libcaer)
 - DVS128 or DAVIS240 camera (can also load events from files)

 To compile the GUI and command-line utility:
 ~~~
mkdir build
cd build
cmake ..
make -j6
 ~~~

 Per default, the application will compile to support the iniLabs DVS128. If you want to attach a DAVIS240 instead, uncomment L23 in `denoisingmainwindow.h` and re-compile.

## Usage
Launch `live_reconstruction_gui` to get to the main application which should look like this:
<img src="https://github.com/VLOGroup/dvs-denoising/raw/master/images/screenshot.png"></img>
Clicking on the play button with an attached camera will start the live reconstruction method. Alternatively, events can be loaded from text files with one event per line:
~~~
<timestamp in seconds> <x> <y> <polarity (-1/1)>
...
...
~~~
