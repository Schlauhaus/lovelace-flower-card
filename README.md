# Release

See https://community.home-assistant.io/t/miflora-sensor-plant-database/53131 for more information of this particular MiFlora / Home-Assistant card.
Also see my detailed post in this same thread at https://community.home-assistant.io/t/miflora-sensor-plant-database/53131/73

![](https://github.com/remkolems/lovelace-flower-card/blob/master/lovelace-flower-card_popup.png)

### Disclaimer
I looked into several forks of the original card https://github.com/thomasloven/lovelace-flower-card. Some forks were very interesting and I edited several of those source codes changes into my own new fork. Credits to those original authors.

### Dependencies
1. Plant sensor (https://www.home-assistant.io/integrations/plant)

### Instructions

1: Install the card
  * Ensure HACS is installed.
  * Go to Community -> Frontend -> press the three dots (top right corner of screen) -> Custom repositories and add the following information:
  Add custom repository URL: https://github.com/Yolandavdvegt/lovelace-flower-card
  Category: Lovelace
  Press add.

Press on the just added `Lovelace Flower Card` and press `Install this repository in HACS`

2: Setup card

```yaml
type: custom:flower-card
entity: plant.my_plant
species: "tulipa 'hollandia'"
```

To get a list of the available species run `python3 convert.py DBFilename.csv species`. The value you want is the one after the colon. Enter it exactly like it says, with quotes and all.

3: Place an jpg image with the name of the entity id in the `/config/www/images/plants` directory. Example: `/local/images/plants/tulipa balkon.jpg`. Images of species can be found in the https://github.com/khronimo/MiFloraDB repository readme.

4: configuration.yaml

Add the following to configuration.yaml (bottom of this file)
```plant: !include plants.yaml```

I do this to separate my config files.

5: plants.yaml

Create, edit and add the following to plants.yaml. Change accordingly. Repeat this section for other plants. Separate each section with a blank line.
```
spathiphyllum_bingo_cupido:
  sensors:
    moisture: sensor.spathiphyllum_moisture
    battery: sensor.spathiphyllum_battery
    temperature: sensor.spathiphyllum_temperature
    conductivity: sensor.spathiphyllum_conductivity
    brightness: sensor.spathiphyllum_brightness
```
