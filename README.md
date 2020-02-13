**THIS IS EXPERIMENTAL SOFTWARE FOR RESEARCH PURPOSES ONLY. THIS IS NOT A PRODUCT.
YOU ARE RESPONSIBLE FOR COMPLYING WITH LOCAL LAWS AND REGULATIONS.
NO WARRANTY EXPRESSED OR IMPLIED.**

---

The 'DisgracedPilot' Fork
------

This is an experimental OpenPilot fork that uses the Accord-Bosch camera system to provide lane detection. It is strictly for research purposes only. It only aims to show that the vehicle can be controlled using Bosch lane guidance directly off of the CAN, made possible by carefully decoding the raw bit data and producing a custom DBC file. As a research + test article, absolutely no user-level support will be given. **IMPROPER USE OR ABUSE OF THIS SOFTWARE MAY RESULT IN PROPERTY DAMAGE, INJURY, OR DEATH. ANY APPLICATION OF THIS SOFTWARE IS AT YOUR OWN RISK.** 

The system in action: https://www.youtube.com/watch?v=GB8I9_anNG4

Instructions:

* Load code onto the EON.
* SSH into the EON and run 'scons' in the ~/openpilot folder. (May take one hour or more.)
* Copy LiveParameters from another fork into the ~/data/params folder.

Known Limitations:

 * There are innumerable unknown limitations, behaviours, and interactions that can and will adversely affect system performance.
 * Limited handling of loss of one or both lane lines. System may be unpredictable in this scenario.
 * No handling of lane changes. System tries to return to the centre of the original lane until the lane lines are passed.
 * Steep turns close to the Accord EPS torque limit have unpredictable performance.
 * Controls have only been mildly tuned, resulting in occasional lateral oscillation or overly-aggressive steering.
 * Bosch lane detection is unreliable near shadows or on rough, poorly-maintained roads.

To do:

* More accurately determine the decoding of the Bosch lane polynomial messages. Particularly need to understand the "LINE_JERK" parameter, as it seems inaccurate or misnamed. Other flags like line colour or slope seem to be present but need to be identified.
* Identify the coordinate frame of the Bosch camera. It may be referenced to the rear axle of the vehicle, instead of the camera centre in OpenPilot. The impact may be minimal, however.
* Investigate model features and deficiencies, e.g. moving from light into shadow, detection of non-line lane boundaries like curbs or grass.
* Handle common freeway features like lane merging + ending and freeway exits.
* Tune the controls and other new logic parameters.
* Re-purpose various vision and control warnings to be based on the Bosch lane outputs.
* Lightly smooth lane probabilities to reduce drive path jitter.
* Use adjacent lane lines to potentially improve or stabilise lane guidance.
* Consider new functionality, e.g. using the adjacent lane tracking to create a lane change assistance function; implementing navigation coasting to pass through intersections or deal with brief lane line dropouts; new parameter learner like camera offset; lead car following in laneless conditions.
* Determine which OpenPilot processes can be disabled and cleanly remove or ignore them. Particularly need to investigate the necessity of periodic steering angle offset calibration and if necessary, ways to perform one.
* Investigate running this fork on a Raspberry Pi 4. 
* Push any universal features to the main line OpenPilot.

Please contact me if you are interested in contributing to any of these points.