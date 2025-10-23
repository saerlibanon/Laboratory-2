Architecture overview
---------------------

This document briefly outlines the Media Player's architecture, which is intentionally built using structural design patterns to ensure high flexibility, modularity, and extensibility. The application is an adaptable player designed to easily source and play content from various providers.

Key Design Patterns Used
Bridge Pattern: The MediaPlayer and RenderImpl components decouple the player from its rendering technology, allowing for runtime switching (e.g., between software and hardware rendering).

Decorator Pattern: Implemented by PlayerDecorator and its subclasses, this enables the dynamic addition of features (like subtitles or equalizers) to the core player logic without modifying existing code.

Adapter Pattern: The MediaSource interface provides a consistent interface to access diverse media sources, simplifying the integration of new or external data providers.

Proxy Pattern: The CachingProxy adds transparent performance caching around a media source, reducing redundant remote data fetching.

Composite Pattern: The Playlist class allows for the uniform handling of both single tracks (MediaItems) and nested collections (Playlists), treating them identically.