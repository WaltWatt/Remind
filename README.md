# remind

A fork of http://git.roaringpenguin.com/Remind.git

Remind is a full-featured calendar/alarm program.
Copying policy is in the file [COPYRIGHT](COPYRIGHT).

Manual pages are in [man](man).

## Installation

Installation notes for various operating systems are in [docs](docs).
See the appropriate README file for installation on your system.

### Compiling from source

1. Edit the file [src/custom.h](src/custom.h) according to your preferences.
2. Edit the file [src/lang.h](src/lang.h) to choose a language.
3. Run these commands:
    ```
    meson build
    ninja -C build
    sudo ninja -C build install
    ```
    ... or alternatively using autotools:
    ```
    ./configure
    make
    sudo make install
    ```
   You can supply options; type `./configure --help` for details.

See also the original [README file](README) 

## Contact info 
### Remind
Email: dfs@roaringpenguin.com 

Home page: http://www.roaringpenguin.com/remind

### Build __remind__ with meson/ninja (this fork)
Email:       walt@gbyte.co
