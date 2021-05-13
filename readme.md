# Coroutines debugger does not work with Kotlin 1.5.0 + coroutines 1.5.0-RC

Just discovered, this problem.

Roman Elizarov has already issued an error report here:

<https://youtrack.jetbrains.com/issue/KTIJ-11620>

![screenshot](/Screenshot.png)

# Trace
```
2021-05-13 16:33:34,202 [1935636]  ERROR - roxy.CoroutineDebugProbesProxy - Exception is thrown by calling dumpCoroutines. 
java.lang.IllegalStateException: Unable to find loaded class _COROUTINE._CREATION
	at org.jetbrains.kotlin.idea.debugger.coroutine.proxy.LocationCache.createLocation(LocationCache.kt:17)
	at org.jetbrains.kotlin.idea.debugger.coroutine.proxy.CoroutineLibraryAgent2Proxy.findStackFrames(CoroutineLibraryAgent2Proxy.kt:86)
	
    ...
    
	at java.base/java.util.concurrent.Executors$PrivilegedThreadFactory$1$1.run(Executors.java:668)
	at java.base/java.util.concurrent.Executors$PrivilegedThreadFactory$1$1.run(Executors.java:665)
	at java.base/java.security.AccessController.doPrivileged(Native Method)
	at java.base/java.util.concurrent.Executors$PrivilegedThreadFactory$1.run(Executors.java:665)
	at java.base/java.lang.Thread.run(Thread.java:834)
2021-05-13 16:33:34,204 [1935638]  ERROR - roxy.CoroutineDebugProbesProxy - IntelliJ IDEA 2021.1  Build #IU-211.6693.111 
2021-05-13 16:33:34,206 [1935640]  ERROR - roxy.CoroutineDebugProbesProxy - JDK: 11.0.10; VM: Dynamic Code Evolution 64-Bit Server VM; Vendor: JetBrains s.r.o. 
2021-05-13 16:33:34,207 [1935641]  ERROR - roxy.CoroutineDebugProbesProxy - OS: Linux 
2021-05-13 16:33:34,207 [1935641]  ERROR - roxy.CoroutineDebugProbesProxy - Plugin to blame: Kotlin version: 211-1.5.0-release-759-IJ6693.72 
2021-05-13 16:33:34,207 [1935641]  ERROR - roxy.CoroutineDebugProbesProxy - Last Action: Debug 
```