# 🇺🇸 US Cities JSON

A complete, structured JSON dataset of every **state**, **county**, and **city/place** in the United States — free and open for anyone to use.

## 📊 Coverage

| Level | Count |
|---|---|
| States + DC | 51 |
| Counties / County Equivalents | 3,142 |
| Cities / Towns / Places | 33,034 |

## 📁 File

[`us_cities.json`](./us_cities.json) — ~700 KB, no dependencies, no API key required.

## 🗂️ Structure

```json
{
  "StateName": {
    "County Name": [
      "City",
      "Town",
      "Place"
    ]
  }
}
```

### Example

```json
{
  "Alabama": {
    "Baldwin County": [
      "Bay Minette",
      "Daphne",
      "Fairhope",
      "Foley",
      "Gulf Shores",
      "Orange Beach"
    ]
  },
  "California": {
    "Los Angeles County": [
      "Los Angeles",
      "Long Beach",
      "Glendale",
      "Santa Clarita"
    ]
  }
}
```

## 🚀 Usage

### JavaScript / Node.js

```js
const data = require('./us_cities.json');

// Get all counties in Texas
const texasCounties = Object.keys(data['Texas']);

// Get all cities in Travis County, Texas
const travisCities = data['Texas']['Travis County'];

// Get all cities across all states
const allCities = Object.values(data)
  .flatMap(state => Object.values(state).flat());
```

### Python

```python
import json

with open('us_cities.json') as f:
    data = json.load(f)

# Get all counties in California
ca_counties = list(data['California'].keys())

# Get all cities in Cook County, Illinois
cook_cities = data['Illinois']['Cook County']

# Total city count
total = sum(len(city) for state in data.values() for city in state.values())
```

### Fetch from GitHub (browser / frontend)

```js
const res = await fetch(
  'https://raw.githubusercontent.com/gfrancomontero/us-cities-json/main/us_cities.json'
);
const data = await res.json();
```

## 💡 Use Cases

- Address autocomplete / form dropdowns
- Geographic filtering in search UIs
- Data validation for location fields
- Real estate, logistics, and delivery apps
- Research and data science projects
- Seeding databases with US geographic data

## 📋 Notes

- County equivalents (parishes, boroughs, census areas, independent cities) are included under their respective state.
- Place names reflect commonly recognized cities, towns, villages, and census-designated places (CDPs).
- Data covers all 50 states plus the District of Columbia.

## 📄 License

[MIT License](./LICENSE) — free to use, modify, and distribute in personal and commercial projects.

## 👤 Author

**Gonzalo Franco**  
[gonzalofranco.com](https://www.gonzalofranco.com)

---

If this saves you time, consider starring ⭐ the repo!
