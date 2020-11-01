# DayzXboxConfigTutorial

This is a tutorial to customize a Dayz Server for Xbox. 

I collected this knowledge by being an admin for 6 months and I wanted to make this knowledge public to others, so they can easily know how to customize their servers.

## Table of content
- [General Configurations](#global-configurations)
- [Car related configurations](#car-related-configurations)


## Global configurations

### Change the despawn timer of things in the world
ruined items, dead players, animals and dead zombies despawn timer can be changed. 
1. Open the ___Globals.xml___ file.
2. Find the appropriate tag you want to change :
```xml
    <var name="CleanupLifetimeDeadAnimal" type="0" value="1200"/>
    <var name="CleanupLifetimeDeadInfected" type="0" value="330"/>
    <var name="CleanupLifetimeDeadPlayer" type="0" value="3600"/>
    <var name="CleanupLifetimeDefault" type="0" value="45"/>
    <var name="CleanupLifetimeLimit" type="0" value="3600"/>
    <var name="CleanupLifetimeRuined" type="0" value="330"/>
```
3. Change the ___value___ attribute of the item you want 
> Values are in seconds. Here ___3600___ means it is a ___60 seconds per minute X 60 minutes___ = ___1 hour___
4. Save the file and restart the server.

### Change the numbre on items found on the map
Dayz limits the number of items you can find on the map to ___1200___. You can change this value, but be warn it can affect the server performance.
1. Open the ___Globals.xml___ file.
2. Find the ___SpawnInitial___ tag :
```xml
<var name="SpawnInitial" type="0" value="1200"/>
```
3. Change the ___value___ attribute of the number of items you want to spawn on the map.
4. Save the file and restart the server.

### Change the number of zombies on the map

Dayz limits the number of zombies players can encounters on the map to ___800___. You can change this value, but be warn it can affect the server performance.
1. Open the ___Globals.xml___ file.
2. Find the ___ZombieMaxCount___ tag :
```xml
<var name="ZombieMaxCount" type="0" value="800"/>
```
3. Change the ___value___ attribute of the number of zombies you want on the map.
4. Save the file and restart the server.

## Car related configurations

### Car types
Dayz for xbox has only 4 car types : 
- VehicleCivilianSedan
- VehicleHatchback02 
- VehicleOffroadHatchback
- VehicleSedan02
Others like the VS3 truck and the bus are non functionnal.

### How to spawn more cars
In order to spawn more cars :
1. Open the ___event.xml___ file.
2. Find the event of the car you want to spawn more (VehicleCivilianSedan, VehicleHatchback02, VehicleOffroadHatchback, VehicleSedan02).
```xml
<event name="VehicleOffroadHatchback">
        <nominal>4</nominal>
        <min>1</min>
        <max>8</max>
        <lifetime>300</lifetime>
        <restock>0</restock>
        <saferadius>500</saferadius>
        <distanceradius>500</distanceradius>
        <cleanupradius>200</cleanupradius>
        <flags deletable="0" init_random="0" remove_damaged="1"/>
        <position>fixed</position>
        <limit>mixed</limit>
        <active>1</active>
        <children>
            <child lootmax="0" lootmin="0" max="15" min="3" type="OffroadHatchback"/>
            <child lootmax="0" lootmin="0" max="15" min="3" type="OffroadHatchback_Blue"/>
            <child lootmax="0" lootmin="0" max="15" min="3" type="OffroadHatchback_White"/>
        </children>
    </event>
```
3. Change the ___min___, ___max___ and ___nominal___ tags to the values you want.
- ___min___ is the minimum number of this type of car you want on the map.
- ___max___ is the maximum number of this type of car you want on the map.
- ___nominal___ is the average number of this type of car you want on the map.

```xml
<event name="VehicleOffroadHatchback">
        <nominal>20</nominal>
        <min>10</min>
        <max>30</max>
        <lifetime>300</lifetime>
        <restock>0</restock>
        <saferadius>500</saferadius>
        <distanceradius>500</distanceradius>
        <cleanupradius>200</cleanupradius>
        <flags deletable="0" init_random="0" remove_damaged="1"/>
        <position>fixed</position>
        <limit>mixed</limit>
        <active>1</active>
        <children>
            <child lootmax="0" lootmin="0" max="15" min="3" type="OffroadHatchback"/>
            <child lootmax="0" lootmin="0" max="15" min="3" type="OffroadHatchback_Blue"/>
            <child lootmax="0" lootmin="0" max="15" min="3" type="OffroadHatchback_White"/>
        </children>
    </event>
```
4. Save the file and restart the server.

### How to despawn all cars and make then respawn brand new
In order to make all car, working and broken ones, despawn and respawn brand new :

1. Open the ___event.xml___ file.
2. For each car type you want to despawn find the corresponding event, for example : 
```xml
<event name="VehicleOffroadHatchback">
```

3.change the ___active___ tag to ___0___.
```xml
<event name="VehicleOffroadHatchback">
        <nominal>40</nominal>
        <min>20</min>
        <max>70</max>
        <lifetime>300</lifetime>
        <restock>0</restock>
        <saferadius>500</saferadius>
        <distanceradius>500</distanceradius>
        <cleanupradius>200</cleanupradius>
        <flags deletable="0" init_random="0" remove_damaged="1"/>
        <position>fixed</position>
        <limit>mixed</limit>
        <active>0</active>
        <children>
            <child lootmax="0" lootmin="0" max="15" min="3" type="OffroadHatchback"/>
            <child lootmax="0" lootmin="0" max="15" min="3" type="OffroadHatchback_Blue"/>
            <child lootmax="0" lootmin="0" max="15" min="3" type="OffroadHatchback_White"/>
        </children>
    </event>
```
4. Save the file and restart your server. 
> This will make all car despawn.
5. For each car event you changed in the ___event.xml___ file, change back the ___active___ tag to ___1___.
```xml
<event name="VehicleOffroadHatchback">
        <nominal>40</nominal>
        <min>20</min>
        <max>70</max>
        <lifetime>300</lifetime>
        <restock>0</restock>
        <saferadius>500</saferadius>
        <distanceradius>500</distanceradius>
        <cleanupradius>200</cleanupradius>
        <flags deletable="0" init_random="0" remove_damaged="1"/>
        <position>fixed</position>
        <limit>mixed</limit>
        <active>1</active>
        <children>
            <child lootmax="0" lootmin="0" max="15" min="3" type="OffroadHatchback"/>
            <child lootmax="0" lootmin="0" max="15" min="3" type="OffroadHatchback_Blue"/>
            <child lootmax="0" lootmin="0" max="15" min="3" type="OffroadHatchback_White"/>
        </children>
    </event>
```
6. Save the file and restart your server. 
> All cars should know respawn as brand new one.

### How to make cars non persistant
In order to make car non persistant, by that I mean despawn and respawn after every server restart : 

1. Despawn all cars.
> This is to make sure your cars will spawn as brand new one. 
> Not doing this will make car spawn in their last known state. 
3. Open the ___economy.xml___ file.
4. Find the ___vehicules___ tag.
5. Change the ___save___ parameter to ___0___

```xml
<vehicles init="1" load="1" respawn="1" save="0"/>
```
6. Save the file and restart your server.

### How to spawn fully built cars
Cars in dayz spawn with random ___attachments___, in order to make then always fully built :

1. Open the file ___cfgspawnabletypes.xml___.
2. Find the entry for the car type you want fully built, for example : 
```xml
<type name="OffroadHatchback">
```
3.For each ___attachments___ tag, change the ___chance___ attribute value to ___1.00___ and also for the following ___item___ tag change the chance attribute value to ___1.00___
```xml
<type name="OffroadHatchback">
		<attachments chance="1.00">
			<item name="HatchbackWheel" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="HatchbackWheel" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="HatchbackWheel" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="HatchbackWheel" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="HatchbackWheel" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="CarRadiator" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="CarBattery" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="SparkPlug" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="HeadlightH7" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="HeadlightH7" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="HatchbackDoors_Driver" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="HatchbackDoors_CoDriver" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="HatchbackHood" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="HatchbackTrunk" chance="1.00" />
		</attachments>
        </type>
```
4. Save the file and restart your server.

### How to add items in cars
Cars can spawn with cargo in them, for example you may want to provide canteen of water and fuel to your players so they can fill their brand new car.
1. Open the file ___cfgspawnabletypes.xml___.
2. Find the entry for the car type you want to add items, for example : 
```xml
<type name="OffroadHatchback">
```
3. Add an attachement tag for each item you want to add in the cars. Remember a car can hold a maximum of 300 slots. For example: 
```xml
	<type name="OffroadHatchback">
		<!-- Car parts attachments goes here -->
		<attachments chance="1.00">
			<item name="Canteen" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="Canteen" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="Canteen" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="Canteen" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="CanisterGasoline" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="EpoxyPutty" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="EpoxyPutty" chance="1.00" />
		</attachments>
		<attachments chance="1.00">
			<item name="TacticalBaconCan" chance="1.00" />
		</attachments>
	</type>
```
4. Save the file and restart your server.

### How to make your car fly
Yes Dayz can have flying cars !!!

1. Make your server 70 slots.
2. Become very popular so that your server has more than 60 players.
3. Drive a car. 
> Dayz servers become very laggy when there are more thant 60 players playing, this makes car undrivable and sometimes makes them go off in the air. 
