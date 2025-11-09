# Pokédex Assets

Public dataset of Pokémon sprites and reference charts for development and testing.

## Overview
This repository contains static files that map each National Pokédex number (1–1025) to a corresponding sprite URL from the [PokeAPI GitHub mirror](https://github.com/PokeAPI/sprites).  
These assets are designed for use in projects that need lightweight graphical or tabular Pokémon references without scraping or API calls.

## Files

### pokedex_sprites_1_1025.csv
A comma-separated file with two columns:
```
pokedex_number,sprite_url
1,https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/1.png
2,https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/2.png
...
1025,https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/1025.png
```
Useful for importing into scripts, dataframes, or databases.

### pokedex_sprites_1_1025.html
An HTML grid displaying all sprites (1–1025) for quick visual reference.  
Open directly in a browser or host via GitHub Pages.

## Usage Examples

### JavaScript
```js
async function loadDex(url) {
  const text = await fetch(url).then(r => r.text());
  const rows = text.trim().split('\n').slice(1).map(line => {
    const [num, sprite] = line.split(',');
    return { num: Number(num), sprite };
  });
  console.log(rows[0]); // { num: 1, sprite: 'https://...' }
}
loadDex('https://raw.githubusercontent.com/Tignome/pokedex-assets/main/pokedex_sprites_1_1025.csv');
```

### Python
```python
import pandas as pd
url = "https://raw.githubusercontent.com/Tignome/pokedex-assets/main/pokedex_sprites_1_1025.csv"
df = pd.read_csv(url)
print(df.head())
```

### HTML grid
Open the HTML file or embed its content directly in your project.  
All images load via standard HTTPS links and require no authentication.

## Source Attribution
Sprite images © Nintendo / Game Freak / The Pokémon Company.  
Sprite hosting provided by [PokeAPI](https://pokeapi.co/).  
This repository is a derivative dataset for educational and development use only.

## License
MIT License applies to the generated data files and HTML layout in this repository.  
Sprites themselves remain under their respective copyright holders.

## Maintainer
Created by Mark Fenner (GitHub: [Tignome](https://github.com/Tignome)).
