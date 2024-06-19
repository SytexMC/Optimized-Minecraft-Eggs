
If you aren't running the server on pterodactyl, replace `{{SERVER_MEMORY}}` with your server's memory in megabytes.

Also remove `--add-modules=jdk.incubator.vector`, if you are running any server software that isn't a fork of pufferfish, which I do not recommend.

Here you can find a startup flag generator that can automatically generate these flags for you.

### Recommended Memory

**I recommend using at least 4-8GB**, no matter how few players! 
If you can't afford 8GB of memory, give as much as you can, but ensure you also leave the operating system some memory too. G1GC operates better with more memory!

However, more memory does not mean better performance above a certain point. Eventually you will hit a point of diminishing returns. Going out and getting 32GB of RAM for a server will only waste your money with minimal returns.
### [Dynamic Startup Flags](https://docs.papermc.io/paper/aikars-flags#technical-explanation-of-the-flags)

```
java -Xms128M -Xmx{{SERVER_MEMORY}}M --add-modules=jdk.incubator.vector -XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=8M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:SurvivorRatio=32 -XX:+PerfDisableSharedMem -XX:MaxTenuringThreshold=1 -Dusing.aikars.flags=https://mcflags.emc.gs -Daikars.new.flags=true -jar {{SERVER_JARFILE}} --nogui
```

### [Static Startup Flags](https://docs.papermc.io/paper/aikars-flags#technical-explanation-of-the-flags)

```
java -Xms{{SERVER_MEMORY}}M -Xmx{{SERVER_MEMORY}}M --add-modules=jdk.incubator.vector -XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=8M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:SurvivorRatio=32 -XX:+PerfDisableSharedMem -XX:MaxTenuringThreshold=1 -Dusing.aikars.flags=https://mcflags.emc.gs -Daikars.new.flags=true -jar {{SERVER_JARFILE}} --nogui
```
