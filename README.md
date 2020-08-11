# Qt Mapbox in Docker

## Preconditions

- Ubuntu 18.04 LTS

- Install docker and docker compose, and add non-root docker user. 
  - https://docs.docker.com/engine/install/ubuntu/
  - https://docs.docker.com/compose/install/
  - https://docs.docker.com/engine/install/linux-postinstall/

- execute the below command to use x11 in docker.

~~~
$ xhost +
~~~


## How to use

- If you'd like to change your work directory, please edit "setenv.sh"

- build container
~~~
$ . setenv.sh
$ docker-compose build
~~~

- start container
~~~
$ . setenv.sh
$ docker-compose up -d
~~~

- enter/re-enter container
~~~
$ docker-compose exec app /bin/bash
~~~

- stop container
~~~
$ docker-compose down
~~~

# build 
~~~
sudo apt-get install qtwayland5
git clone https://github.com/mapbox/mapbox-gl-native.git -b maps-v1.6.0
cd mapbox-gl-native/

edit CMakeList.txt L.20
option(MBGL_WITH_QT "Build Mapbox GL Qt bindings" ON)


export MAPBOX_ACCESS_TOKEN=<xxxxx your token>
mkdir build
cd build/
git submodule update --init --recursive
cmake ..
make
./mbgl-qt -platform wayland
~~~

