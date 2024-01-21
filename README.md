# Android-Interview-Questions
This is a compilation of Important Android Interview questions and answers.

## Core Android
### Android Interview Questions:

#### Base
##### Why does an Android App lag?

**Reasons and Solutions for Android App Lag**

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

##### When to use `getApplicationContext()` in Android and why?

**Understanding Context in Android Development**

- **Definition:** Context in Android refers to the current state and location within the application, providing information about the activity and application, essential for various operations.

- **Importance:** Context is crucial in Android development, used for accessing resources, databases, shared preferences, and more. It plays a pivotal role in preventing memory leaks, making correct usage vital.

- **Types of Context:**
  1. **Application Context:** Singleton instance tied to the application's lifecycle. Used when a context is needed beyond the scope of an activity, preventing memory leaks.
  2. **Activity Context:** Associated with the activity's lifecycle. Used for UI operations within an activity, like showing toasts and dialogs.

- **When to Use:**
  - **Application Context:** For singleton objects and library initialization in activities to prevent memory leaks.
  - **Activity Context:** For UI operations such as displaying toasts and dialogs within an activity.

- **Example:**
  - **MyApplication (extends Application):** Application context is present.
  - **MainActivity1 and MainActivity2:** Both have both Activity context and Application context.
  - **getContext() in ContentProvider:** Provides the application context.

- **Best Practices:**
  - Use the nearest context available (Activity or Application context) based on the scope of your operation.
  - Singleton objects, tied to the application's lifecycle, should use the Application Context.
  - Avoid using `getApplicationContext()` for GUI-related operations to prevent memory leaks.
  
- **Rule of Thumb:** Use the context directly available from the enclosing component, ensuring the reference does not extend beyond the component's lifecycle. Switch to the application context for references that outlive the Activity or Service.

---

