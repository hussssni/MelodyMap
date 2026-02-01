# Spotify Song Recommendation System

A graph-based music recommendation system that finds similar songs based on audio features and creates personalized Spotify playlists.

**CSC111 Project 2 - University of Toronto**

## Overview

This application analyzes Spotify song data to find tracks with similar audio characteristics. When you select a song, the system:

1. Calculates similarity scores against thousands of songs using audio features
2. Returns the top 25 most similar tracks with similarity percentages
3. Automatically creates a Spotify playlist with your recommendations
4. Visualizes the song similarity network as an interactive graph

## Features

- **Smart Song Search**: Search by song name or artist with auto-suggestions
- **Audio-Based Matching**: Uses 11 audio features for accurate similarity scoring
- **Spotify Integration**: Creates public playlists directly in your Spotify account
- **Network Visualization**: Interactive graph showing song relationships
- **Multi-Song Mode**: Find songs similar to two tracks simultaneously

## How It Works

### Similarity Algorithm

Songs are compared using normalized Euclidean distance across these Spotify audio features:

| Feature | Description |
|---------|-------------|
| Danceability | How suitable for dancing (0.0 - 1.0) |
| Energy | Intensity and activity level (0.0 - 1.0) |
| Valence | Musical positiveness/happiness (0.0 - 1.0) |
| Tempo | Beats per minute (BPM) |
| Acousticness | Confidence the track is acoustic |
| Speechiness | Presence of spoken words |
| Instrumentalness | Likelihood of no vocals |
| Liveness | Probability of live recording |
| Loudness | Overall volume in decibels |
| Key | Musical key (0-11) |
| Mode | Major (1) or minor (0) |

The similarity score ranges from 0% (completely different) to 100% (identical features).

### Graph Structure

- Each song is a **vertex** containing metadata and audio features
- **Edges** connect songs with similarity scores above 90%
- The graph enables efficient traversal and relationship visualization

## Installation

### Prerequisites

- Python 3.9+
- Spotify Developer Account (for API access)

### Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/project_2.git
   cd project_2
   ```

2. Install dependencies:
   ```bash
   pip install spotipy networkx matplotlib
   ```

3. Configure Spotify API credentials in `main.py`:
   ```python
   SPOTIFY_CLIENT_ID = "your_client_id"
   SPOTIFY_CLIENT_SECRET = "your_client_secret"
   SPOTIFY_REDIRECT_URI = "http://127.0.0.1:8080"
   ```

4. Run the application:
   ```bash
   python main.py
   ```

## Usage

### Single Song Mode (`main.py`)

1. Launch the GUI with `python main.py`
2. Type a song name or artist in the search box
3. Select a song from the suggestions
4. Click "Select Song" to get recommendations
5. View similarity scores and the generated playlist link
6. Double-click the playlist link to open in Spotify

### Multi-Song Mode (`multiple song.py`)

1. Run `python "multiple song.py"`
2. Enter two song names when prompted
3. View songs that are similar to both tracks
4. See the dual-similarity visualization

## Project Structure

```
project_2/
├── main.py                 # Main application with GUI
├── multiple song.py        # Two-song similarity comparison
├── Graphing.py            # Graph/Vertex class implementations
├── ex3_visualization.py   # Alternate visualization module
├── spotify_songs.csv      # Dataset (~32,000 songs)
└── spotify_data/
    └── readme.md          # Dataset documentation
```

## Dataset

The dataset contains approximately 32,000 Spotify songs with:
- Track metadata (name, artist, album)
- Audio features extracted via Spotify API
- Popularity scores

Source: [TidyTuesday Spotify Dataset](https://github.com/rfordatascience/tidytuesday/tree/master/data/2020/2020-01-21)

## Visualization

The network graph displays:
- **Red node**: Your selected song
- **Green nodes**: Similar songs (90%+ similarity)
- **Edges**: Connections between highly similar tracks

## Dependencies

- `spotipy` - Spotify API wrapper
- `networkx` - Graph data structures
- `matplotlib` - Visualization
- `tkinter` - GUI framework (included with Python)

## Authors

CSC111 Project Team - University of Toronto.

## License

This project is for educational purposes as part of CSC111 coursework.
