Test Case 1: Bird on the tracks
Precondition: Circuit is active, and components are functioning as intended.
Steps: Start -> checks for object -> object detected-> 100m inbound -> Lower Boom gates -> check tracks for object 50m outbound -> object detected (however object detected was stray bird) -> boom gates raised and lights stopped -> vehicle drives onto tracks, collision occurs.
Expected Result: Boom gates will close after train is detected and lights will flash. Boom gates will open, and lights will stop after train is detected 50m outbound.
Actual Result: Boom gates opened too early due to a false reading at 50m outbound sensor and collision occurred.
Status: Test failed
Possible improvements:
1.Replace simple motion sensor at 50m outbound with camera that an AI analyses to make sure it is a train and not any other object. 
2. Replace motion sensor with weight sensor that detected weight of train passing over tracks to ensure train has passed fully.

Test Case 2: Two trains were detected on the tracks. 
Precondition: Circuit is active, and components are functioning as intended
Steps: Start -> checks for object -> object detected-> 100m inbound -> Lower Boom gates -> check tracks for object 50m outbound -> object detected -> boom gates lifted and lights stopped-> vehicle drives onto tracks, collision occurs.
Expected Result: The first train passes the outbound 50m sensor, and the first train hits the 100m inbound sensor after that so there is enough time for the boom gates to lower again.
Actual Result: 50m outbound sensor detected an object and therefore the boom gates lifted however a train was still inbound and circuit did not re-lower the boom gates in time, a vehicle attempted crossing the tracks and a collision occurred.
Status: Test Failed
Possible improvements:
1. Extend the gap between the sensors and the crossing. 
2. Add logic circuit where if both are detected at the same time, ignore 100m sensor 

Test Case 3: A vehicle drives onto the tracks and breaks down, a train is inbound.
Precondition: Circuit is active, and components are functioning as intended
Steps: Start -> checks for object -> object detected-> On crossing -> Start timer for 10secs -> Object still on track after timer ends -> Lower boom gates and flash lights -> loop -> train arrives and crashes into the vehicle.
Expected Result: The object breaks down in the crossing, there is enough time to fix the vehicle or move it manually, there are no objects in the crossing, after 20 secs the boom gate raise.
Actual Result: The object breaks down in the crossing, the incoming train is not notified, it is not detected by the sensor as the logic is still looping due there still being an object in the crossing. The train crashes into the vehicle.
Status: Test Failed
Possible improvements:
1. Include an early warning system toward the inbound direction of the track to notify the trains of a vehicle on the tracks.
2. Include a winch on either side of the crossing to allow for quick removal of vehicles stuck on the crossing in emergencies.
3. Include a side track with a barrier to allow for trains to stop quickly if they cannot stop fully before reaching the crossing if a vehicle is stuck on it.
Test Case 4: Vehicle drives on to tracks via the crossing 
Precondition: Circuit is active, and components are functioning as intended
Steps: Start -> checks for object -> object detected-> On crossing -> Start timer for 10secs -> Object not on tracks -> Start timer for 20 secs -> Raise boom gates and stop lights -> incoming train -> no lights, boom gates up -> train crashes into vehicles
Expected Result: The vehicle drives onto the crossing, the boom gates lower, the vehicle drives across the crossing (not onto the train tracks) , the boom gates eventually raise.
Actual Result: The vehicle drives onto the crossing, then onto the train tracks, the train isn’t notified of the vehicle as it isn’t on the crossing, the train crashes into the vehicle.
Status: Test failed
Possible improvements:
1. Line the tracks with sensors to detect any large object and therefore trigger the boom gates
2. Install train track boom gates that lower when vehicles cross, but raise when the other boom gates lower
