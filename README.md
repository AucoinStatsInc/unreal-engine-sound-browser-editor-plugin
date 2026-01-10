# Unreal Engine Sound Browser Editor Plugin For Freesound.org

> **Note**: This repository is for documentation and issue tracking only. The plugin itself is distributed exclusively through the Epic Games Fab Marketplace.

[**Sound Browser for Freesound.org**](https://www.fab.com/listings/a2698cbd-6529-4179-b25c-8860c0cc0aba) is an Unreal Engine editor plugin that lets you search, preview, and import sound effects from Freesound.org directly inside the Unreal Editor, without leaving your workflow.

The plugin is designed to help solo developers and small teams prototype quickly by making it easy to discover suitable sound effects, preview them instantly, and turn them into Unreal sound assets with relevant metadata preserved.

> **Disclaimer**  
> This plugin integrates with the public Freesound.org API but is **not affiliated with, endorsed by, or officially connected to Freesound.org or its maintainers**.

![Sound Browser for Freesound.org - Preview image](assets/sound-browser-plugin-screenshot.png)

---

## Main Features

- Search Freesound.org directly from the Unreal Editor
- Preview sound effects instantly using high-quality preview audio
- Filter results by:
  - Publisher
  - Maximum duration
  - License type
- Create `USoundWave` assets from preview audio
- Specify the default asset creation location
- Cache downloaded preview audio for reuse
  - Cache can be shared across multiple Unreal projects
- Generated sound assets include searchable metadata:
  - Freesound identifier
  - Name
  - Publisher
- Generated sound assets also include Freesound-specific metadata and editor customization:
  - User metadata stored directly on the `USoundWave` asset
  - A custom **“Freesound”** category in the asset’s Details panel
  - Displayed information includes:
    - Freesound ID (with direct link to the sound’s page)
    - Sound name
    - Publisher (with direct link to the publisher’s profile)
    - License information (i.e., a direct link to the license)
    - Asset creation date

---

## About Freesound.org

Freesound.org is a large, community-driven online sound library maintained by the Music Technology Group at Universitat Pompeu Fabra in Barcelona. It hosts hundreds of thousands of user-contributed sound effects, recordings, and audio clips covering a wide range of categories and styles.

Sounds on Freesound are published under various Creative Commons licenses, and usage terms depend on the specific license chosen by each contributor.

> **Note**  
> Users are responsible for reviewing and complying with the license terms associated with each sound they download or use.

---

## Supported Versions and Platforms

**Supported Unreal Engine Versions:**
* Unreal Engine 5.5
* Unreal Engine 5.6
* Unreal Engine 5.7

**Supported Platforms:**
* Windows (Editor)
* macOS (Editor)

> **macOS support note**  
> While the plugin has been fully tested and confirmed to work on macOS, the Fab Store’s macOS build pipeline was not functioning properly at the time of publication. As a result, no macOS binaries were produced on Epic’s end for the moment. The issue is expected to be resolved soon.

> **Linux support note (unofficial):**
> This plugin has not been officially tested on native Linux editor builds.
> However, it does not rely on any known platform-specific APIs and is expected
> to compile on Linux-based Unreal Engine editor environments.
>
> Linux support is therefore considered unofficial and is not currently provided
> as part of the supported platforms listed above.


---

## Getting Started

1. Download and install the plugin (either at the engine or project level).
2. Enable the plugin in Unreal Engine.
3. Open the Sound Browser window:
   - From the Level Editor toolbar
   - From the Window menu
   - From the Content Browser toolbar
   - From the Content Browser context menu
4. Enter search keywords in the search field to query Freesound.org.

### Freesound API Key

Accessing the Freesound API requires an API key, which you can obtain from:  
https://freesound.org/apiv2/apply/

The plugin will guide you through the setup process and help you configure your API key.

---

## Browsing and Importing Sounds

- Search results are paginated (10 items per page by default; configurable in settings).
- Click the **Play** button to download and preview a sound.
- Click a result row to open the detailed view.
- Use the filter menu to narrow results by license, duration, or publisher.
- When you find a suitable sound, click **Create Sound Asset** to generate a `USoundWave` asset from the cached preview audio.

---

## Notes on Audio Assets

- Sound assets are created from the high-quality MP3 preview files served by Freesound’s CDN.
- Preview audio is used intentionally to provide fast downloads, consistent playback, and a smooth editor experience during prototyping.

---

## Typical Use Cases

Sound Browser for Freesound.org is ideal for:

- Solo developers and small indie teams
- Rapid prototyping and iteration
- Placeholder or early-stage sound design
- Projects where staying inside the Unreal Editor improves productivity

By eliminating the need to switch between a web browser and the editor, the plugin helps streamline audio discovery and asset creation. Sound effects can be searched, previewed, filtered by license, and imported in just a few clicks. Imported assets retain relevant Freesound metadata and a direct connection to their source, making it easy to track sounds in the Content Browser and revisit their license, author, and source page long after import.

---

## Security & Privacy

Sound Browser for Freesound.org is designed with privacy and minimal data exposure in mind.

- The plugin only communicates with Freesound.org’s public API endpoints and its content delivery network (CDN) to retrieve publicly available preview audio files.
- Your Freesound API key is stored locally using Unreal Engine’s standard settings system and is never transmitted to third parties.
- No personal account information is accessed beyond what is required to perform search and preview requests.
- The plugin does not perform authenticated downloads of original source files and does not trigger public download actions on your behalf.
- No usage analytics, telemetry, or tracking data are collected by the plugin.

All network communication is limited to querying Freesound.org and downloading publicly available preview audio files.

---

## Support

- [Epic Developer Community forum thread](https://forums.unrealengine.com/t/aucoinstats-inc-sound-browser-for-freesound-org/2690966)
- [GitHub documentation and issue tracker](https://github.com/AucoinStatsInc/unreal-engine-sound-browser-editor-plugin)

---

## Frequently Asked Questions

### How is my Freesound API key stored?

Your Freesound API key is stored locally in the plugin’s settings using Unreal Engine’s standard `UDeveloperSettings` system, similar to how other editor plugins store API keys (for example, the Android SDK configuration).

The API key used by this plugin has **search and query-only permissions**. It is tied to your Freesound account and is used primarily for request throttling and identification. It does **not** grant access to account management features or private user data.

While your API key should not be shared, compromising it does **not** allow someone to take control of your Freesound account. You can revoke or regenerate your API key at any time from your Freesound account settings if needed.

---

### What is the difference between preview audio and original source files?

Freesound provides preview audio files that are publicly accessible and optimized for fast playback and discovery. This plugin uses those preview files for sound previewing and asset creation inside the Unreal Editor.

Accessing the original source files on Freesound requires authenticated downloads through the website or via OAuth2 authorization. While OAuth2 support was explored, it was intentionally not included in this plugin.

Downloading original files on Freesound is a **public, permanent action** that appears on the sound’s profile page and cannot be removed. Requiring OAuth2 would mean that such public download actions could be triggered directly from the plugin, which many users may not want.

By using preview audio instead, the plugin:
- Preserves user privacy
- Avoids unintended public download records
- Provides a smoother and faster editor experience
- Keeps setup and usage simple

Users who need the original source files can still download them manually from Freesound.org.

---

### What do I need to use this plugin?

To use Sound Browser for Freesound.org, you will need:

- A supported version of Unreal Engine
- An active Freesound.org account
- A Freesound API key
- Internet access

The plugin will guide you through the API key setup process.

---

### What is Freesound.org?

Freesound.org is a large, community-driven online sound library maintained by the Music Technology Group at Universitat Pompeu Fabra in Barcelona. It hosts hundreds of thousands of user-contributed sound effects, recordings, and audio clips covering a wide range of categories and styles.

Sounds on Freesound are published under various Creative Commons licenses, and usage terms depend on the specific license chosen by each contributor.
