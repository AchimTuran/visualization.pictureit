PictureIt - Kodi Visualization
==============================

PictureIt is supposed to make listening to music more elegant and less flashy.<br>
The idea is to take random images YOU selected and display them alongside a simple spectrum at the bottom.<br>
Simple right?

![Screenshot-1](http://i.imgur.com/XTlrbGS.png "Screenshot 1")

## Features
 * Select a local directory containing your images (If sub-folders are present, those will be used as "Preset")
 * Update images by interval
 * Update images on new track
 * Change the transition time
 * Enable/Disable the spectrum
 * Enable/Disable a settle spectrum-background
 * Change the spectrums: Width, Bottom-Padding, Animation-Speed

## Installation
 1. Install SOIL on your system
      * Ubuntu:   `apt-get install libsoil1`
      * Arch:     `pacaur -S soil`
 2. Install the [linuxwhatelse repository](http://linuxwhatelse.de/projects/kodi/repo/repository.linuxwhatelse.zip)
 3. Install PictureIt
 4. In the add-on configuration set the path to a directory holding your images/wallpapers
 5. Done!

## Build
 1. Install SOIL development package on your system
      * Ubuntu:   `apt-get install libsoil-dev`
      * Arch:     `pacaur -S soil-dev`?(Please confirm that)
 2. Clone the Kodi Github repository with:
      * `cd <your-source-path>`
      * `git clone https://github.com/xbmc/xbmc.git`
 3. Clone PictureIt repository 
      * `cd <your-source-path>`
      * `git clone https://github.com/linuxwhatelse/visualization.pictureit.git`
 4. Create directories
      * `mkdir <your-source-path>/visualization.pictureit/build`
      * `mkdir <your-source-path>/kodi-binary-addons`
      * `cd /home/user/sources/visualization.pictureit/build`
 5. Configure the build process with CMake
      * `cmake -DADDONS_TO_BUILD=visualization.pictureit -DADDON_SRC_PREFIX=<your-source-path> -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=<your-source-path>/kodi-binary-addons -DPACKAGE_ZIP=1 <your-source-path>/kodi/project/cmake/addons`
 6. Build the PictureIt add-on
     * `make -C <your-source-path>/visualization.pictureit/build`
