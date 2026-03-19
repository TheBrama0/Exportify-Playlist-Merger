# 🎵 Exportify CSV Compiler Tool

A pure HTML/JavaScript tool that merges CSV files exported from **exportify.app** and **exportify.net** into one comprehensive CSV. All processing happens in your browser – your files never leave your device.

## 🌟 Features
- **Merge two CSV exports** of the same Spotify playlist.
- **Outer join on `Track URI`** – no data is lost; tracks appearing in only one file are still included.
- **Predefined column mapping** combines metadata from `exportify.app` with audio features from `exportify.net`.
- **Smart file detection** – upload files in any order; the tool automatically identifies which is from `.app` and which from `.net`.
- **Preview** the first 20 rows of the merged result.
- **Custom output filename** – name your merged file before downloading (default: `Playlist-Merger.csv`).
- **100% client‑side** – no server, no upload, works offline once downloaded.
- **Self‑contained** – includes the [Papa Parse](https://www.papaparse.com/) library locally, so no external dependencies.

## 📋 Column Mapping (What gets merged)

| Source Column (exportify.app)       | Source Column (exportify.net)        | Final Column               | Merge Rule                                      |
|-------------------------------------|--------------------------------------|----------------------------|-------------------------------------------------|
| Track URI                           | Track URI                            | Track URI                  | Merge key – identical in both files.            |
| Track Name                          | Track Name                           | Track Name                 | Prefer exportify.net, else exportify.app.       |
| Artist URI(s)                       | –                                    | Artist URI(s)              | Only from exportify.app.                        |
| Artist Name(s)                      | Artist Name(s)                       | Artist Name(s)             | Prefer exportify.net, else exportify.app.       |
| Album URI                           | –                                    | Album URI                  | Only from exportify.app.                        |
| Album Name                          | Album Name                           | Album Name                 | Prefer exportify.net, else exportify.app.       |
| Album Artist URI(s)                 | –                                    | Album Artist URI(s)        | Only from exportify.app.                        |
| Album Artist Name(s)                | –                                    | Album Artist Name(s)       | Only from exportify.app.                        |
| Album Release Date                  | –                                    | Album Release Date         | Only from exportify.app.                        |
| Album Image URL                     | –                                    | Album Image URL            | Only from exportify.app.                        |
| Disc Number                         | –                                    | Disc Number                | Only from exportify.app.                        |
| Track Number                        | –                                    | Track Number               | Only from exportify.app.                        |
| Track Duration (ms)                 | Duration (ms)                        | Track Duration (ms)        | Prefer exportify.net, else exportify.app.       |
| Track Preview URL                   | –                                    | Track Preview URL          | Only from exportify.app.                        |
| Explicit                            | Explicit                             | Explicit                   | Prefer exportify.net, else exportify.app.       |
| Popularity                          | Popularity                           | Popularity                 | Prefer exportify.net, else exportify.app.       |
| ISRC                                | –                                    | ISRC                       | Only from exportify.app.                        |
| Added By                            | Added By                             | Added By                   | Prefer exportify.net, else exportify.app.       |
| Added At                            | Added At                             | Added At                   | Prefer exportify.net, else exportify.app.       |
| –                                   | Release Date                         | Release Date               | Only from exportify.net.                         |
| –                                   | Genres                               | Genres                     | Only from exportify.net.                         |
| –                                   | Record Label                         | Record Label               | Only from exportify.net.                         |
| –                                   | Danceability                         | Danceability               | Only from exportify.net.                         |
| –                                   | Energy                               | Energy                     | Only from exportify.net.                         |
| –                                   | Key                                  | Key                        | Only from exportify.net.                         |
| –                                   | Loudness                             | Loudness                   | Only from exportify.net.                         |
| –                                   | Mode                                 | Mode                       | Only from exportify.net.                         |
| –                                   | Speechiness                          | Speechiness                | Only from exportify.net.                         |
| –                                   | Acousticness                         | Acousticness               | Only from exportify.net.                         |
| –                                   | Instrumentalness                     | Instrumentalness           | Only from exportify.net.                         |
| –                                   | Liveness                             | Liveness                   | Only from exportify.net.                         |
| –                                   | Valence                              | Valence                    | Only from exportify.net.                         |
| –                                   | Tempo                                | Tempo                      | Only from exportify.net.                         |
| –                                   | Time Signature                       | Time Signature             | Only from exportify.net.                         |

> **Note:** If a column is missing in one file (e.g., exportify.net has no `Artist URI(s)`), the value from the other file is used when the track exists in both. If a track is only in one file, the other file's columns remain empty.

## 🚀 How to Use

### Option 1: Use the hosted version (GitHub Pages)
1. Go to the live tool at [https://thebrama0.github.io/Exportify-Playlist-Merger/](https://thebrama0.github.io/Exportify-Playlist-Merger/).

### Option 2: Run locally (offline)
1. **Download the repository** as a ZIP from GitHub and extract it, or clone it.
2. Open the extracted folder – you'll see two files:
   - `index.html`
   - `papaparse.min.js` (included – no need to download separately)
3. **Double‑click `index.html`** – it will open in your default browser.

### Using the tool
1. **Export the same playlist** from both [exportify.app](https://exportify.app) and [exportify.net](https://exportify.net).  
   - Keep the files as downloaded; you don't need to rename them.
2. In the tool, click **Choose File** for **File 1** and select one of the CSV files.
3. Click **Choose File** for **File 2** and select the other CSV file.  
   *(The order doesn't matter – the tool automatically detects which file is from exportify.app and which from exportify.net.)*
4. Optionally change the **output filename** (default: `Playlist-Merger`).
5. Click **Merge & Preview** – the first 20 rows of the merged data will appear.
6. Click **Download merged CSV** to save the complete file.

## ⚠️ Important Notes
- **Same playlist:** For best results, export the identical playlist from both services. If the playlists differ, tracks unique to one side will still appear, but some columns will be empty.
- **No data leaves your device:** All processing is done locally in your browser – your CSV files are never uploaded to any server.
- **Offline ready:** Because the Papa Parse library is included locally, the tool works completely offline after you've downloaded the repository.

## 📄 License
This project is open source under the [MIT License](LICENSE). Feel free to modify and share.

---

**Made for Exportify users – because combining metadata shouldn't be a hassle.**
