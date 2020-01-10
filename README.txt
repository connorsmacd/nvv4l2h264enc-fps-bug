Test code for nvv4l2h264enc dynamic FPS change bug

This program will launch a pipeline with a videotestsrc at 15 FPS. Once the
pipeline has started playing, the program will attempt to change the FPS to 30,
optionally stopping the pipeline in between the CAPS change. There is a filesink
that will trigger an EOS once it has received 150 buffers, so the program
should eventually exit gracefully if everything is working.

Currently, if the FPS is changed dynamically without stopping the pipeline, the
encoder will halt processing. Running with the "stop-on-change" option will
demonstrate that the pipeline can't even be stopped before performing he CAPS
change.

Build Instructions:
mkdir build
cd build
cmake .. -DCMAKE_BUILD_TYPE=<Release|Debug>
make

Run Instructions:
./nvv4l2h264enc-fps-bug [GSTREAMER_OPTIONS]
./nvv4l2h264enc-fps-bug [GSTREAMER_OPTIONS] stop-on-change
The latter option will stop the pipeline before performing the FPS change
