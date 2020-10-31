# DayzXboxConfigTutorial

This is a tutorial to customize a Dayz Server for Xbox. 

I collected this knowledge by being an admin for 6 months and I wanted to make this knowledge public to others, so they can easily know how to customize their servers.

## Table of content
-


## General Config


## Car Related

### How to despawn all cars and make then respawn brand new
In order to make all car, working and broken ones, despawn and respawn brand new :

1. Open the ___event.xml___ file.
2. For each car event you want to despawn (VehicleCivilianSedan, VehicleHatchback02, VehicleOffroadHatchback, VehicleSedan02), change the ___active___ entry to ___0___.
3. Restart your server. 
> This will make all car despawn.

### How to make car non persistant
In order to make car non persistant, by that I mean despawn and respawn after every server restart : 

1. Despawn all cars.
2. Restart your server and stop it. This will make sure your cars will spawn brand new. Not doing this will make car spawn in their last known state. 
3. Open the ___economy.xml___ file.
4. Find the ___vehicules___ tag.
5. Change the ___save___ parameter to ___0___

```xml
<vehicles init="1" load="1" respawn="1" save="0"/>
```
