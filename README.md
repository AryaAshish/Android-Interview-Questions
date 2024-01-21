# Android-Interview-Questions
This is a compilation of Important Android Interview question and answers 



## Core Android
### Android Interview Questions:

#### Base
##### Why does an Android App lag?

##### Reasons and Solutions for Android App Lag

1. **Major Culprit: Garbage Collector (GC)**
   - Frequent GC runs interrupt app execution, causing lag.
   - GC time is downtime for the app, impacting UI updates and smooth performance.

2. **Additional Cause: Main Thread Overload**
   - Performing extensive tasks on the main thread (>16ms) leads to UI lag.
   - Frame drops occur when UI updates take longer than the 16ms target.

3. **Performance Improvement Steps:**
   - **Memory Optimization:**
     - Avoid unnecessary object allocation.
     - Utilize lazy initialization to allocate objects when needed.
     - Minimize auto-boxing, favor primitive types over classes.
     - Implement object pools to manage memory efficiently.

   - **Thread Management:**
     - Offload heavy work to background threads.
     - Use static final or const val for constants.
     - Optimize getters/setters, favor direct field access for speed.
     - Prevent context leaks in inner classes, prefer static inner classes.

   - **Memory Cache Strategies:**
     - Implement LRU cache for bitmaps to reduce GC calls.
     - Leverage tools like StrictMode to catch accidental main thread operations.
     - Enable Profile GPU Rendering for visualizing frame rendering performance.

   - **General Tips:**
     - Avoid unnecessary object allocation to reduce memory churn.
     - Adopt good coding practices to enhance app responsiveness and user experience.

For a comprehensive solution, developers should focus on minimizing GC impact, optimizing main thread tasks, and implementing effective memory management strategies.




