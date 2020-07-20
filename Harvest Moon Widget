--[[												---

			MEAP HARVEST MOON FOMT GUI
		This GUI is made to display events suchas 
	birthday or village events such as Horse Racing
	
	
						CREDITS
				Programmer : MeapMeap
			  V Jasper for the gameshark
	  arashinonatsu for the gift guide and calendar
			  


---													]]--


--Player Input--

--[[
	--How to enter--
	Player's Birthday
	1. Put your season on the first digit (1 : Spring, 2: Summer, 3: Fall, 4: Winter)
	2. Put your date on the second digit
	3. Leave anniversay at 0 if you're not married yet
]]--


local player_birthday={
	1,8
}

local player_anniversary={
	0,0
}

--Initialize variable
local stamina
local fatigue
local dates={}

local seasons={
	"SPRING", "SUMMER", "FALL", "WINTER"
}

--Initialize dates
i1 = 1
tgl = 1
for i=0, 119 do

	dates[i] = string.format("%s %d", seasons[i1], tgl)

	if i1 == 4 then
		i1 = 1
		tgl = tgl+1
	else
		i1 = i1+1
	end
	
end

--Initialize events
local events={}
local playerBirthdayIndex
local playerAnnivIndex

local playerBirthdayString = ""
local playerAnnivString = ""

if player_birthday[1] ~= 0 or player_birthday[2] ~= 0 then
	playerBirthdayString = string.format("%s %d", seasons[player_birthday[1]], player_birthday[2])
end

if player_anniversary[1] ~= 0 or player_anniversary[2] ~= 0 then
	playerAnnivString = string.format("%s %d", seasons[player_anniversary[1]], player_anniversary[2])
end

for i=0, 119 do

	if dates[i] == playerBirthdayString then
		playerBirthdayIndex = i
	end
	
	if dates[i] == playerAnnivString then
		playerAnnivIndex = i
	end
end

if playerBirthdayIndex ~= nil then
	events[playerBirthdayIndex] = "Player's Birthday"
end
if playerAnnivIndex ~= nil then
	if playerAnnivIndex == playerBirthdayIndex then
		events[playerAnnivIndex] = "Player's Birthday\nPlayer's Anniversary"
	else
		events[playerAnnivIndex] = "Player's Anniversary"
	end
end

local eventString

local eventIndexes = {
	0, 12, 28, 40, 52, 56, 60, 64, 68, 72, 80, 84, 100, 116, --spring
	1, 9, 13, 21, 25, 41, 61, 65, 77, 85, 93, 97, 113, --summer
	6, 10, 18, 34, 38, 42, 50, 54, 58, 70, 74, 78, 82, 90, 106, 118, --fall
	7, 23, 43, 51, 55, 59, 75, 79 , 87, 95, 99, 103, 115, 119 -- winter
}

local altIndexes = {
	[28]=32, [60]=76, [80]=76, --spring
	[9]=37, [21]=37, [65]=85, [85]=65, --summer
	[58]=90, [106]=90, [74]=98, --fall
	[75]=83, [23]=91, [79]=99, --winter
	
}

