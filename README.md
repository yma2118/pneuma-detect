## 🚦 Urban Traffic Flow Analysis with piNEUMA and OpenStreetMap
This project analyzes traffic activity in Athens by integrating the piNEUMA vehicle trajectory dataset with OpenStreetMap (OSM) infrastructure data. Our goal was to uncover active intersections and road segments, label and structure them, and compute traffic-related statistics such as average speed, vehicle counts, and turning ratios.
This initiative was conducted as part of a collaborative effort under Professor Qi Gao guidance. The project involved data cleaning, spatial mapping, and graph-based modeling using Python and Jupyter Notebooks.

## 🧠 How We Tackled This Project

The project evolved in several structured stages, blending geographic data processing with vehicle analysis:

## 🗂️ Step 1: Understanding and Preparing the Data

We began by examining the piNEUMA dataset, which contains high-resolution GPS traces of vehicles across Athens. The initial .csv format was dense and hard to parse, so we planned a conversion to .json format. This allowed a more hierarchical structure to represent each vehicle's journey, including fields such as:

track_id, type, traveled_d, avg_speed

Lists of lat, lon, speed, acceleration, and timestamps

This transformation made it easier to analyze movement patterns.

## 🧭 Step 2: Integrating OpenStreetMap (OSM)

To understand the underlying road infrastructure, we used OpenStreetMap, accessed through the osmnx Python library. This allowed us to:

Download the full road network of Athens

Extract geometries of roads, nodes (intersections), and connectivity information

Using this, we filtered out only the intersections and segments that were covered by piNEUMA vehicles — those where vehicle traces overlapped with the OSM road geometry. This gave us a structured view of the active road network.

We then organized this into two dictionaries:

Intersections: with lat, lon, and connected_roads

RoadSegments: with polyline coords and connected_intersections

## 🔁 Step 3: Mapping Vehicles to Roads

Each vehicle trace from piNEUMA was spatially mapped onto the OpenStreetMap network. This was done by computing spatial proximity between GPS points and road geometries from OSM. Once matched, we could associate each trace to a specific road segment or intersection.

## 📉 Step 4: Computing Segment-Level Statistics

With vehicles assigned to road segments, we calculated useful metrics per segment:

-Average speed

-Vehicle count

-Density of flow

These insights allow us to understand traffic performance at different segments of the city.

## 🔄 Step 5: Turning Ratios (WIP)

The final stage involves calculating turning ratios at intersections — i.e., estimating the likelihood of vehicles turning from one connected road to another. This requires analyzing sequences of GPS points and transitions between intersecting road segments. Further refinements will be addressed in future work.

## Roadmap to the future
-Clean and refine the road-to-vehicle matching

-Make traffic data easier to explore (maybe with a simple dashboard)

-Try applying the same method in a different city
