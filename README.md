# DayzXboxConfigTutorial

## Table of content
-


## General Config


## Car Related

### How to make car non persistant
In order to make car non persistant, by that I mean despawn and respawn after every server restart : 

1- Despawn all cars.
2- Restart your server and stop it. This will make sure your cars will spawn brand new. Not doing this will make car spawn in their last known state. 
3- Open the ___economy.xml___ file.
4- Find the ___vehicule___ tag.
5- Change the ___save___ parameter to ___0___

```xml
<vehicles init="1" load="1" respawn="1" save="0"/>
```
