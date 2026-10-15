# Beacon 

![Swift](https://img.shields.io/badge/Swift-F05138?logo=swift&logoColor=white)
![SwiftUI](https://img.shields.io/badge/SwiftUI-0D96F6?logo=swift&logoColor=white)
![iOS](https://img.shields.io/badge/iOS_26-000000?logo=apple&logoColor=white)

> Find cafés, restaurants and hotels around you, right on the map.

Beacon is a place-discovery app built around an interactive map. Pick a category, see what's nearby, open a place for details and save your favourites so they're there next time you open the app.

Built as the exam project for **iOS Programming** (15 ECTS) at Kristiania University College.

<!-- Add 2–3 screenshots here: map with pins, place details, saved places -->

## Features

- **Interactive map** centred on your location (MapKit)
- **Category picker** for cafés, restaurants and hotels
- **Nearby search** through the Geoapify Places API
- **Place details** and a list view of the results
- **Saved places** stored locally with SwiftData, so favourites survive restarts
- **Custom animations** per category (like the steaming coffee cup for cafés)

## Tech stack

| Area | Tools |
| --- | --- |
| Language & UI | Swift, SwiftUI |
| Maps & location | MapKit, CoreLocation |
| Persistence | SwiftData |
| Networking | URLSession with async/await, Codable models |
| Data source | [Geoapify Places API](https://www.geoapify.com/places-api/) |

## Architecture

```
Beacon/
├── MapTab/      Map, category toolbar, results list and place details
├── ListTab/     Saved places list
├── Models/      Category, FeatureCollection (decoded API response), SavedPlace (SwiftData)
├── Service/
│   ├── NetworkClient    Generic request/decoding layer
│   ├── DataService      Builds Geoapify queries and returns places
│   └── LocationManager  Wraps CLLocationManager and publishes the user's position
└── MainTabView.swift    Tab bar: map + saved places
```

The views stay focused on layout. Anything that talks to the network or the location APIs lives in `Service/`, and the API response is decoded straight into `Codable` models.

## Getting started

### Prerequisites

- Xcode 26 or newer (the project targets iOS 26)
- A free [Geoapify API key](https://myprojects.geoapify.com/)

### Run it

```bash
git clone https://github.com/breadbakerlevi/beacon.git
cd beacon
open Beacon.xcodeproj
```

1. Open `Beacon/Service/DataService.swift` and set `apiKey` to your own Geoapify key
2. Pick a simulator and hit **Run** (⌘R)
3. Allow location access when asked. In the simulator you can set a position under **Features → Location**
