Test code for nvv4l2h264enc dynamic FPS change bug

Build Instructions:
mkdir build
cd build
cmake .. -DCMAKE_BUILD_TYPE=<Release|Debug>
make

Run Instructions:
./nvv4l2h264enc-fps-bug [GSTREAMER_OPTIONS]
./nvv4l2h264enc-fps-bug [GSTREAMER_OPTIONS] stop-on-change
The latter option will stop the pipeline before performing the FPS change