local eventStrings = {
	--Spring--
	"The New Year’s Festival, 6pm - Midnight",
	"Bold's Birthday (Flour)",
	"Harvest Goddess's Birthday\n(Pineapple, Strawberries, Flowers)\nKappa's Birthday (Cucumber)",
	"Saibara's Birthday (Flour)",
	"Spring Thanksgiving Festival (Boys Give Cookies)",
	"Staid's Birthday (Flour)",
	"Elli's Birthday (Moon Dumpling, Hot Milk)",
	"Barley's Birthday (Rice Ball)",
	"The Spring Horse Races, 10am - 6pm",
	"Lilia's Birthday (Bodigizer)",
	"Gourmet's Birthday \n(Elli Leaves, Moon Dumpling, Curry Rice)",
	"The Cooking Festival, 10am - 6pm",
	"Aqua's Birthday (Flour)",
	"Sasha's Birthday (Chocolate)",
	
	--Summer--
	"Beach Day, 10am - 6pm",
	"Popuri's Birthday (Scrambled Egg, Eggs)",
	"Harris's Birthday (Bodigizer)",
	"Cliff's Birthday \n(Curry Rice, Pancake, Chocolate)",
	"The Chicken Festival, 10am - 6pm",
	"Basil's Birthday (Black Grass)",
	"Timid's Birthday (Flour)",
	"Ann's Birthday (Cake, Chocolate)",
	"The Cow Festival, 10am - 6pm",
	"Kai's Birthday (Pineapple, Bread)",
	"The Fireworks Festival, 6pm - 9pm",
	"Thomas's Birthday (Wine)",
	"Zack's Birthday (Curry Rice, Wine)",
	
	--Fall--
	"Gotz's Birthday (Flour)",
	"Music Festival, 6pm - Midnight",
	"Stu's Birthday (Honey)",
	"The Harvest Festival, 10am - 6pm",
	"Hoggy's Birthday (Flour)",
	"Manna's Birthday (Honey)",
	"The Full Moon Festival, 6pm - Midnight",
	"Chef's Birthday (Flour)",
	"Karen's Birthday \n(French Fries, Pop Corn, Wine)",
	"The Autumn Horse Races, 10am - 6pm",
	"Doctor's Birthday (Milk, Egg)",
	"Carter's Birthday (Flour)",
	"The Sheep Festival, 10am - 6pm",
	"Anna's Birthday (Flour)",
	"Rick's Birthday (Spa Egg, Eggs)",
	"Pumpkin Festival (Give Chocolate To Children), 6am - 11am",
	
	--Winter--
	"Thomas’ Request, 6am - 0am and 7pm - 0pm",
	"Gray's Birthday (Baked Corn)",
	"Doug's Birthday (Black Grass)",
	"Ellen's Birthday (Flour)",
	"Winter Thanksgiving Festival (Girls Give Chocolate)",
	"Duke's Birthday (Wine, Bread)",
	"Won's Birthday (Gold Ore)",
	"Mary's Birthday \n(Veggie Juice, Black Grass)",
	"Nappy's Birthday (Flour)",
	"The Starry Night Festival (with friend), 6pm - 9pm\nThe Starry Night Festival (with spouse), Noon - Midnight",
	"The Stocking Festival (Go to bed between 9pm - Midnight)",
	"May's Birthday (Honey)",
	"Jeff's Birthday (Bodigizer)",
	"The New Year's Eve Festival (Noodles), 6pm - Midnight\nThe New Year's Eve Festival (Sunrise), Midnight - 6am",
}

local eventString

for i,e in ipairs(eventIndexes) do
	
	eventString = eventStrings[i]
	
	if altIndexes[e] ~= nil and playerBirthdayIndex == e then
		if events[altIndexes[e]] ~= nil then
			events[altIndexes[e]] = string.format("$s\n$s", events[altIndexes[e]], eventString)
		else
			events[altIndexes[e]] = eventString
		end
	else
		if events[e] ~= nil then
			events[e] = string.format("$s\n$s", events[e], eventString)
		else
			events[e] = eventString
		end
	end
end

--Execute each frame advance
while true do

	--initialize variable
	stamina = memory.readbyteunsigned(0x02006A29)
	fatigue = memory.readbyteunsigned(0x02006A2A)
	
	--gui text update
	gui.text(180,2,string.format("Stamina: %d", stamina))
	gui.text(180,10,string.format("Fatigue: %d", fatigue))
	
	errorBool = false
	
	if dates[memory.readbyteunsigned(0x02004E1D)] ~= nil then
		dateString = dates[memory.readbyteunsigned(0x02004E1D)]
	else
		dateString = "Error, please restart & reload your game"
		errorBool = true
	end
	
	gui.text(5,2,string.format("Date: %s", dateString))
	if not errorBool then
		event = events[memory.readbyteunsigned(0x02004E1D)]
		--event = dates[4] == playerBirthdayString
		if event == nil then
			event = "No events"
		end
		
		gui.text(5,13,event)
	end
	--r, g, b = gui.getpixel(0,2)
	--gui.text(135,140,string.format("RGB: %d,%d,%d", r,g,b))
	emu.frameadvance()

end