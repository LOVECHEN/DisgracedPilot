**THIS IS EXPERIMENTAL SOFTWARE FOR RESEARCH PURPOSES ONLY. THIS IS NOT A PRODUCT.
YOU ARE RESPONSIBLE FOR COMPLYING WITH LOCAL LAWS AND REGULATIONS.
NO WARRANTY EXPRESSED OR IMPLIED.**

---

The 'DisgracedPilot' Fork
------

This is an experimental OpenPilot build that uses the Accord-Bosch camera system to provide lane detection instead of OpenPilot. It is for research purposes only and absolutely not for use in daily driving. Its purpose is simply to prove that the vehicle can be controlled directly using the Bosch data from the CAN in the path / lane planner, and that the EON may be left in storage during operation. As such, absolutely no user support will be given. **ABUSE OF THIS SOFTWARE MAY RESULT IN INJURY OR DEATH.** 

Instructions:

* Load code onto the EON.
* SSH into the EON and run 'scons' in the ~/openpilot folder. (May take one hour or more.)
* Copy LiveParameters from another fork into the ~/data/params folder.

To do:

* More accurately determine the decoding of the Bosch lane polynomial messages. Particularly need to understand the "LINE_JERK" parameter, as it seems inaccurate or misnamed. Other flags like line colour or slope seem to be present but need to be identified.
* Identify the coordinate frame of the Bosch camera. It may be referenced to the rear axle of the vehicle, instead of the camera centre in OpenPilot. The impact may be minimal, however.
* Investigate model deficiencies, e.g. moving from light into shadow.
* Tune the controls.
* Handle common freeway lane occurrences like lane merging, lane ending.
* Consider new functionality, e.g. using the outer lane tracking to create a lane change assistance model, implementing navigation coasting to pass through intersections or deal with brief lane line dropouts.
* Determine which OpenPilot processes can be disabled and cleanly remove or ignore them.

Please contact me if you are interested in contributing to any of these points.