Test suite
==========

The Expyriment test suite is a guided tool for testing your computer's 
abilities and performance. This includes timing accuracy of visual stimulus
presentation, audio playback functionality, mouse functionality and
serial/parallel port functionality.

Eventually, all test results can be saved as a protocol, together with some 
information about the system.

.. image:: test_suite.png

Usage
-----
Starting the test suite
~~~~~~~~~~~~~~~~~~~~~~~
The test suite can either be started from within an experiment, or from an 
interactive Python session (for instance with IPython). To start the test 
suite, just call::

    import expyriment
    expyriment.control.run_test_suite()

Alternatively, you can start the test suite from the command line using the 
:doc:`Command line interface <CommandLineInterface>`::

   $ expyriment.cli -T 

**Please note that all changes to the** :doc:`Defaults` **prior to starting the
test suite apply!**

Menu overview
~~~~~~~~~~~~~
Here is a brief explanation of the available options:

1. **Visual stimulus presentation**

 * Tests the visual stimulus presentation timing specifics of the system.

   The following results will be reported:

    * **Estimated Screen Refresh Rate**: The refresh rate of the screen in Hz
      and the approximated time of a single refresh in milliseconds. The most
      common refresh rates are 60 Hz, 75 Hz, 120 Hz, 144 Hz and 240 Hz (marked
      green), but specialised displays might also have refresh rates between 50
      and 360 Hz (marked orange). Reported refresh rates outside of this range
      (marged red) are most likely erroneous.

    * **Detected Framebuffer Pages**: The amount of buffers used for drawing to
      the screen; if only one buffer is used, new stimuli will be drawn directly
      to the screen. If two buffers (double buffer) are used, new stimuli will
      be drawn to an additional page, and a screen update will replace the
      screen with this page and put the screen contents into the page (i.e. the
      two buffers are swapped). If three buffers (triple buffer) are used, new
      stimuli will be drawn to a third page, and a screen update will replace
      the screen with this page, and put the screen contents into the second
      page (i.e. a history of 2 former screens is kept). Only when 2 buffers are
      uses (marked green) blocking on the vertical retrace can function properly
      and lead to accurate presentation time reports.

    * **Average Reporting Inaccuracy**: The average time in milliseconds between
      Expyriment reporting that the stimulus has been presented (i.e. the
      ``present()`` method returns) and the actual time the stimulus could
      actually been physically shown on the screen, given the refresh rate. An
      inaccuracy of 0 ms (marked green) will indicate that blocking on the
      vertical retrace functions properly. An inaccuracy between 1 ms and 1/4th
      of the length of a single refresh cycle (e.g. ~4 ms for a refresh rate of
      60 Hz, marked orange) could indicate a problem with blocking on the
      vertical retrace (e.g. due to the presence of a compositor and/or adaptive
      v-sync mechanism) and requires further measurements by the researcher
      (e.g. with a photodiode) to assess timing accuracy. A delay of more than a
      single refresh cycle (e.g. ~4 ms for a refresh rate of 60 Hz, marked red)
      will indicate that blocking on the vertical retrace does not function
      properly and lead to inaccurate presentation time reports.

    * **Unexplained Presentation Delays**: The amount in percent of
      presentations that will take longer (or shorter) than a single refresh
      cycle. It encompasses of two different types of delays:
    
      * *Accurately Reported*: Presentations delayed by one or more full refresh
        cycles. While these presentations appear later than intended, the time
        they are displayed on screen should be accurately reported. It is not
        uncommon to see up to 5% of presentations delayed in this manner (marked
        green). For delays exceeding this threshold (marked orange), the
        researcher must determine whether the delay is acceptable.

      * *Inaccurately Reported*: Presentations delayed by amounts that do not
        correspond to full refresh cycles. If blocking on the vertical retrace
        functions correctly, such delays should not occur and are likely
        reported incorrectly. A very low percentage of these delays (up to 1%,
        marked green) is acceptable and may indicate rounding errors. Higher
        percentages (up to 10%, marked orange) could suggest issues with
        blocking on the vertical retrace (e.g., due to the presence of a
        compositor and/or adaptive v-sync mechanism) and require further
        measurements by the researcher (e.g., using a photodiode) to assess
        timing accuracy. Percentages exceeding this range (marked red) indicate
        a high likelihood that presentation timing reporting is inaccurate.

    * A histogram showing the obtained presentation timings

2. **Auditory stimulus presentation**

  * Tests functionality of audio playback

3. **Font viewer**

 * Test installed fonts

4. **Mouse test**

 * Tests mouse accuracy (polling time)
 * Tests functionality of mouse buttons

5. **Parallel Port test**

 * Tests functionality of devices connected via the parallel port

6. **Serial port test**

 * Tests functionality of devices connected via the serial port

7. **Write protocol**

 * Saves all test results, as well as information about the system, as a text 
   file.

8. **Quit**

 * Quits the test suite

