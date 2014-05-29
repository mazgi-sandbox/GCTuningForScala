An Application GC Tuning
====

## App summary

### Server spec

## JVM & GC parameters

### Before

```
-Xms48G \
-Xmx48G \
-XX:NewSize=24G \
-XX:MaxPermSize=512M \
-XX:PermSize=256M \
-verbose:gc \
-Xloggc:$GC_LOG \
-XX:+PrintGCDetails \
-XX:+PrintGCDateStamps \
-XX:+HeapDumpOnOutOfMemoryError \
-XX:+UseGCLogFileRotation \
-XX:NumberOfGCLogFiles=10 \
-XX:GCLogFileSize=10M \
```

### After

```
-server \
-Xms48G \
-Xmx48G \
-XX:NewSize=32G \
-XX:SurvivorRatio=6 \
-XX:PermSize=128M \
-XX:MaxPermSize=128M \
-XX:MaxTenuringThreshold=512 \
-XX:+DisableExplicitGC \
-XX:+UseConcMarkSweepGC \
-XX:+CMSClassUnloadingEnabled \
-XX:+CMSPermGenSweepingEnabled \
-XX:+CMSParallelRemarkEnabled \
-XX:CMSInitiatingOccupancyFraction=75 \
-XX:+UseCMSInitiatingOccupancyOnly \
-verbose:gc \
-Xloggc:$GC_LOG \
-XX:+PrintGCDetails \
-XX:+PrintGCDateStamps \
-XX:+UseGCLogFileRotation \
-XX:NumberOfGCLogFiles=10 \
-XX:GCLogFileSize=10M \
```

