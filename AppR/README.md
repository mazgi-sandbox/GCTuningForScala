An Application GC Tuning
====

## Before

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

## After

```
-Xms48G \
-Xmx48G \
-XX:NewSize=24G \
-XX:MaxPermSize=512M \
-XX:PermSize=256M \
-XX:+UseConcMarkSweepGC \
-XX:+CMSClassUnloadingEnabled \
-XX:+CMSPermGenSweepingEnabled \
-XX:CMSInitiatingOccupancyFraction=75 \
-XX:+UseCMSInitiatingOccupancyOnly \
-verbose:gc \
-Xloggc:$GC_LOG \
-XX:+PrintGCDetails \
-XX:+PrintGCDateStamps \
-XX:+HeapDumpOnOutOfMemoryError \
-XX:+UseGCLogFileRotation \
-XX:NumberOfGCLogFiles=10 \
-XX:GCLogFileSize=10M \
```

