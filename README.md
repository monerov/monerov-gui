# MoneroV GUI 

Copyright (c) 2018, The MoneroV Project

Copyright (c) 2014-2018, The Monero Project


This is the GUI for the [core MoneroV project](https://github.com/monerov/monerov). It is an open source project that is completely free to use without restrictions, except for those specified in the license agreement below. There are no restrictions on anyone creating an alternative implementation of MoneroV.

![alt text](https://i.imgur.com/V1fv2sQ.png)

## Development resources

- Website: [monerov.org](https://monerov.org)
- Github: [https://github.com/monerov/monerov-gui](https://github.com/monerov/monerov-gui)
- Mail: [team at monerov.org](mailto:team@monerov.org)


## Supporting the MoneroV project

MoneroV GUI and all its dependencies is 100% open sourced. Everyone can join by making pull requests to this project repository or by making transaltions.


## License

See [LICENSE](LICENSE).

## Compiling the MoneroV GUI from source

### On Linux:

(Tested on Ubuntu 16.04 x86)

1. Install MoneroV dependencies

  - For Ubuntu and Mint

	`sudo apt install build-essential cmake libboost-all-dev miniupnpc libunbound-dev graphviz doxygen libunwind8-dev pkg-config libssl-dev libzmq3-dev`

  - For Gentoo

	`sudo emerge app-arch/xz-utils app-doc/doxygen dev-cpp/gtest dev-libs/boost dev-libs/expat dev-libs/openssl dev-util/cmake media-gfx/graphviz net-dns/unbound net-libs/ldns net-libs/miniupnpc net-libs/zeromq sys-libs/libunwind`

2. Grab an up-to-date copy of the monerov-gui repository

	`git clone --recursive https://github.com/monerov/monerov-gui.git`

3. Go into the repository

	`cd monerov-gui`

4. Install the GUI dependencies

  - For Ubuntu 16.04 x86

	`sudo apt install qtbase5-dev qt5-default qtdeclarative5-dev qml-module-qtquick-controls qml-module-qtquick-controls2 qml-module-qt-labs-folderlistmodel qml-module-qtquick-xmllistmodel qttools5-dev-tools qml-module-qtquick-dialogs`

  - For Ubuntu 16.04+ x64

    `sudo apt install qtbase5-dev qt5-default qtdeclarative5-dev qml-module-qtquick-controls qml-module-qtquick-xmllistmodel qttools5-dev-tools qml-module-qtquick-dialogs qml-module-qt-labs-settings libqt5qml-graphicaleffects`

  - For Linux Mint 18 "Sarah" - Cinnamon x64

    `sudo apt install qml-module-qt-labs-settings qml-module-qtgraphicaleffects`

  - For Gentoo

    `sudo emerge dev-qt/qtcore:5 dev-qt/qtdeclarative:5 dev-qt/qtquickcontrols:5 dev-qt/qtquickcontrols2:5 dev-qt/qtgraphicaleffects:5`

  - Optional : To build the flag `WITH_SCANNER`

    - For Ubuntu and Mint

      `sudo apt install qtmultimedia5-dev qml-module-qtmultimedia libzbar-dev`

    - For Gentoo

      The *qml* USE flag must be enabled.

      `emerge dev-qt/qtmultimedia:5 media-gfx/zbar`

5. Build the GUI

  - For Ubuntu and Mint

	`./build.sh`

  - For Gentoo

    `QT_SELECT=5 ./build.sh`

The executable can be found in the build/release/bin folder.

### On OS X:

1. Install Xcode from AppStore

2. Install [homebrew](http://brew.sh/)

3. Install [monerov](https://github.com/monerov/monerov) dependencies:

  `brew install boost --c++11`

  `brew install openssl` - to install openssl headers

  `brew install pkgconfig`

  `brew install cmake`

  `brew install zeromq`

  *Note*: If cmake can not find zmq.hpp file on OS X, installing `zmq.hpp` from https://github.com/zeromq/cppzmq to `/usr/local/include` should fix that error.

4. Install Qt:

  `brew install qt5`  (or download QT 5.8+ from [qt.io](https://www.qt.io/download-open-source/))

  If you have an older version of Qt installed via homebrew, you can force it to use 5.x like so:
  
  `brew link --force --overwrite qt5`

5. Add the Qt bin directory to your path

    Example: `export PATH=$PATH:$HOME/Qt/5.8/clang_64/bin`

    This is the directory where Qt 5.x is installed on **your** system

6. Grab an up-to-date copy of the monerov-gui repository

  `git clone https://github.com/monerov/monerov-gui.git`

7. Go into the repository

  `cd monerov-gui`

8. Start the build

  `./build.sh`

The executable can be found in the `build/release/bin` folder.

**Note:** Workaround for "ERROR: Xcode not set up properly"

Edit `$HOME/Qt/5.8/clang_64/mkspecs/features/mac/default_pre.prf`

replace
`isEmpty($$list($$system("/usr/bin/xcrun -find xcrun 2>/dev/null")))`

with
`isEmpty($$list($$system("/usr/bin/xcrun -find xcodebuild 2>/dev/null")))`

More info: http://stackoverflow.com/a/35098040/1683164


### On Windows:

1. Install [MSYS2](https://www.msys2.org/), follow the instructions on that page on how to update packages to the latest versions

2. Install MoneroV dependencies as described in [monerov documentation](https://github.com/monerov/monerov) into the MSYS2 environment (using the MSYS2 MinGW 64-bit shell)
   **As we only build the application for Windows 64-bit, install only dependencies for 64-bit architecture (x86_64 in package name)**
   ```
   pacman -S mingw-w64-x86_64-toolchain make mingw-w64-x86_64-cmake mingw-w64-x86_64-boost mingw-w64-x86_64-openssl mingw-w64-x86_64-zeromq mingw-w64-x86_64-libsodium

   ```

3. Install git into MSYS2 environment

    ```
    pacman -S git
    ```

4. Install Qt5 into the MSYS2 enviroment

    ```
    pacman -S mingw-w64-x86_64-qt5
    ```

5. Clone repository

    ```
    git clone https://github.com/monerov/monerov-gui.git
    ```

6. Build the GUI
    ```
    cd monerov-gui
    ./build.sh
    cd build
    make deploy
    ```

The executable can be found in the ```.\release\bin``` directory.
Depending on your machine's graphics card, you might need to ```export QT_QUICK_BACKEND="software"``` from inside the MSYS2 MinGW 64-bit shell to get the application started.

## Known issues

Please refer to the open issues tab to see open and closed known issues.
