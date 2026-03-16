# 🎵 MusicConnect for Unreal Engine
### The Ultimate Blueprint-Driven Audio Streaming Plugin

Welcome to **MusicConnect**! This plugin allows you to stream audio directly from platforms like YouTube, Spotify, SoundCloud, and Apple Music straight into your Unreal Engine project.

MusicConnect is **100% Blueprint friendly**. You don't need any coding knowledge to use it. Just add the component, drop in a few nodes, and you are ready to play music!

---

## 🚀 Quick Start: Playing Your First Song
Getting music to play in your game takes less than a minute.

### Step 1: Add the Component
1. Open your `GameMode`, `PlayerController`, or any custom Blueprint actor.
2. Go to the **Components** panel, click **+ Add**, and search for `Music Connect Player`.
3. Add it to your Blueprint.

### Step 2: Use the "Play Music Stream" Node
We have created a powerful, all-in-one async node to handle playback automatically.

1. Drag your **Music Connect Player** component into your Event Graph.
2. Drag a wire from it and search for **Play Music Stream**.
3. In the **Search Or URL** pin, type a song name (e.g., *"Daft Punk Get Lucky"*) or paste a direct URL.
4. Connect this node to an event (like `BeginPlay` or a UI button click).

**Understanding the Execution Pins:**
* **On Playing:** Fires as soon as the music successfully starts streaming. Perfect for updating UI.
* **On Track Changed:** Fires when a playlist moves to the next song automatically.
* **On Error:** Fires if the search fails, internet is disconnected, or the platform is unsupported.

---

## 🎛️ Blueprint Nodes & Controls
Once your music is playing, you can control it easily using the built-in Blueprint nodes.

### Playback Controls
* **Pause Music:** Pauses the current track.
* **Resume Music:** Resumes paused playback.
* **Stop Music:** Fully stops the audio and clears the player.
* **Next Track / Previous Track:** Skips in your playlist.
* **Jump To Track:** Skips to a specific song index in a playlist.

### Audio & Settings
* **Set Volume:** Instantly change the volume (Value between `0.0` and `1.0`).
* **Fade Volume:** Smoothly transitions volume over time.
* **Set Looping:** Loop a single track or an entire playlist.
* **Set Shuffle:** Randomizes the playlist order.

### Getting Information (Variables)
* **Get Current Track:** Breaks open a struct containing *Title, Artist, Thumbnail URL,* and *Duration*.
* **Get Player State:** Returns current status (e.g., *Playing, Paused, Buffering, Resolving*).
* **Get Playback Position:** Returns the current timestamp in seconds.

---

## ⚡ Event Dispatchers
If you want your UI to react automatically, bind events directly to the component:

1. Select **Music Connect Player** in your Components list.
2. Scroll down in the **Details** panel to the **Events** section.
3. Click the **+** icon next to:
    * `On State Changed`
    * `On Track Changed`
    * `On Error`

---

## 📦 Crucial Step for Packaged Games
MusicConnect uses a background streaming engine. For this to work in your final game, you **must** include its folder:

1. Go to **Edit > Project Settings**.
2. Search for **Additional Non-Asset Directories to Copy**.
3. Add a new element to the array (+).
4. Paste exactly this text: `Plugins/MusicConnect/Binaries/ThirdParty`

> [!CAUTION]
> If you skip this step, the plugin will work in the Editor but **will not play music** in the packaged game!

---

## ❓ FAQ for Blueprint Users

**Q: Can I use Spotify or Apple Music links?** **A:** Yes! The plugin reads the URL, finds the song metadata, and seamlessly plays the high-quality audio track via YouTube in the background.

**Q: Why does the music take 1-3 seconds to start?** **A:** The node must search the internet and buffer the stream. You can use the `Get Player State` node to show a loading spinner when it is "Buffering".

**Q: Will this work on Android, iOS, or Consoles?** **A:** **No.** MusicConnect uses background desktop processes. It is supported on **Windows, Mac, and Linux** only.
