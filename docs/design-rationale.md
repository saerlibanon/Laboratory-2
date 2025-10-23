# Design rationale

This document summarizes what structural patterns are used, where they appear in the code, and why they were chosen. The rationale is intentionally short to keep the lab focused and practical.

Adapter
- Where: `Source.java` — `LocalFileSource`, `HlsStreamSource`, `RemoteApiSource`
- Why: Different media sources expose different ways to obtain data. The Adapter role standardizes this to a `Stream` object so the rest of the system (player, renderers) can remain source-agnostic.

Proxy
- Where: `CachingProxy` in `Source.java`
- Why: Demonstrates an object that controls access to another (remote or slow) resource and adds caching behavior without altering the client or source implementations.

Composite
- Where: `Playlist.java`
- Why: Playlists can contain items and nested playlists. The Composite pattern lets code treat both uniformly by implementing the same `Playable` interface.

Render implementor (Bridge-style)
- Where: `RenderImpl` interface and concrete `SoftwareRenderImpl` / `HardwareRenderImpl` in `Player.java`
- Why: Decouples how media is rendered from the player abstraction. `Main` can substitute render implementors at runtime to demonstrate hardware vs software rendering.

Decorator
- Where: `PlayerDecorator` and `SubtitlePlugin`, `EqualizerPlugin`, `WatermarkPlugin` in `Player.java`
- Why: Enables adding features (subtitles, EQ, watermark) to the player dynamically without modifying the core `MediaPlayer` class.

Trade-offs and choices
- Files grouped to stay under 10 files for clarity: related small classes were co-located (e.g., sources and simple `Stream` in `Source.java`). In production each class would likely get its own file.
- The demo favors clarity and visible console traces over production concerns such as real stream handling, error recovery, and cache eviction policies.
- Plugin ordering is deterministic and controlled by `Main` when constructing the decorator chain. A production system could provide a pluggable registry for dynamic ordering.

Testing and future extensions
- Small unit tests would validate `CachingProxy` cache behavior and `Playlist` traversal.
- Extensions: add dynamic plugin loading and specific configuration objects. This will allow for handling real-time network streams smoothly by incorporating effective jitter handling.
