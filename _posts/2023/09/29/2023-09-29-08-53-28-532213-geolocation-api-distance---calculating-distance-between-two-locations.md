---
layout: post
title: "Geolocation API distance - calculating distance between two locations"
description: " "
date: 2023-09-29
tags: []
comments: true
share: true
---

In this blog post, we will explore how to use the Geolocation API to calculate the distance between two locations. Whether you are building a ride-hailing app, a food delivery service, or a travel website, knowing the distance between two points is essential for providing accurate information to your users.

## What is the Geolocation API?

The Geolocation API is a web API that allows web developers to access the user's current location. It provides the latitude and longitude coordinates, which can then be used to calculate the distance between two points.

## Calculating Distance using Haversine formula

To calculate the distance between two points on the Earth's surface, we can use the Haversine formula. The Haversine formula takes into account the curvature of the Earth and provides an accurate distance calculation.

```python
import math

def calculate_distance(lat1, lon1, lat2, lon2):
    R = 6371  # Radius of the Earth in kilometers

    # Convert degrees to radians
    lat1 = math.radians(lat1)
    lon1 = math.radians(lon1)
    lat2 = math.radians(lat2)
    lon2 = math.radians(lon2)

    # Haversine formula
    dlon = lon2 - lon1
    dlat = lat2 - lat1
    a = math.sin(dlat / 2) ** 2 + math.cos(lat1) * math.cos(lat2) * math.sin(dlon / 2) ** 2
    c = 2 * math.atan2(math.sqrt(a), math.sqrt(1 - a))

    # Calculate the distance
    distance = R * c
    return distance
```

In the above code, we define a function `calculate_distance` that takes in the latitude and longitude coordinates of two points as parameters. It converts the coordinates from degrees to radians and then applies the Haversine formula to calculate the distance between the two points. The result is returned in kilometers.

## Usage Example

Let's see an example of how we can use the `calculate_distance` function to find the distance between two locations.

```python
lat1 = 37.7749  # Latitude of location 1
lon1 = -122.4194  # Longitude of location 1
lat2 = 34.0522  # Latitude of location 2
lon2 = -118.2437  # Longitude of location 2

distance = calculate_distance(lat1, lon1, lat2, lon2)
print(f"The distance between the two locations is {distance} kilometers.")
```

In the above example, we pass the latitude and longitude coordinates of San Francisco (location 1) and Los Angeles (location 2) into the `calculate_distance` function. The result is then printed, giving us the distance between the two locations.

## Conclusion

The Geolocation API is a powerful tool for accessing the user's location and calculating the distance between two points. By using the Haversine formula, we can accurately calculate the distance, taking into account the curvature of the Earth. This information can be invaluable for a wide range of applications, from navigation to location-based services.