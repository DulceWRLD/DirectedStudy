# ETS 6 Man In The Middle Attack
A detailed walkthrough on how to use ETS 6 in order to control a home automation system that communicates via KNX
## SETUP
Connect your knx/ip interface

Start up ETS

Make the project by hitting the button that says "+New Project"

You should now see a screen to make your project

Make sure the settings are the same as this screen:
<img src= "/Tutorial/Images/ProjectScreen.png">

## ADDING THE NECCESITIES
Adding Building Parts:

In order to add a building part, right click on your project and navigate to where it says add

You should now see another meu that has an option called "Building Parts"

The menus should look like this:
<img src= "/Tutorial/Images/AddingBuildingParts.png">

You should now see a pop up that looks like this:
<img src= "/Tutorial/Images/BuildingPartsPopUp.png">

Here you can enter the name of your Building Part

Hit ok

Adding a floor:

In order to add a floor, right click on the building and navigate to where it says add

You should now see another menu that has an option called "Floors". Click on that

This is what the menus should look like:
<img src= "/Tutorial/Images/AddingFloors.png">
 
You should now see a pop up that looks like this:
<img src= "/Tutorial/Images/AddingFloorsPopUp.png">

Here you can enter the name of your floor

Hit ok

Now to add a room:

In order to add a room, right click on the floor and navigate to where it says add

You should now see another menu that has an option called "Rooms". Click on that

This is what the menus should look like:
<img src= "/Tutorial/Images/AddingRooms.png">

You should now see a pop up that looks like this:
<img src= "/Tutorial/Images/AddingRoomsPopUp.png">

Here you can enter the name of your room

Hit ok

## ADDING YOUR DEVICES:
Right click on the room and navigate to where it says add

You should now see another menu that has an option called "Devices". Click on that

This is what the menus should look like:
<img src= "/Tutorial/Images/AddingDevices.png">

Now it should pop up with a list of devices that look like this:
<img src= "/Tutorial/Images/DevicesList.png">

Adding the Actuator:

Navigate to Siemens HVAC -> Heating, Ventilation, Air Conditioning -> Actuators

This is what you should see:
<img src= "/Tutorial/Images/Actuator.png">

Now, click on GDB111.9E/KN

Adding the Presence detector:

Navigate to Siemens -> physical sensors

Click on Presence detector, brightness sensor up 268D12

Adding the Temparature sensor:

Navigate to Siemens HVAC -> Heating, Ventilation, Air Conditioning

Click on QMX3 P37 Room unit

Finally, the USB interface:

Navigate to Siemens -> Comm -> Serial USB->N-Devices

Click on USB interface N 148/12

Once your done adding all your devices, it should look something like this:
<img src= "/Tutorial/Images/ImportedDevices.png">

Make sure the actuator is at individual address 1.1.1, the temperature sensor is at address 1.1.4, the presence detector is at 1.1.7 and the usb interface is at 1.1.120

Refer to the image of all the devices and make sure your devices have the same addresses

##ADDING the Group Addresses
In order to add a group address, navigate to the Group Addresses section in the menu

The menu should look like this:
<img src= "/Tutorial/Images/GroupAddressMenu.png">

Next, you add your main group.

This is done by right clicking on the Group Addresses bar

Next click on the option that says "Add Main Groups"

You should see this before clicking:
<img src= "/Tutorial/Images/MainGroupAddress.png">

You should now get a pop up that looks like this:
<img src= "/Tutorial/Images/MainGroupAddressPopUp.png">

Fill it out with the name you want to give it

NExt, you add your middle group by right clicking on the main group and hitting the option that says "Add Middle Groups"

The fill out the menu with the name you want

Add a middle group called temperature sensor aa your first group object at 0/0

Next, add a middle group called placeholder, this is a placeholder of an old device we no longer have

Next, add a middle group called presence detector, this will be at 0/2

Next, add another placeholder

Finally, add a middle group called actuator at 0/4

Now, time to add your group addresses:

Right click on the the middle group you want to add your group address to

Click the option that says "Add Group Addresses"

This is what the menu should look like:
<img src= "/Tutorial/Images/GroupAddress.png">

Once you click, you should see a pop up that looks like this:

<img src= "/Tutorial/Images/GroupAddressPopUp.png">

Repeat this process until your list of Group Addresses looks like this:
<img src= "/Tutorial/Images/FinalizedGroupAddresses.png">

##ADDING THE GROUP OBJECTS TO THE GROUP ADDRESSES
FIrst, click on the group address you are adding the group address for

Next, navigate on the upper area to the device that has the same name as the middle group the group address is under

Now, click on the device and you should see a list of group objects

This is what you should see:
<img src= "/Tutorial/Images/GroupObjects.png">

Take the group object with the same name as the group address, drag it down to the group address and drop it there

Keep doing this until all the group addresses have a group object

##EXECUTING THE FIRST ATTCK
Navigate to the menu and click on it, naviagte to the diagnostics section

This is what you should see:
<img src= "/Tutorial/Images/Diagnostics.png">

Click on the Group Monitor section

Now, to execute the first attack:

In the Group Address field, enter the Group Address for setpoint cooling, 0/4/2

Now click on the data point type and naviagte to 5.001 percentage

This is what you should see:
<img src= "/Tutorial/Images/PercentageValuePopUp.png">

Now enter 0 for the percentage

Now click on the write button to execute your attack

This is what it should look like when you click it:
<img src= "/Tutorial/Images/Write.png">

Now this is what the results of the attack should look like on the monitor:
<img src= "/Tutorial/Images/Attack1Retult.png">

You should also see the actuator moving slowly

If it isn't moving then it is already at the 0 position. Change the percentage to 90 and run it again

##EXECUTING THE SECOND ATTACK
Navigate to the temperature sensor and right click it

There should be a button called Restart Device

This is what the menu should look like:
<img src= "/Tutorial/Images/Attack2.png">

Click on the restart device button

Now, you should see this in the group monitor to tell it's working:
<img src= "/Tutorial/Images/Attack2Result.png">

##EXECUTING THE THIRD ATTACK
Navigate to the Individual Address Check section

It should look like this:
<img src= "/Tutorial/Images/IndividualAddressCheck.png">

Now, enter the indnividual address 1.1.7

This is what you shbould see:
<img src= "/Tutorial/Images/Attack3.png">

Now hit the flash button to see the presence detector flashing

You can also restart the presence detector by doing the same thing as in attack 2 but for the presence detector

Once the detector turns on, you should see it flashing indicating you have succesfully restarted it

Those are all the attacks we did

Here is a demo of all of the attack being executed together:

https://youtu.be/cWh1C1_epDs
