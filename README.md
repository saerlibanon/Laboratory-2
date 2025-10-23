# Modular Media Streaming Suite (Java)

### Description
A modular media player simulation demonstrating multiple **Structural Design Patterns**:
- Bridge (Renderer switching)
- Decorator (Feature plugins)
- Proxy (Caching remote sources)
- Adapter (Unified media source interface)
- Composite (Playlists of items)

---

# How to Run the Project

1. Save the provided code into the following files in a single directory:
- Main.java
- Media.java
- MediaItem.java
- Playable.java
- Player.java
- Playlist.java
- Source.java

2. Compile
 - Open IDE such as VS Code, IntelliJ, or Eclipse or Open your terminal or command prompt, navigate to the directory where you saved the files

3. Run the Main.java demo

# After running 'java Main', enter the following:

Choose media source:
1 - Local File (No Proxy)
2 - HLS Stream (With Proxy Cache)
3 - Remote API (With Proxy Cache)
> 2

Enter media identifier (filename for Local, URL for HLS, id for Remote). Press Enter to use default:
> 

Available plugins: subtitle, equalizer, watermark
Enter plugins to enable (comma-separated or 'none'):
> equalizer, watermark

Switch renderer (hardware/software/quit):
> hardware

Playing with settings:
 - Media: Live HLS
 - Renderer: hardware
 - Plugins: equalizer, watermark

[EqualizerPlugin] Applying EQ preset: Bass Boost
[Player] Start playing: Live HLS
[Proxy] Cache miss for HlsStreamSource@... - fetching
[HardwareRenderer] Playing 'Live HLS' using hardware from HLS(https://example.com/stream.m3u8)
[Player] Finished: Live HLS
[Plugin] Watermark is on

Play another? (y/n): n
Exiting.

