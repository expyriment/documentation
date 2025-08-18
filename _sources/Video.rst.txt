Presenting videos in Expyriment
===============================

Video formats
-------------
Expyriment uses FFmpeg (https://www.ffmpeg.org) to decode video files. This means that a large variety of video formats are automatically supported.

Usage
-----

1. Create a video object::

    my_video = expyriment.stimuli.Video("filename")

2. Preload the video into memory, before playing it back::

    my_video.preload()

3. To actually present the video on screen, understanding the various methods of the video object is crucial:

   ``play()``
       simply starts video (and audio) playback in the background. This has no effect on the screen, no frames from the video are presented automatically.

   ``present()``
        starts video (and audio) playback (if not started yet) and waits for a new frame, then presents this frame on the screen. The method blocks until the new frame has been presented on the screen (if in OpenGL mode).

   ``update()``
        presents the currently available frame immediately (i.e. without waiting for a new one). The methods blocks until the currently available frame has been presented on the screen (if in OpenGL mode).

   ``wait_end()``
        continuously presents frames until the last frame of the video is reached. Dropped frames will be reported (in the terminal as well as in the event file). The keyboard is monitored during this, such that hitting ESC will pause playback, and then choosing "n" will resume it (while choosing "y" will quit of course).

   ``wait_frame()``
        behaves like ``wait_end()``, with the difference that it waits until frame number `frame` instead of the last frame.

   `wait_time()``
        behaves like ``wait_frame()``, with the difference that it waits until a certain time instead of a frame number.


   The perhaps most common situation is thus to use a combination of ``present()`` and ``wait_end()``.


Example
-------

Simple example::

    import expyriment as xpy

    exp = xpy.control.initialize()
    v = xpy.stimuli.Video("file.mp4")
    v.preload()

    v.present()
    video_presentation_time = exp.clock.time
    v.wait_end()
    v.stop()


If key presses (other than the control keys) need to be checked during the video playback::

    import expyriment as xpy

    exp = xpy.control.initialize()
    v = xpy.stimuli.Video("file.mpg")
    v.preload()

    v.play()
    v.present()
    video_presentation_time = exp.clock.time
    while v.is_playing:
        if v.new_frame_available:
            video.update()
        else:
            key = exp.keyboard.check()
            if key is not None:
                key_pressed = True
    v.stop()
    
**NOTE**: Be aware that infering reaction times from this might not be fully accurate, due to multiple threads running in the background to enable video frame updating and audio playback.
