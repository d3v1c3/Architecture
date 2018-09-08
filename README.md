# Architecture

d3v1c3 is an architecture for the secure delivery of executable and configuration bundles to IoT devices.  The bundles themselves are signed (to the best ability of the relevant component) and version controlled in a public (here GitHub) repository set.

Ideally, a d3v1c3 will have a minimum set of features.  It can have fewer (e.g. Protected PROM, or they can be emulated (e.g. cert store).  But the guarantees of the architecture depend upon the minimal set, and therefore will not be realized.

d3v1c3 guarantees that an IoT node, which has the minimum features, and when used properly, will be running exactly the image, and with the exact configuration, that the d3v1c3 owner specifies.  Futher, that the d3v1c3 has a secure mechanism to transition from one runtime-state to another according to pre-determined rules.  Finally, that the d3v1c3 has a mechanism to update it's executable and or configuration bundle.   Optionally, the d3v1c3 has the ability to select degraded-state operations to keep running in the event of certain events (e.g. Loss of connectivity, resource starvation, or exhaustion of certificates due to revocations.)

d3v1c3 is an amalgam of several components.  As an implementation guide, these are best realized by existing projects.  They can be realized by multiple components.

Components

**Server:

***State Server -- Receives a JSON struct of d3v1c3's state and responds with a "next state" JSON Response
***Artifact Server -- Serves files / Provides lookup services
***DNSSec Server -- d3v1c3.xyz is the signed root for d3v1c3s, and d3v1c3.io is the signed root for d3v1c3 services.
*** 

**d3v1c3 
***boot loader -- Generally supplied by HW manufacturer  
***transition loader (s) -- check state response and load the next bundle until next-state === state
***Runtimes -- Specialized execute bundles that can contain sub-bundle executables
**** Examples
*****Python, Julia, Kotlin, Java
*****JEE, node

