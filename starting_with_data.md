# Question 1: Which products do people spend the most time on the site for? 

## SQL Queries:
```sql
-- Question 1: Which products do people spend the most time on the site for on avg? 

SELECT	 
		products.name
		, prodcategoryV2
		, ROUND(time_on_site_avg, 2)
FROM
	(SELECT
		 prodnameV2
		, prodcategoryV2
		, sessions_prod_SKU
		, avg(time_on_site) AS time_on_site_avg
	FROM 
		(
		SELECT 
			a3.visitid AS anlytics_visitid
			, sessions.visitid AS sessions_visitid
			, a3.timeonsite AS time_on_site
			, sessions.v2productname AS prodnameV2
			, sessions.v2productcategory AS prodcategoryV2
			, sessions.productsku AS sessions_prod_SKU
		FROM analytics_clean3 AS a3
		JOIN all_sessions_clean3 AS sessions
		ON a3.visitid = sessions.visitid 
		WHERE a3.timeonsite IS NOT NULL	
		) AS subq1
	GROUP BY sessions_prod_SKU, prodnameV2, prodcategoryV2
	ORDER BY avg(time_on_site) DESC ) AS subq2
JOIN products
ON sessions_prod_SKU = products."SKU"
GROUP BY  prodcategoryV2, products.name,time_on_site_avg
ORDER BY time_on_site_avg DESC
```


## Answer: 
(expand)
```sql
" Baby Essentials Set"	"Home/Apparel/Kid's/Kid's-Infant/"	3020.00
" Women's 3/4 Sleeve Baseball Raglan Heather/Black"	"${escCatTitle}"	1860.00
" Women's Performance Full Zip Jacket Black"	"(not set)"	1710.00
" Learning Thermostat 3rd Gen-USA - Copper"	"(not set)"	1498.00
" Water Resistant Bluetooth Speaker"	"Home/Electronics/Audio/"	1390.00
"Rubber Grip Ballpoint Pen 4 Pack"	"Home/Office/"	1202.11
" Bib White"	"Home/Apparel/Kid's/"	1189.29
" Laptop and Cell Phone Stickers"	"Home/Shop by Brand/"	1108.00
"Android RFID Journal"	"Home/Shop by Brand/Android/"	1028.36
" Women's Recycled Fabric Tee"	"Home/Apparel/Women's/Women's-T-Shirts/"	1013.03
"Switch Tone Color Crayon Pen"	"Home/Office/"	1001.72
" Tube Power Bank"	"Home/Electronics/"	956.29
"25L Classic Rucksack"	"Home/Bags/Backpacks/"	951.37
" Learning Thermostat 3rd Gen-USA - Stainless Steel"	"Nest-USA"	943.00
" Women's Short Sleeve Hero Tee Black"	"(not set)"	919.00
" Kick Ball"	"Home/Accessories/Sports & Fitness/"	876.00
" Women's Vintage Hero Tee Platinum"	"Home/Apparel/Women's/Women's-T-Shirts/"	809.20
"SPF-15 Slim & Slender Lip Balm"	"Housewares"	800.00
"Android Lunch Kit"	"Home/Accessories/"	798.00
" Custom Decals"	"(not set)"	792.00
"22 oz Android Bottle"	"Home/Drinkware/"	784.52
"Android Twill Cap"	"Home/Apparel/"	779.20
"20 oz Stainless Steel Insulated Tumbler"	"Home/Drinkware/"	774.71
" Blackout Cap"	"Home/Apparel/Headgear/"	771.00
"Android Men's Vintage Henley"	"Home/Shop by Brand/Android/"	760.12
"Basecamp Explorer Powerbank Flashlight"	"Home/Electronics/"	750.12
" 5-Panel Snapback Cap"	"Home/Apparel/Headgear/"	739.47
"Waterproof Backpack"	"Home/Shop by Brand/"	724.33
"8 pc Android Sticker Sheet"	"Home/Office/"	718.16
" 17 oz Double Wall Stainless Steel Insulated Bottle"	"Home/Drinkware/"	709.50
"24 oz  Sergeant Stripe Bottle"	"Home/Shop by Brand/YouTube/"	664.70
" Tote Bag"	"Home/Bags/Shopping and Totes/"	652.41
"Pen Pencil & Highlighter Set"	"Home/Office/Writing Instruments/"	648.06
"Collapsible Shopping Bag"	"Home/Bags/"	638.71
" Women's Long Sleeve Tee Lavender"	"Home/Apparel/Women's/Women's-T-Shirts/"	635.00
" Women's Convertible Vest-Jacket Sea Foam Green"	"Home/Apparel/Women's/Women's-Outerwear/"	621.91
" Men's 100% Cotton Short Sleeve Hero Tee White"	"Home/Apparel/"	602.55
" Men's Airflow 1/4 Zip Pullover Lapis"	"Home/Apparel/Men's/Men's-Performance Wear/"	602.00
" Bongo Cupholder Bluetooth Speaker"	"Home/Electronics/Audio/"	597.18
"Android Men's Long Sleeve Badge Crew Tee Heather"	"Home/Apparel/Men's/Men's-T-Shirts/"	592.35
"Android Stretch Fit Hat Black"	"Home/Apparel/Headgear/"	584.00
" Twill Cap"	"Home/Apparel/"	539.65
"Clip-on Compact Charger"	"Home/Electronics/"	535.42
" Lunch Bag"	"Home/Bags/"	532.21
" Cam Indoor Security Camera - USA"	"Home/Nest/Nest-USA/"	528.48
"Android Luggage Tag"	"Home/Shop by Brand/Android/"	526.53
"26 oz Double Wall Insulated Bottle"	"Home/Drinkware/Water Bottles and Tumblers/"	521.11
"Yoga Block"	"Home/Accessories/"	514.27
"1 oz Hand Sanitizer"	"Home/Office/"	495.01
"Red Shine 15 oz Mug"	"Home/Drinkware/Mugs and Cups/"	492.00
"Spiral Notebook and Pen Set"	"(not set)"	491.00
"Red Shine 15 oz Mug"	"Home/Drinkware/"	491.00
" Vintage Henley Grey/Black"	"Home/Apparel/Men's/Men's-T-Shirts/"	490.85
"Suitcase Organizer Cubes"	"Home/Bags/"	490.49
" Men's Vintage Badge Tee White"	"Home/Apparel/Men's/Men's-T-Shirts/"	489.82
"Android Hard Cover Journal"	"Home/Shop by Brand/Android/"	485.68
" Mood Original Window Decal"	"Home/Accessories/Stickers/"	473.83
"Android 17oz Stainless Steel Sport Bottle"	"Home/Drinkware/"	464.54
" Men's Short Sleeve Hero Tee Charcoal"	"Home/Shop by Brand/YouTube/"	456.07
"Foam Can and Bottle Cooler"	"Home/Drinkware/"	452.56
" 5-Panel Snapback Cap"	"Home/Apparel/"	452.34
" Tri-blend Hoodie Grey"	"(not set)"	450.00
"Android Women's Short Sleeve Hero Tee Black"	"Home/Apparel/Women's/Women's-T-Shirts/"	442.00
" Lunch Bag"	"Home/Bags/More Bags/"	440.00
" Dress Socks"	"Home/Apparel/"	438.71
"Windup Android"	"Home/Shop by Brand/"	434.31
"23 oz Wide Mouth Sport Bottle"	"(not set)"	434.00
" Laptop and Cell Phone Stickers"	"Home/Accessories/Stickers/"	431.30
"Electronics Accessory Pouch"	"Home/Electronics/"	419.47
" Lunch Bag"	"Home/Accessories/Housewares/"	414.10
" Water Resistant Bluetooth Speaker"	"Home/Electronics/"	409.65
"Metal Texture Roller Pen"	"Home/Spring Sale!/"	407.00
" Car Clip Phone Holder"	"Home/Shop by Brand/Google/"	404.18
"Android Sticker Sheet Ultra Removable"	"Home/Accessories/"	400.52
" Car Clip Phone Holder"	"Home/Accessories/Housewares/"	395.00
"Suitcase Organizer Cubes"	"Home/Accessories/"	392.69
" Men's Vintage Badge Tee Sage"	"Apparel"	391.00
"Rocket Flashlight"	"Home/Electronics/"	390.11
"Android Spiral Journal with Pen"	"Home/Office/"	389.56
" Tote Bag"	"Home/Bags/"	389.25
" 4400mAh Power Bank"	"Home/Electronics/Power/"	389.00
" Women's Vintage Hero Tee Lavender"	"Home/Apparel/Women's/"	382.89
" Wool Heather Cap Heather/Black"	"Home/Shop by Brand/YouTube/"	382.52
"Android Luggage Tag"	"Home/Accessories/Housewares/"	380.68
" 5-Panel Cap"	"Home/Apparel/"	376.59
"Android Men's Vintage Henley"	"Home/Apparel/Men's/"	369.00
"Android Wool Heather Cap Heather/Black"	"Home/Shop by Brand/Android/"	363.65
" Stylus Pen w/ LED Light"	"Home/Shop by Brand/Google/"	362.37
" Pocket Bluetooth Speaker"	"Home/Electronics/Audio/"	360.54
" Laptop Backpack"	"Home/Bags/Backpacks/"	358.52
" Twill Cap"	"Home/Apparel/"	353.65
" Men's Vintage Badge Tee Sage"	"Home/Apparel/Men's/"	353.00
" Infant Short Sleeve Tee Red"	"Home/Apparel/Kid's/Kid's-Infant/"	347.96
"Seat Pack Organizer"	"Home/Office/"	345.00
"Android Men's Engineer Short Sleeve Tee Charcoal"	"Home/Apparel/Men's/Men's-T-Shirts/"	344.43
"Bottle Opener Clip"	"Home/Drinkware/"	343.33
" Women's 1/4 Zip Jacket Charcoal"	"(not set)"	343.00
" Men's Vintage Badge Tee Black"	"Home/Apparel/Men's/Men's-T-Shirts/"	339.23
" Laptop and Cell Phone Stickers"	"Home/Office/"	338.28
" Protect Smoke + CO White Wired Alarm-USA"	"Home/Nest/Nest-USA/"	336.70
" Flashlight"	"Home/Electronics/"	332.04
"Micro Wireless Earbud"	"Home/Electronics/"	325.36
"Android Hard Cover Journal"	"(not set)"	325.00
" Infant Zip Hood Pink"	"Home/Apparel/Kid's/"	324.00
" Twill Cap"	"Home/Apparel/Headgear/"	323.54
" Alpine Style Backpack"	"Home/Bags/"	322.60
" Women's Short Sleeve Hero Tee Black"	"Home/Apparel/Women's/Women's-T-Shirts/"	320.36
"22 oz Android Bottle"	"Home/Shop by Brand/Android/"	318.00
" Bib Red"	"Home/Apparel/"	317.83
"Waterproof Backpack"	"Home/Shop by Brand/Google/"	316.00
" Luggage Tag"	"Home/Shop by Brand/YouTube/"	313.84
" 17 oz Double Wall Stainless Steel Insulated Bottle"	"Home/Drinkware/Water Bottles and Tumblers/"	311.42
" Cam Outdoor Security Camera - USA"	"Home/Nest/Nest-USA/"	310.27
" Slim Utility Travel Bag"	"Home/Bags/"	308.83
" Luggage Tag"	"Home/Accessories/Fun/"	307.42
" Women's Short Sleeve Hero Tee White"	"(not set)"	307.00
" Learning Thermostat 3rd Gen-USA - Stainless Steel"	"Home/Nest/Nest-USA/"	304.32
" 5-Panel Cap"	"Home/Apparel/Headgear/"	302.00
"Windup Android"	"Home/Accessories/"	300.83
" Women's Short Sleeve Hero Tee Sky Blue"	"Home/Apparel/Women's/Women's-T-Shirts/"	300.07
"Windup Android"	"Home/Accessories/Fun/"	299.34
" 17oz Stainless Steel Sport Bottle"	"Home/Drinkware/Water Bottles and Tumblers/"	296.40
" 2200mAh Micro Charger"	"Home/Electronics/"	293.00
"Sport Bag"	"Home/Bags/"	290.43
" Men's Performance Full Zip Jacket Black"	"Home/Apparel/Men's/Men's-Outerwear/"	289.00
"Leatherette Journal"	"Home/Office/Notebooks & Journals/"	287.00
" Hard Cover Journal"	"Home/Shop by Brand/YouTube/"	286.90
"Seat Pack Organizer"	"Home/Accessories/"	278.37
"Windup Android"	"Home/Shop by Brand/Android/"	277.35
" Doodle Decal"	"Home/Office/"	269.16
" Men's Vintage Tank"	"Home/Apparel/Men's/"	267.43
" Blackout Cap"	"(not set)"	266.00
" Wool Heather Cap Heather/Black"	"(not set)"	266.00
"Android Stretch Fit Hat"	"(not set)"	266.00
" Men's Vintage Badge Tee White"	"Apparel"	258.00
" Women's Short Sleeve Performance Tee Charcoal"	"Home/Apparel/Women's/Women's-Performance Wear/"	258.00
"22 oz  Bottle Infuser"	"Home/Drinkware/"	258.00
" Laptop and Cell Phone Stickers"	"Home/Shop by Brand/Google/"	255.99
" Women's Short Sleeve Hero Dark Grey"	"Home/Apparel/Women's/Women's-T-Shirts/"	255.00
" Men's Airflow 1/4 Zip Pullover Black"	"Home/Apparel/Men's/Men's-Performance Wear/"	254.00
" Women's Vintage Hero Tee Black"	"Home/Apparel/Women's/"	253.00
" Men's Vintage Tank"	"Home/Apparel/Men's/Men's-T-Shirts/"	251.87
"24 oz  Sergeant Stripe Bottle"	"Home/Drinkware/"	247.00
" Men's 3/4 Sleeve Henley"	"Home/Apparel/Men's/Men's-T-Shirts/"	242.23
"Android Rise 14 oz Mug"	"Home/Drinkware/Mugs and Cups/"	241.31
"Android Hard Cover Journal"	"Home/Office/Notebooks & Journals/"	240.55
" Women's Tee Grey"	"Home/Apparel/Women's/Women's-T-Shirts/"	237.42
" 22 oz Water Bottle"	"Drinkware"	236.00
" Women's Yoga Jacket Black"	"(not set)"	235.00
"Android Wool Heather Cap Heather/Black"	"Home/Apparel/Headgear/"	233.51
" Canvas Tote Natural/Navy"	"Home/Bags/"	233.33
"Keyboard DOT Sticker"	"Home/Office/"	233.27
" Wool Heather Cap Heather/Black"	"Home/Apparel/"	232.00
"24 oz  Sergeant Stripe Bottle"	"Home/Drinkware/Water Bottles and Tumblers/"	232.00
" Device Holder Sticky Pad"	"(not set)"	231.00
"Android Luggage Tag"	"Home/Accessories/Fun/"	231.00
"Electronics Accessory Pouch"	"Home/Electronics/Electronics Accessories/"	229.00
" Men's Airflow 1/4 Zip Pullover Black"	"Home/Apparel/Men's/Men's-Outerwear/"	228.03
" Men's Fleece Hoodie Black"	"Home/Shop by Brand/YouTube/"	226.00
" Women's Quilted Insulated Vest Black"	"Home/Apparel/Women's/Women's-Outerwear/"	225.20
"Android Onesie Gold"	"Home/Apparel/Kid's/Kid's-Infant/"	224.00
"Plastic Sliding Flashlight"	"Home/Electronics/"	222.46
" Men's Short Sleeve Performance Badge Tee Pewter"	"Home/Apparel/Men's/Men's-Performance Wear/"	222.40
" Doodle Decal"	"Home/Shop by Brand/"	221.00
" Laptop and Cell Phone Stickers"	"(not set)"	217.00
" Slim Utility Travel Bag"	"Home/Bags/More Bags/"	215.00
" Men's Vintage Henley"	"Home/Apparel/Men's/"	214.97
" RFID Journal"	"Home/Clearance Sale/"	212.00
"Android Rise 14 oz Mug"	"Home/Drinkware/"	208.00
"Recycled Mouse Pad"	"Home/Electronics/"	205.56
" Rucksack"	"Home/Bags/Backpacks/"	205.49
"Seat Pack Organizer"	"Home/Accessories/Fun/"	205.00
" Women's Vintage Hero Tee Lavender"	"Home/Apparel/Women's/Women's-T-Shirts/"	204.41
"Android Infant Short Sleeve Tee Pewter"	"Home/Apparel/Kid's/Kid's-Infant/"	204.26
"Android Lunch Kit"	"Home/Shop by Brand/"	204.00
" Men's Pullover Hoodie Grey"	"Home/Apparel/Men's/Men's-Outerwear/"	202.29
" Men's Convertible Vest-Jacket Pewter"	"Home/Apparel/Men's/Men's-Performance Wear/"	199.33
" Snapback Hat Black"	"Home/Shop by Brand/Google/"	197.09
"Android Men's Vintage Tank"	"Home/Apparel/Men's/"	196.94
" Men's 100% Cotton Short Sleeve Hero Tee White"	"Home/Shop by Brand/Google/"	195.59
"Rocket Flashlight"	"Home/Electronics/Flashlights/"	195.31
" Women's Yoga Jacket Black"	"Home/Apparel/Women's/Women's-Performance Wear/"	194.00
" Men's Quilted Insulated Vest Battleship Grey"	"Home/Apparel/Men's/Men's-Outerwear/"	193.86
"Android Rise 14 oz Mug"	"Home/Shop by Brand/"	193.00
" Custom Decals"	"Home/Shop by Brand/YouTube/"	192.15
"8 pc Android Sticker Sheet"	"Home/Accessories/"	188.41
" Mood Happy Window Decal"	"Home/Accessories/Stickers/"	188.00
" Women's Short Sleeve Hero Tee White"	"(not set)"	186.00
" Women's Vintage Hero Tee Black"	"Home/Apparel/Women's/Women's-T-Shirts/"	186.00
" Men's Short Sleeve Hero Tee Charcoal"	"(not set)"	184.71
" Rucksack"	"Home/Shop by Brand/Google/"	184.70
"Android Women's Fleece Hoodie"	"Home/Apparel/Women's/"	183.00
" Men's Quilted Insulated Vest Black"	"(not set)"	182.00
"23 oz Wide Mouth Sport Bottle"	"Home/Drinkware/"	182.00
"Android 17oz Stainless Steel Sport Bottle"	"Home/Drinkware/Water Bottles and Tumblers/"	182.00
" Kick Ball"	"Home/Accessories/Fun/"	181.00
" Hard Cover Journal"	"(not set)"	180.00
"24 oz  Sergeant Stripe Bottle"	"(not set)"	180.00
"1 oz Hand Sanitizer"	"Home/Accessories/"	179.14
" Toddler Short Sleeve Tee Red"	"Home/Shop by Brand/YouTube/"	179.00
" Men's Vintage Badge Tee Sage"	"Home/Apparel/Men's/Men's-T-Shirts/"	178.23
"Android Onesie Gold"	"(not set)"	178.00
" Men's Vintage Henley"	"Home/Shop by Brand/YouTube/"	177.94
" Snapback Hat Black"	"Home/Apparel/"	176.76
" Women's 3/4 Sleeve Baseball Raglan Heather/Black"	"(not set)"	174.33
" Trucker Hat"	"Home/Apparel/"	173.37
" Laptop Backpack"	"(not set)"	173.00
" Men's Short Sleeve Performance Badge Tee Black"	"Home/Apparel/Men's/Men's-Performance Wear/"	172.00
" Rucksack"	"Home/Bags/"	171.00
" Sunglasses"	"Home/Accessories/Fun/"	166.33
"Waterproof Backpack"	"Home/Bags/Backpacks/"	164.00
"Recycled Mouse Pad"	"Home/Electronics/Electronics Accessories/"	163.30
" Men's Pullover Hoodie Grey"	"(not set)"	163.00
" Device Holder Sticky Pad"	"Home/Electronics/Electronics Accessories/"	161.71
"Android Men's  Zip Hoodie"	"(not set)"	159.50
" Women's Short Sleeve Hero Tee Sky Blue"	"(not set)"	158.00
" Men's Short Sleeve Hero Tee Black"	"Home/Shop by Brand/YouTube/"	155.25
" Men's Vintage Tank"	"Home/Shop by Brand/YouTube/"	155.12
"Suitcase Organizer Cubes"	"Home/Office/"	154.54
" Lunch Bag"	"Home/Accessories/"	154.00
"Basecamp Explorer Powerbank Flashlight"	"Home/Accessories/"	153.16
"Switch Tone Color Crayon Pen"	"Home/Accessories/Fun/"	153.00
" Spiral Journal with Pen"	"Home/Office/Notebooks & Journals/"	153.00
"22 oz  Bottle Infuser"	"Home/Shop by Brand/YouTube/"	152.03
" Women's Short Sleeve Tri-blend Badge Tee Grey"	"(not set)"	150.00
"Red Spiral  Notebook"	"Home/Office/Notebooks & Journals/"	150.00
" Women's Scoop Neck Tee White"	"Home/Apparel/Women's/Women's-T-Shirts/"	149.20
" 25 oz Red Stainless Steel Bottle"	"Home/Drinkware/"	149.00
" Pocket Bluetooth Speaker"	"Home/Shop by Brand/Google/"	148.00
" Bib White"	"Home/Apparel/"	144.07
" Men's Vintage Henley"	"(not set)"	144.00
" Men's  Zip Hoodie"	"Home/Apparel/Men's/"	144.00
" Trucker Hat"	"Home/Shop by Brand/Google/"	144.00
" Power Bank"	"Home/Electronics/"	143.10
" Power Bank"	"Home/Electronics/Power/"	143.00
" G Noise-reducing Bluetooth Headphones"	"Home/Electronics/Audio/"	142.88
"Android Stretch Fit Hat"	"Home/Apparel/Headgear/"	141.86
"Sport Bag"	"Home/Bags/More Bags/"	141.35
" Screen Cleaning Cloth"	"Home/Electronics/Electronics Accessories/"	140.12
"Android Wool Heather Cap Heather/Black"	"Home/Shop by Brand/"	140.00
" Women's Long Sleeve Tee Lavender"	"(not set)"	139.00
" Device Holder Sticky Pad"	"Home/Electronics/"	139.00
" Men's Performance 1/4 Zip Pullover Heather/Black"	"Home/Apparel/Men's/Men's-Outerwear/"	138.00
"Android Men's Short Sleeve Tri-blend Hero Tee Grey"	"Home/Apparel/Men's/Men's-T-Shirts/"	138.00
" Women's Fleece Hoodie"	"Home/Apparel/Women's/Women's-Outerwear/"	137.79
" Learning Thermostat 3rd Gen-USA - White"	"Home/Nest/Nest-USA/"	136.64
" Tri-blend Hoodie Grey"	"Home/Apparel/Men's/Men's-Outerwear/"	136.29
" Alpine Style Backpack"	"Home/Shop by Brand/Google/"	135.58
"Keyboard DOT Sticker"	"Home/Electronics/"	135.22
"Android Women's Long Sleeve Blended Cardigan Grey"	"(not set)"	133.00
"Android Youth Short Sleeve T-shirt Aqua"	"Home/Apparel/Kid's/Kids-Youth/"	132.22
"Switch Tone Color Crayon Pen"	"Home/Office/Writing Instruments/"	132.00
"Android Men's  Zip Hoodie"	"Home/Apparel/Men's/Men's-Outerwear/"	131.47
"Android Luggage Tag"	"Home/Shop by Brand/"	131.00
" Cam Outdoor Security Camera - USA"	"Nest-USA"	130.00
" Women's Short Sleeve Hero Tee Black"	"Home/Apparel/Women's/"	127.77
" Alpine Style Backpack"	"Home/Bags/Backpacks/"	127.42
"Android Hard Cover Journal"	"Home/Office/"	127.00
"Android Wool Heather Cap Heather/Black"	"Home/Apparel/"	126.01
"Android Men's Short Sleeve Hero Tee White"	"Home/Apparel/Men's/Men's-T-Shirts/"	125.69
" Men's 100% Cotton Short Sleeve Hero Tee White"	"Home/Apparel/Men's/"	125.20
"26 oz Double Wall Insulated Bottle"	"(not set)"	125.00
" Men's 100% Cotton Short Sleeve Hero Tee White"	"Home/Apparel/Men's/Men's-T-Shirts/"	123.38
" Men's Short Sleeve Performance Badge Tee Charcoal"	"Home/Apparel/Men's/Men's-Performance Wear/"	123.00
" Women's Performance Full Zip Jacket Black"	"Home/Apparel/Women's/Women's-Performance Wear/"	123.00
"Android Sticker Sheet Ultra Removable"	"Home/Office/"	123.00
" Men's Convertible Vest-Jacket Pewter"	"Home/Apparel/Men's/Men's-Outerwear/"	121.13
" Protect Smoke + CO White Battery Alarm-USA"	"Home/Nest/Nest-USA/"	121.03
"Compact Selfie Stick"	"Home/Electronics/"	119.71
" Twill Cap"	"Home/Shop by Brand/YouTube/"	116.63
" Snapback Hat Black"	"Home/Apparel/Headgear/"	116.00
"Badge Holder"	"Home/Office/Office Other/"	116.00
"Recycled Mouse Pad"	"Home/Office/Office Other/"	116.00
"Android Lunch Kit"	"Home/Shop by Brand/Android/"	115.10
" Tote Bag"	"(not set)"	115.00
" Doodle Decal"	"Home/Shop by Brand/Google/"	114.41
" Screen Cleaning Cloth"	"Home/Office/Office Other/"	113.65
"Android Women's Long Sleeve Blended Cardigan Grey"	"Home/Apparel/Women's/Women's-Outerwear/"	113.23
"Women's  Short Sleeve Hero Tee Black"	"Home/Shop by Brand/YouTube/"	113.16
"UpCycled Handlebar Bag"	"Home/Bags/More Bags/"	113.00
"Aluminum Handy Emergency Flashlight"	"Home/Shop by Brand/Google/"	110.00
"Android Men's Vintage Henley"	"Home/Apparel/Men's/Men's-T-Shirts/"	108.24
" High Capacity 10,400mAh Charger"	"Home/Electronics/Power/"	107.87
" Vintage Henley Grey/Black"	"Home/Apparel/Men's/"	107.00
" Men's Vintage Tank"	"Home/Apparel/Men's/Men's-T-Shirts/"	106.84
" Onesie Green"	"Home/Apparel/Kid's/"	106.69
" Men's Vintage Henley"	"Home/Apparel/Men's/Men's-T-Shirts/"	106.64
" Women's Long Sleeve Tee Lavender"	"Home/Apparel/Women's/"	106.00
" Baby on Board Window Decal"	"Home/Shop by Brand/"	106.00
" Women's Short Sleeve Tri-blend Badge Tee Grey"	"Home/Shop by Brand/YouTube/"	104.00
" Men's Microfiber 1/4 Zip Pullover Blue/Indigo"	"Home/Apparel/Men's/Men's-Outerwear/"	102.09
" Men's 3/4 Sleeve Henley"	"Home/Shop by Brand/YouTube/"	102.00
" Hard Cover Journal"	"Home/Office/Notebooks & Journals/"	101.40
" Blackout Cap"	"Home/Apparel/"	100.45
" Pet Feeding Mat"	"Home/Accessories/Pet/"	99.50
" Leather Journal"	"(not set)"	99.00
" Men's Vintage Badge Tee White"	"Home/Apparel/Men's/"	99.00
" Car Clip Phone Holder"	"Home/Electronics/"	98.00
" Car Clip Phone Holder"	"Home/Electronics/Electronics Accessories/"	98.00
" RFID Journal"	"Home/Shop by Brand/YouTube/"	97.60
" Men's Vintage Tank"	"Home/Shop by Brand/"	96.29
"Keyboard DOT Sticker"	"Home/Accessories/Stickers/"	96.00
" Protect Smoke + CO White Battery Alarm-USA"	"(not set)"	95.00
" Women's Scoop Neck Tee Black"	"Home/Apparel/Women's/Women's-T-Shirts/"	95.00
" 25 oz Red Stainless Steel Bottle"	"Home/Drinkware/Water Bottles and Tumblers/"	95.00
" Mood Original Window Decal"	"(not set)"	92.00
"Foam Can and Bottle Cooler"	"(not set)"	92.00
" Mood Ninja Window Decal"	"Home/Accessories/Stickers/"	90.64
"UpCycled Handlebar Bag"	"(not set)"	89.00
"Recycled Mouse Pad"	"Home/Accessories/"	89.00
"Android Twill Cap"	"Home/Apparel/Headgear/"	88.79
" Men's Vintage Badge Tee Black"	"Home/Apparel/Men's/"	88.49
"Compact Selfie Stick"	"Home/Accessories/"	88.00
"1 oz Hand Sanitizer"	"Home/Accessories/Fun/"	88.00
"Clip-on Compact Charger"	"Home/Electronics/Power/"	88.00
"SPF-15 Slim & Slender Lip Balm"	"Home/Accessories/"	87.92
" Flashlight"	"Home/Accessories/"	87.00
" Baby on Board Window Decal"	"Home/Accessories/Stickers/"	85.11
"UpCycled Handlebar Bag"	"Home/Accessories/Sports & Fitness/"	85.00
" Men's Watershed Full Zip Hoodie Grey"	"Home/Apparel/Men's/Men's-Outerwear/"	83.85
"8 pc Android Sticker Sheet"	"Home/Accessories/Stickers/"	83.67
"Electronics Accessory Pouch"	"Home/Bags/"	83.50
" Cam Indoor Security Camera - USA"	"(not set)"	83.00
" 22 oz Water Bottle"	"Home/Drinkware/Water Bottles and Tumblers/"	82.60
" Men's Short Sleeve Hero Tee Charcoal"	"Home/Apparel/Men's/"	82.00
" Leatherette Notebook Combo"	"Home/Shop by Brand/YouTube/"	81.07
" Men's 100% Cotton Short Sleeve Hero Tee Navy"	"(not set)"	81.00
" Men's Watershed Full Zip Hoodie Grey"	"Home/Apparel/Men's/Men's-Performance Wear/"	81.00
"Android Men's Vintage Tank"	"Home/Apparel/Men's/Men's-T-Shirts/"	80.13
" Women's Short Sleeve Hero Tee Charcoal"	"Home/Shop by Brand/YouTube/"	80.00
" Women's Performance Hero Tee Gunmetal"	"(not set)"	79.89
" Canvas Tote Natural/Navy"	"Home/Bags/Shopping and Totes/"	79.00
" Device Stand"	"Home/Electronics/Electronics Accessories/"	79.00
"26 oz Double Wall Insulated Bottle"	"(not set)"	78.00
"Suitcase Organizer Cubes"	"Home/Accessories/Fun/"	78.00
"Red Spiral  Notebook"	"Home/Shop by Brand/"	77.00
" Learning Thermostat 3rd Gen-USA - Copper"	"Home/Nest/Nest-USA/"	75.77
"Suitcase Organizer Cubes"	"Home/Bags/More Bags/"	75.00
" Women's 1/4 Zip Performance Pullover Black"	"Home/Apparel/Women's/Women's-Performance Wear/"	71.46
" Men's Airflow 1/4 Zip Pullover Lapis"	"Home/Apparel/Men's/Men's-Outerwear/"	71.42
" Men's Quilted Insulated Vest Black"	"Home/Apparel/Men's/Men's-Outerwear/"	70.24
" Alpine Style Backpack"	"(not set)"	68.00
" Youth Short Sleeve T-shirt Royal Blue"	"Home/Apparel/Kid's/Kids-Youth/"	67.00
" RFID Journal"	"Home/Office/Notebooks & Journals/"	67.00
" 17oz Stainless Steel Sport Bottle"	"Home/Drinkware/"	66.33
" Toddler Short Sleeve T-shirt Grey"	"Home/Apparel/Kid's/Kid's-Toddler/"	66.00
" Leatherette Notebook Combo"	"(not set)"	64.42
"Android Men's Long & Lean Badge Tee Charcoal"	"Home/Apparel/Men's/Men's-T-Shirts/"	64.00
"Ballpoint LED Light Pen"	"(not set)"	63.00
" Laptop Backpack"	"Home/Bags/"	62.52
" Men's Short Sleeve Hero Tee White"	"Home/Shop by Brand/YouTube/"	62.13
" Screen Cleaning Cloth"	"Home/Accessories/"	61.00
" Luggage Tag"	"Home/Accessories/Fun/"	61.00
" 4400mAh Power Bank"	"(not set)"	60.00
" Hard Cover Journal"	"(not set)"	60.00
"Waterproof Backpack"	"Home/Bags/"	59.09
"Bottle Opener Clip"	"Home/Accessories/Housewares/"	58.00
"Yoga Block"	"Home/Clearance Sale/"	58.00
" Women's Yoga Jacket Black"	"(not set)"	57.00
" Toddler Raglan Shirt Blue Heather/Navy"	"Home/Apparel/Kid's/"	57.00
" Men's Long & Lean Tee Charcoal"	"Home/Shop by Brand/YouTube/"	55.39
" Men's Short Sleeve Performance Badge Tee Black"	"Home/Apparel/Men's/Men's-T-Shirts/"	55.00
"Android Spiral Journal with Pen"	"Home/Shop by Brand/Android/"	53.38
" Youth Short Sleeve Tee White"	"Home/Apparel/Kid's/Kids-Youth/"	53.00
"Android RFID Journal"	"Home/Office/Notebooks & Journals/"	53.00
" 4400mAh Power Bank"	"Home/Electronics/"	52.08
"Crunch Noise Dog Toy"	"(not set)"	51.00
" Bib Red"	"Home/Apparel/Kid's/Kid's-Infant/"	51.00
" Zipper-front Sports Bag"	"Home/Bags/More Bags/"	50.53
" Youth Girl Hoodie"	"Home/Apparel/Kid's/Kids-Youth/"	49.00
" Men's Vintage Badge Tee Sage"	"(not set)"	48.00
"26 oz Double Wall Insulated Bottle"	"Home/Drinkware/"	46.97
" Women's Quilted Insulated Vest White"	"Home/Apparel/Women's/Women's-Outerwear/"	46.00
" Youth Baseball Raglan Heather/Black"	"Home/Apparel/Kid's/Kids-Youth/"	45.00
" Men's Fleece Hoodie Black"	"Home/Apparel/Men's/Men's-Outerwear/"	45.00
" Women's Convertible Vest-Jacket Black"	"Home/Apparel/Women's/Women's-Outerwear/"	45.00
" Men's Vintage Tank"	"Home/Apparel/Men's/"	44.29
"Android Women's Fleece Hoodie"	"Home/Apparel/Women's/Women's-Outerwear/"	42.84
" Men's Performance 1/4 Zip Pullover Heather/Black"	"Home/Apparel/Men's/Men's-Performance Wear/"	41.00
" Infant Zip Hood Royal Blue"	"Home/Apparel/Kid's/"	39.00
" Men's Long Sleeve Raglan Ocean Blue"	"(not set)"	36.00
" Women's 1/4 Zip Performance Pullover Two-Tone Blue"	"Home/Apparel/Women's/Women's-Outerwear/"	36.00
"22 oz Android Bottle"	"Home/Drinkware/Water Bottles and Tumblers/"	35.00
" Pocket Bluetooth Speaker"	"${escCatTitle}"	31.00
" Leather Perforated Journal"	"Home/Office/Notebooks & Journals/"	31.00
" Twill Cap"	"Home/Apparel/Headgear/"	30.00
" Toddler 1/4 Zip Fleece Pewter"	"Home/Apparel/Kid's/"	29.00
" 17oz Stainless Steel Sport Bottle"	"Home/Shop by Brand/Google/"	27.00
" Women's Convertible Vest-Jacket Black"	"${escCatTitle}"	24.00
"Plastic Sliding Flashlight"	"Home/Electronics/Flashlights/"	24.00
" Tube Power Bank"	"(not set)"	23.00
"Yoga Mat"	"(not set)"	23.00
"Android Rise 14 oz Mug"	"Home/Shop by Brand/Android/"	23.00
"Android Sticker Sheet Ultra Removable"	"Home/Accessories/Stickers/"	22.00
" Onesie Red/Graphite"	"Home/Apparel/Kid's/Kid's-Infant/"	21.00
" Men's Performance Full Zip Jacket Black"	"(not set)"	16.00
" Men's Short Sleeve Hero Tee Heather"	"(not set)"	16.00
" Pack of 9 Decal Set"	"(not set)"	16.00
" Women's Short Sleeve Hero Tee Black"	"(not set)"	16.00
" Collapsible Pet Bowl"	"Home/Accessories/Pet/"	14.00
"7 Dog Frisbee"	"Home/Accessories/Pet/"	14.00
" Women's Vintage Hero Tee Platinum"	"Home/Apparel/Women's/"	13.00
" Zipper-front Sports Bag"	"Home/Bags/"	11.00
"SPF-15 Slim & Slender Lip Balm"	"Home/Accessories/Fun/"	9.00
" Mobile Phone Vent Mount"	"Home/Electronics/Electronics Accessories/"	8.00
" Women's Vintage Hero Tee White"	"Home/Apparel/Women's/Women's-T-Shirts/"	1.00
```

# Question 2: # Question 1: Which product category do people spend the most time on the site for? 

## SQL Queries (expand)
```sql

SELECT prodcategoryV2 AS product_category, avg_timeonsite
FROM 
(SELECT	 
		 CASE 
		 	WHEN prodcategoryV2 = '(not set)' THEN NULL
		 	ELSE prodcategoryV2
		END 
			   ,ROUND(time_on_site_avg, 2) AS avg_timeonsite
FROM
	(SELECT
		 prodnameV2
		, prodcategoryV2
		, sessions_prod_SKU
		, avg(time_on_site) AS time_on_site_avg
	FROM 
		(
		SELECT 
			a3.visitid AS anlytics_visitid
			, sessions.visitid AS sessions_visitid
			, a3.timeonsite AS time_on_site
			, sessions.v2productname AS prodnameV2
			, sessions.v2productcategory AS prodcategoryV2
			, sessions.productsku AS sessions_prod_SKU
		FROM analytics_clean3 AS a3
		JOIN all_sessions_clean3 AS sessions
		ON a3.visitid = sessions.visitid 
		WHERE a3.timeonsite IS NOT NULL	
		) AS subq1
	GROUP BY sessions_prod_SKU, prodnameV2, prodcategoryV2
	ORDER BY avg(time_on_site) DESC ) AS subq2
JOIN products
ON sessions_prod_SKU = products."SKU") AS subq3
WHERE prodcategoryV2 IS NOT NULL
ORDER BY avg_timeonsite DESC
```



## Answer: expand
```sql
"Home/Apparel/Kid's/Kid's-Infant/"	3020
"${escCatTitle}"	1860
"Home/Electronics/Audio/"	1390
"Home/Office/"	1202.11
"Home/Apparel/Kid's/"	1189.29
"Home/Shop by Brand/"	1108
"Home/Shop by Brand/Android/"	1028.36
"Home/Apparel/Women's/Women's-T-Shirts/"	1013.03
"Home/Office/"	1001.72
"Home/Electronics/"	956.29
"Home/Bags/Backpacks/"	951.37
"Nest-USA"	943
"Home/Accessories/Sports & Fitness/"	876
"Home/Apparel/Women's/Women's-T-Shirts/"	809.2
"Housewares"	800
"Home/Accessories/"	798
"Home/Drinkware/"	784.52
"Home/Apparel/"	779.2
"Home/Drinkware/"	774.71
"Home/Apparel/Headgear/"	771
"Home/Shop by Brand/Android/"	760.12
"Home/Electronics/"	750.12
"Home/Apparel/Headgear/"	739.47
"Home/Shop by Brand/"	724.33
"Home/Office/"	718.16
"Home/Drinkware/"	709.5
"Home/Shop by Brand/YouTube/"	664.7
"Home/Bags/Shopping and Totes/"	652.41
"Home/Office/Writing Instruments/"	648.06
"Home/Bags/"	638.71
"Home/Apparel/Women's/Women's-T-Shirts/"	635
"Home/Apparel/Women's/Women's-Outerwear/"	621.91
"Home/Apparel/"	602.55
"Home/Apparel/Men's/Men's-Performance Wear/"	602
"Home/Electronics/Audio/"	597.18
"Home/Apparel/Men's/Men's-T-Shirts/"	592.35
"Home/Apparel/Headgear/"	584
"Home/Apparel/"	539.65
"Home/Electronics/"	535.42
"Home/Bags/"	532.21
"Home/Nest/Nest-USA/"	528.48
"Home/Shop by Brand/Android/"	526.53
"Home/Drinkware/Water Bottles and Tumblers/"	521.11
"Home/Accessories/"	514.27
"Home/Office/"	495.01
"Home/Drinkware/Mugs and Cups/"	492
"Home/Drinkware/"	491
"Home/Apparel/Men's/Men's-T-Shirts/"	490.85
"Home/Bags/"	490.49
"Home/Apparel/Men's/Men's-T-Shirts/"	489.82
"Home/Shop by Brand/Android/"	485.68
"Home/Accessories/Stickers/"	473.83
"Home/Drinkware/"	464.54
"Home/Shop by Brand/YouTube/"	456.07
"Home/Drinkware/"	452.56
"Home/Apparel/"	452.34
"Home/Apparel/Women's/Women's-T-Shirts/"	442
"Home/Bags/More Bags/"	440
"Home/Apparel/"	438.71
"Home/Shop by Brand/"	434.31
"Home/Accessories/Stickers/"	431.3
"Home/Electronics/"	419.47
"Home/Accessories/Housewares/"	414.1
"Home/Electronics/"	409.65
"Home/Spring Sale!/"	407
"Home/Shop by Brand/Google/"	404.18
"Home/Accessories/"	400.52
"Home/Accessories/Housewares/"	395
"Home/Accessories/"	392.69
"Apparel"	391
"Home/Electronics/"	390.11
"Home/Office/"	389.56
"Home/Bags/"	389.25
"Home/Electronics/Power/"	389
"Home/Apparel/Women's/"	382.89
"Home/Shop by Brand/YouTube/"	382.52
"Home/Accessories/Housewares/"	380.68
"Home/Apparel/"	376.59
"Home/Apparel/Men's/"	369
"Home/Shop by Brand/Android/"	363.65
"Home/Shop by Brand/Google/"	362.37
"Home/Electronics/Audio/"	360.54
"Home/Bags/Backpacks/"	358.52
"Home/Apparel/"	353.65
"Home/Apparel/Men's/"	353
"Home/Apparel/Kid's/Kid's-Infant/"	347.96
"Home/Office/"	345
"Home/Apparel/Men's/Men's-T-Shirts/"	344.43
"Home/Drinkware/"	343.33
"Home/Apparel/Men's/Men's-T-Shirts/"	339.23
"Home/Office/"	338.28
"Home/Nest/Nest-USA/"	336.7
"Home/Electronics/"	332.04
"Home/Electronics/"	325.36
"Home/Apparel/Kid's/"	324
"Home/Apparel/Headgear/"	323.54
"Home/Bags/"	322.6
"Home/Apparel/Women's/Women's-T-Shirts/"	320.36
"Home/Shop by Brand/Android/"	318
"Home/Apparel/"	317.83
"Home/Shop by Brand/Google/"	316
"Home/Shop by Brand/YouTube/"	313.84
"Home/Drinkware/Water Bottles and Tumblers/"	311.42
"Home/Nest/Nest-USA/"	310.27
"Home/Bags/"	308.83
"Home/Accessories/Fun/"	307.42
"Home/Nest/Nest-USA/"	304.32
"Home/Apparel/Headgear/"	302
"Home/Accessories/"	300.83
"Home/Apparel/Women's/Women's-T-Shirts/"	300.07
"Home/Accessories/Fun/"	299.34
"Home/Drinkware/Water Bottles and Tumblers/"	296.4
"Home/Electronics/"	293
"Home/Bags/"	290.43
"Home/Apparel/Men's/Men's-Outerwear/"	289
"Home/Office/Notebooks & Journals/"	287
"Home/Shop by Brand/YouTube/"	286.9
"Home/Accessories/"	278.37
"Home/Shop by Brand/Android/"	277.35
"Home/Office/"	269.16
"Home/Apparel/Men's/"	267.43
"Home/Apparel/Women's/Women's-Performance Wear/"	258
"Home/Drinkware/"	258
"Apparel"	258
"Home/Shop by Brand/Google/"	255.99
"Home/Apparel/Women's/Women's-T-Shirts/"	255
"Home/Apparel/Men's/Men's-Performance Wear/"	254
"Home/Apparel/Women's/"	253
"Home/Apparel/Men's/Men's-T-Shirts/"	251.87
"Home/Drinkware/"	247
"Home/Apparel/Men's/Men's-T-Shirts/"	242.23
"Home/Drinkware/Mugs and Cups/"	241.31
"Home/Office/Notebooks & Journals/"	240.55
"Home/Apparel/Women's/Women's-T-Shirts/"	237.42
"Drinkware"	236
"Home/Apparel/Headgear/"	233.51
"Home/Bags/"	233.33
"Home/Office/"	233.27
"Home/Apparel/"	232
"Home/Drinkware/Water Bottles and Tumblers/"	232
"Home/Accessories/Fun/"	231
"Home/Electronics/Electronics Accessories/"	229
"Home/Apparel/Men's/Men's-Outerwear/"	228.03
"Home/Shop by Brand/YouTube/"	226
"Home/Apparel/Women's/Women's-Outerwear/"	225.2
"Home/Apparel/Kid's/Kid's-Infant/"	224
"Home/Electronics/"	222.46
"Home/Apparel/Men's/Men's-Performance Wear/"	222.4
"Home/Shop by Brand/"	221
"Home/Bags/More Bags/"	215
"Home/Apparel/Men's/"	214.97
"Home/Clearance Sale/"	212
"Home/Drinkware/"	208
"Home/Electronics/"	205.56
"Home/Bags/Backpacks/"	205.49
"Home/Accessories/Fun/"	205
"Home/Apparel/Women's/Women's-T-Shirts/"	204.41
"Home/Apparel/Kid's/Kid's-Infant/"	204.26
"Home/Shop by Brand/"	204
"Home/Apparel/Men's/Men's-Outerwear/"	202.29
"Home/Apparel/Men's/Men's-Performance Wear/"	199.33
"Home/Shop by Brand/Google/"	197.09
"Home/Apparel/Men's/"	196.94
"Home/Shop by Brand/Google/"	195.59
"Home/Electronics/Flashlights/"	195.31
"Home/Apparel/Women's/Women's-Performance Wear/"	194
"Home/Apparel/Men's/Men's-Outerwear/"	193.86
"Home/Shop by Brand/"	193
"Home/Shop by Brand/YouTube/"	192.15
"Home/Accessories/"	188.41
"Home/Accessories/Stickers/"	188
"Home/Apparel/Women's/Women's-T-Shirts/"	186
"Home/Shop by Brand/Google/"	184.7
"Home/Apparel/Women's/"	183
"Home/Drinkware/Water Bottles and Tumblers/"	182
"Home/Drinkware/"	182
"Home/Accessories/Fun/"	181
"Home/Accessories/"	179.14
"Home/Shop by Brand/YouTube/"	179
"Home/Apparel/Men's/Men's-T-Shirts/"	178.23
"Home/Shop by Brand/YouTube/"	177.94
"Home/Apparel/"	176.76
"Home/Apparel/"	173.37
"Home/Apparel/Men's/Men's-Performance Wear/"	172
"Home/Bags/"	171
"Home/Accessories/Fun/"	166.33
"Home/Bags/Backpacks/"	164
"Home/Electronics/Electronics Accessories/"	163.3
"Home/Electronics/Electronics Accessories/"	161.71
"Home/Shop by Brand/YouTube/"	155.25
"Home/Shop by Brand/YouTube/"	155.12
"Home/Office/"	154.54
"Home/Accessories/"	154
"Home/Accessories/"	153.16
"Home/Office/Notebooks & Journals/"	153
"Home/Accessories/Fun/"	153
"Home/Shop by Brand/YouTube/"	152.03
"Home/Office/Notebooks & Journals/"	150
"Home/Apparel/Women's/Women's-T-Shirts/"	149.2
"Home/Drinkware/"	149
"Home/Shop by Brand/Google/"	148
"Home/Apparel/"	144.07
"Home/Apparel/Men's/"	144
"Home/Shop by Brand/Google/"	144
"Home/Electronics/"	143.1
"Home/Electronics/Power/"	143
"Home/Electronics/Audio/"	142.88
"Home/Apparel/Headgear/"	141.86
"Home/Bags/More Bags/"	141.35
"Home/Electronics/Electronics Accessories/"	140.12
"Home/Shop by Brand/"	140
"Home/Electronics/"	139
"Home/Apparel/Men's/Men's-Outerwear/"	138
"Home/Apparel/Men's/Men's-T-Shirts/"	138
"Home/Apparel/Women's/Women's-Outerwear/"	137.79
"Home/Nest/Nest-USA/"	136.64
"Home/Apparel/Men's/Men's-Outerwear/"	136.29
"Home/Shop by Brand/Google/"	135.58
"Home/Electronics/"	135.22
"Home/Apparel/Kid's/Kids-Youth/"	132.22
"Home/Office/Writing Instruments/"	132
"Home/Apparel/Men's/Men's-Outerwear/"	131.47
"Home/Shop by Brand/"	131
"Nest-USA"	130
"Home/Apparel/Women's/"	127.77
"Home/Bags/Backpacks/"	127.42
"Home/Office/"	127
"Home/Apparel/"	126.01
"Home/Apparel/Men's/Men's-T-Shirts/"	125.69
"Home/Apparel/Men's/"	125.2
"Home/Apparel/Men's/Men's-T-Shirts/"	123.38
"Home/Office/"	123
"Home/Apparel/Men's/Men's-Performance Wear/"	123
"Home/Apparel/Women's/Women's-Performance Wear/"	123
"Home/Apparel/Men's/Men's-Outerwear/"	121.13
"Home/Nest/Nest-USA/"	121.03
"Home/Electronics/"	119.71
"Home/Shop by Brand/YouTube/"	116.63
"Home/Office/Office Other/"	116
"Home/Apparel/Headgear/"	116
"Home/Office/Office Other/"	116
"Home/Shop by Brand/Android/"	115.1
"Home/Shop by Brand/Google/"	114.41
"Home/Office/Office Other/"	113.65
"Home/Apparel/Women's/Women's-Outerwear/"	113.23
"Home/Shop by Brand/YouTube/"	113.16
"Home/Bags/More Bags/"	113
"Home/Shop by Brand/Google/"	110
"Home/Apparel/Men's/Men's-T-Shirts/"	108.24
"Home/Electronics/Power/"	107.87
"Home/Apparel/Men's/"	107
"Home/Apparel/Men's/Men's-T-Shirts/"	106.84
"Home/Apparel/Kid's/"	106.69
"Home/Apparel/Men's/Men's-T-Shirts/"	106.64
"Home/Shop by Brand/"	106
"Home/Apparel/Women's/"	106
"Home/Shop by Brand/YouTube/"	104
"Home/Apparel/Men's/Men's-Outerwear/"	102.09
"Home/Shop by Brand/YouTube/"	102
"Home/Office/Notebooks & Journals/"	101.4
"Home/Apparel/"	100.45
"Home/Accessories/Pet/"	99.5
"Home/Apparel/Men's/"	99
"Home/Electronics/Electronics Accessories/"	98
"Home/Electronics/"	98
"Home/Shop by Brand/YouTube/"	97.6
"Home/Shop by Brand/"	96.29
"Home/Accessories/Stickers/"	96
"Home/Apparel/Women's/Women's-T-Shirts/"	95
"Home/Drinkware/Water Bottles and Tumblers/"	95
"Home/Accessories/Stickers/"	90.64
"Home/Accessories/"	89
"Home/Apparel/Headgear/"	88.79
"Home/Apparel/Men's/"	88.49
"Home/Accessories/Fun/"	88
"Home/Accessories/"	88
"Home/Electronics/Power/"	88
"Home/Accessories/"	87.92
"Home/Accessories/"	87
"Home/Accessories/Stickers/"	85.11
"Home/Accessories/Sports & Fitness/"	85
"Home/Apparel/Men's/Men's-Outerwear/"	83.85
"Home/Accessories/Stickers/"	83.67
"Home/Bags/"	83.5
"Home/Drinkware/Water Bottles and Tumblers/"	82.6
"Home/Apparel/Men's/"	82
"Home/Shop by Brand/YouTube/"	81.07
"Home/Apparel/Men's/Men's-Performance Wear/"	81
"Home/Apparel/Men's/Men's-T-Shirts/"	80.13
"Home/Shop by Brand/YouTube/"	80
"Home/Bags/Shopping and Totes/"	79
"Home/Electronics/Electronics Accessories/"	79
"Home/Accessories/Fun/"	78
"Home/Shop by Brand/"	77
"Home/Nest/Nest-USA/"	75.77
"Home/Bags/More Bags/"	75
"Home/Apparel/Women's/Women's-Performance Wear/"	71.46
"Home/Apparel/Men's/Men's-Outerwear/"	71.42
"Home/Apparel/Men's/Men's-Outerwear/"	70.24
"Home/Apparel/Kid's/Kids-Youth/"	67
"Home/Office/Notebooks & Journals/"	67
"Home/Drinkware/"	66.33
"Home/Apparel/Kid's/Kid's-Toddler/"	66
"Home/Apparel/Men's/Men's-T-Shirts/"	64
"Home/Bags/"	62.52
"Home/Shop by Brand/YouTube/"	62.13
"Home/Accessories/Fun/"	61
"Home/Accessories/"	61
"Home/Bags/"	59.09
"Home/Accessories/Housewares/"	58
"Home/Clearance Sale/"	58
"Home/Apparel/Kid's/"	57
"Home/Shop by Brand/YouTube/"	55.39
"Home/Apparel/Men's/Men's-T-Shirts/"	55
"Home/Shop by Brand/Android/"	53.38
"Home/Office/Notebooks & Journals/"	53
"Home/Apparel/Kid's/Kids-Youth/"	53
"Home/Electronics/"	52.08
"Home/Apparel/Kid's/Kid's-Infant/"	51
"Home/Bags/More Bags/"	50.53
"Home/Apparel/Kid's/Kids-Youth/"	49
"Home/Drinkware/"	46.97
"Home/Apparel/Women's/Women's-Outerwear/"	46
"Home/Apparel/Kid's/Kids-Youth/"	45
"Home/Apparel/Women's/Women's-Outerwear/"	45
"Home/Apparel/Men's/Men's-Outerwear/"	45
"Home/Apparel/Men's/"	44.29
"Home/Apparel/Women's/Women's-Outerwear/"	42.84
"Home/Apparel/Men's/Men's-Performance Wear/"	41
"Home/Apparel/Kid's/"	39
"Home/Apparel/Women's/Women's-Outerwear/"	36
"Home/Drinkware/Water Bottles and Tumblers/"	35
"Home/Office/Notebooks & Journals/"	31
"${escCatTitle}"	31
"Home/Apparel/Headgear/"	30
"Home/Apparel/Kid's/"	29
"Home/Shop by Brand/Google/"	27
"${escCatTitle}"	24
"Home/Electronics/Flashlights/"	24
"Home/Shop by Brand/Android/"	23
"Home/Accessories/Stickers/"	22
"Home/Apparel/Kid's/Kid's-Infant/"	21
"Home/Accessories/Pet/"	14
"Home/Accessories/Pet/"	14
"Home/Apparel/Women's/"	13
"Home/Bags/"	11
"Home/Accessories/Fun/"	9
"Home/Electronics/Electronics Accessories/"	8
"Home/Apparel/Women's/Women's-T-Shirts/"	1
```


## Question 3: Why is there variability in the product sku format?

SQL Queries: 
### Query 1 - products table
When I run this code:
```sql
SELECT * from products
WHERE "SKU" NOT LIKE '%GG%'
```

I see that all `OrderedQuantity` and `Stocklevel` values are zero. Suggests that one format of product SKU's is for discontinued items. Add new column to label discontinued items? 

### **Query 1 Result**

"9180850"	"Ballpoint Stylus Pen"	0	0	6	0.3	0.5
"9183118"	" Women's Fleece Hoodie Black"	0	0	6	0.3	0.5
"9183203"	" Device Holder Sticky Pad"	0	0	8	0.3	0.5
"9184697"	" Mood Original Window Decal"	0	0	11	0.3	0.5
"9183225"	" Luggage Tag"	0	0	11	0.3	0.5
"9182723"	" Men's 100% Cotton Short Sleeve Hero Tee White"	0	0	11	0.3	0.5
"9182720"	" Men's Short Sleeve Badge Tee Charcoal"	0	0	13	0.3	0.5
"9182772"	" Women's Performance Full Zip Jacket Black"	0	0	14	0.3	0.5
"9182755"	" Men's Colorblock Tee White/Heather"	0	0	14	0.3	0.5
"9184720"	" Women's Short Sleeve Hero Tee Sky Blue"	0	0	16	0.3	0.5
"9182761"	" Women's Yoga Jacket Black"	0	0	16	0.3	0.5
"9184689"	" Men's Short Sleeve Tee"	0	0	17	0.3	0.5
"9184682"	" Mobile Phone Vent Mount"	0	0	7	0.2	0.5
"9183234"	" Learning Thermostat 3rd Gen-USA - Stainless Steel"	0	0	8	0.2	0.5
"9182859"	" Toddler Raglan Shirt Blue Heather/Navy"	0	0	11	0.2	0.5
"9182863"	" Toddler Sports T-shirt Red"	0	0	5	0.6	1
"9180811"	"Plastic Sliding Flashlight"	0	0	5	0.6	1
"9182750"	" Men's Performance 1/4 Zip Pullover Heather/Black"	0	0	6	0.6	1
"9183205"	" Zipper-front Sports Bag"	0	0	7	0.6	1
"9182980"	" Pet Feeding Mat"	0	0	8	0.6	1
"9180813"	" Tube Power Bank"	0	0	11	0.6	1
"9182778"	" Women's Softshell Jacket Black/Grey"	0	0	13	0.6	1
"9184683"	" Women's Short Sleeve Tee"	0	0	13	0.6	1
"9182774"	" Women's Yoga Pants"	0	0	15	0.6	1
"9183220"	" Leather Journal-Brown"	0	0	16	0.6	1
"9182780"	" Women's Shell Jacket Blue/Black"	0	0	16	0.6	1
"9182179"	"Android Women's Short Sleeve Badge Tee Dark Heather"	0	0	7	0.7	1
"9182997"	" 17oz Stainless Steel Sport Bottle"	0	0	18	0.7	1
"9180770"	"Yoga Mat Blue"	0	0	6	0.1	0.3
"9184681"	" 17 oz Double Wall Stainless Steel Insulated Bottle"	0	0	8	0.1	0.3
"9183086"	" Youth Girl Tee Green"	0	0	11	0.1	0.3
"9181573"	" Snapback Hat Black"	0	0	12	0.1	0.3
"9180757"	"Yoga Block"	0	0	13	0.1	0.3
"9182812"	" Infant Zip Hood Pink"	0	0	14	0.1	0.3
"9181019"	" Tri-blend Hoodie Grey"	0	0	19	0.1	0.3
"9180764"	" Canvas Tote Natural/Navy"	0	0	12	0.2	0.3
"9182739"	" Men's Watershed Full Zip Hoodie Grey"	0	0	14	0.2	0.3
"9182793"	" Men's Long & Lean Tee Charcoal"	0	0	16	0.2	0.3
"9183214"	" Hard Cover Journal"	0	0	17	0.2	0.3
"9180844"	"Gunmetal Roller Ball Pen"	0	0	9	0.3	0.6
"9182764"	" Women's Convertible Vest-Jacket Black"	0	0	11	0.3	0.6
"9182828"	" Toddler Short Sleeve T-shirt Royal Blue"	0	0	13	0.3	0.6
"9182751"	" Men's Performance Full Zip Jacket Black"	0	0	14	0.3	0.6
"9184695"	" Baby on Board Window Decal"	0	0	15	0.3	0.6
"9182581"	" Women's Fleece Hoodie"	0	0	17	0.3	0.6
"9182771"	" Women's 1/4 Zip Jacket Charcoal"	0	0	6	0.4	0.6
"9182743"	" Men's Microfiber 1/4 Zip Pullover Blue/Indigo"	0	0	7	0.4	0.6
"9180838"	"Metal Texture Roller Pen"	0	0	8	0.4	0.6
"9182569"	" Men's  Zip Hoodie"	0	0	10	0.4	0.6
"9182737"	" Women's 3/4 Sleeve Baseball Raglan Heather/Black"	0	0	17	0.4	0.6
"9184721"	"BLM Sweatshirt"	0	0	19	0.4	0.6
"9182898"	"Android Youth Short Sleeve T-shirt Aqua"	0	0	16	0.7	1.2
"9183112"	" Men's Fleece Hoodie Black"	0	0	18	0.7	1.2
"9184734"	" Learning Thermostat 3rd Gen-USA - Copper"	0	0	19	0.7	1.2
"9181572"	"Android Wool Heather Cap Heather/Black"	0	0	5	0.8	1.2
"9182705"	"Android Men's Long & Lean Badge Tee Charcoal"	0	0	7	0.8	1.2
"9182785"	" Women's Lightweight Microfleece Jacket"	0	0	8	0.8	1.2
"9180767"	" Slim Utility Travel Bag"	0	0	8	0.8	1.2
"9182502"	" Women's Yoga Jacket Black"	0	0	10	0.8	1.2
"9183186"	" G Noise-reducing Bluetooth Headphones"	0	0	11	0.8	1.2
"9180905"	" Men's Long Sleeve Raglan Ocean Blue"	0	0	13	0.8	1.2
"9183152"	" Youth Short Sleeve Tee Red"	0	0	14	0.8	1.2
"9182777"	" Women's Performance Golf Polo Blue"	0	0	14	0.8	1.2
"9182658"	" Women's Short Sleeve Hero Tee Sky Blue"	0	0	17	0.8	1.2
"9182742"	" Men's Convertible Vest-Jacket Pewter"	0	0	17	0.8	1.2
"9181151"	"Gift Card - $50.00"	0	0	5	0.4	0.7
"9180782"	"Seat Pack Organizer"	0	0	7	0.4	0.7
"9183226"	"Android Luggage Tag"	0	0	7	0.4	0.7
"9183228"	" Cam Indoor Security Camera - USA"	0	0	10	0.4	0.7
"9182999"	" Bongo Cupholder Bluetooth Speaker"	0	0	10	0.4	0.7
"9182909"	" Collapsible Pet Bowl"	0	0	11	0.4	0.7
"9182559"	"Android Men's Vintage Henley"	0	0	12	0.4	0.7
"9181150"	"Gift Card - $250.00"	0	0	12	0.4	0.7
"9184705"	" Women's Typography Short Sleeve Tee"	0	0	13	0.4	0.7
"9180840"	"Satin Black Ballpoint Pen"	0	0	16	0.4	0.7
"9182995"	" Car Clip Phone Holder"	0	0	18	0.4	0.7
"9182752"	" Men's Short Sleeve Performance Badge Tee Charcoal"	0	0	19	0.4	0.7
"9182383"	" Men's Watershed Full Zip Hoodie Grey"	0	0	7	0.9	1.4
"9182587"	"Android Women's Fleece Hoodie"	0	0	12	0.9	1.4
"9183000"	" Pocket Bluetooth Speaker"	0	0	12	0.9	1.4
"9183194"	" Executive Umbrella"	0	0	18	0.9	1.4
"9180868"	"Crunch Noise Dog Toy"	0	0	19	0.9	1.4
"9180808"	"Basecamp Explorer Powerbank Flashlight"	0	0	5	0	0.1
"9184676"	"UpCycled Handlebar Bag"	0	0	7	0	0.1
"9181149"	"Gift Card - $25.00"	0	0	11	0	0.1
"9182706"	"Android Stretch Fit Hat"	0	0	15	0	0.1
"9180862"	" Screen Cleaning Cloth"	0	0	15	0	0.1
"9183106"	" Women's Performance Hero Tee Gunmetal"	0	0	17	0	0.1
"9182701"	"Android Men's Long Sleeve Badge Crew Tee Heather"	0	0	17	0	0.1
"9183210"	" RFID Journal"	0	0	19	0	0.1
"9180792"	"20 oz Stainless Steel Insulated Tumbler"	0	0	8	0	0.2
"9182753"	" Men's Weatherblock Shell Jacket Black"	0	0	10	0	0.2
"9183221"	" Leather Journal-Black"	0	0	15	0	0.2
"9182176"	"Android Women's Short Sleeve Badge Tee Dark Heather"	0	0	8	0.1	0.2
"9182765"	" Women's Convertible Vest-Jacket Sea Foam Green"	0	0	10	0.1	0.2
"9180771"	"Yoga Mat Purple"	0	0	11	0.1	0.2
"9182820"	" Baby Essentials Set"	0	0	12	0.1	0.2
"9183223"	" Spiral Leather Journal"	0	0	18	0.1	0.2
"9182726"	" Men's Long & Lean Tee Charcoal"	0	0	18	0.1	0.2
"9183015"	" Onesie Heather"	0	0	19	0.1	0.2
"9180833"	"Rubber Grip Ballpoint Pen 4 Pack"	0	0	5	0.2	0.4
"9182709"	"Android Women's Long Sleeve Blended Cardigan Grey"	0	0	6	0.2	0.4
"9180781"	"Suitcase Organizer Cubes"	0	0	7	0.2	0.4
"9182769"	" Women's Short Sleeve Performance Tee Pewter"	0	0	7	0.2	0.4
"9181148"	"Gift Card- $100.00"	0	0	10	0.2	0.4
"9182173"	" Stylus Pen w/ LED Light"	0	0	11	0.2	0.4
"9180748"	"Android Lunch Kit"	0	0	12	0.2	0.4
"9182754"	" Men's Softshell Jacket Black/Grey"	0	0	14	0.2	0.4
"9181137"	" Alpine Style Backpack"	0	0	14	0.2	0.4
"9184737"	" Pack of 9 Decal Set"	0	0	14	0.2	0.4
"9182746"	" Men's Quilted Insulated Vest Battleship Grey"	0	0	15	0.2	0.4
"9180806"	"Clip-on Compact Charger"	0	0	16	0.2	0.4
"9180824"	"Foam Can and Bottle Cooler"	0	0	16	0.2	0.4
"9182773"	" Women's Short Sleeve Performance Tee Charcoal"	0	0	18	0.2	0.4
"9183091"	" Youth Baseball Raglan Heather/Black"	0	0	19	0.2	0.4
"9182903"	"Android Youth Short Sleeve T-shirt Pewter"	0	0	19	0.2	0.4
"9180814"	"Micro Wireless Earbud"	0	0	5	0.5	0.8
"9180759"	" Lunch Bag"	0	0	6	0.5	0.8
"9182722"	" Men's 100% Cotton Short Sleeve Hero Tee Navy"	0	0	7	0.5	0.8
"9184620"	" Men's Performance Full Zip Jacket Black"	0	0	9	0.5	0.8
"9180754"	"8 pc Android Sticker Sheet"	0	0	13	0.5	0.8
"9182605"	" Women's Tee Grey"	0	0	13	0.5	0.8
"9184698"	" Mood Ninja Window Decal"	0	0	14	0.5	0.8
"9180809"	" Flashlight"	0	0	14	0.5	0.8
"9183213"	"Android Hard Cover Journal"	0	0	18	0.5	0.8
"9181139"	"Waterproof Backpack"	0	0	18	0.5	0.8
"9182788"	"Yoga Mat"	0	0	19	0.5	0.8
"9183240"	"25L Classic Rucksack"	0	0	5	0.7	1.1
"9182873"	"Android Toddler Short Sleeve T-shirt Pink"	0	0	5	0.7	1.1
"9182721"	" Men's 100% Cotton Short Sleeve Hero Tee Black"	0	0	5	0.7	1.1
"9180756"	"Windup Android"	0	0	6	0.7	1.1
"9183230"	" Protect Smoke + CO White Battery Alarm-USA"	0	0	7	0.7	1.1
"9182738"	" Women's Long Sleeve Blended Cardigan Charcoal"	0	0	8	0.7	1.1
"9182593"	" Men's Pullover Hoodie Grey"	0	0	9	0.7	1.1
"9182781"	" Women's Short Sleeve Hero Tee Black"	0	0	9	0.7	1.1
"9182575"	"Android Men's  Zip Hoodie"	0	0	11	0.7	1.1
"9182784"	" Women's Short Sleeve Hero Tee White"	0	0	12	0.7	1.1
"9181664"	"Waterproof Gear Bag"	0	0	12	0.7	1.1
"9182725"	" Men's Long & Lean Tee Grey"	0	0	15	0.7	1.1
"9180820"	" Doodle Decal"	0	0	7	0.5	0.9
"9180793"	"26 oz Double Wall Insulated Bottle"	0	0	8	0.5	0.9
"9180766"	"Sport Bag"	0	0	8	0.5	0.9
"9184675"	"UpCycled Bike Saddle Bag"	0	0	8	0.5	0.9
"9184708"	" Women's Typography Short Sleeve Tee"	0	0	9	0.5	0.9
"9183096"	" Youth Sports Tee Navy"	0	0	12	0.5	0.9
"9180779"	"1 oz Hand Sanitizer"	0	0	12	0.5	0.9
"9182848"	" Toddler Hoodie Royal Blue"	0	0	18	0.5	0.9
"9181138"	" Rucksack"	0	0	5	0.6	0.9
"9182740"	" Men's Airflow 1/4 Zip Pullover Black"	0	0	9	0.6	0.9
"9184733"	" Learning Thermostat 3rd Gen-USA - White"	0	0	11	0.6	0.9
"9182719"	" Men's Short Sleeve Hero Tee Charcoal"	0	0	12	0.6	0.9
"9182553"	" Men's Vintage Henley"	0	0	17	0.6	0.9
"9182714"	" Men's Long Sleeve Raglan Ocean Blue"	0	0	18	0.6	0.9
"9182816"	" Infant Zip Hood Royal Blue"	0	0	6	0.8	1.3
"9180762"	" Tote Bag"	0	0	6	0.8	1.3
"9183222"	" Leather Perforated Journal"	0	0	7	0.8	1.3
"9180769"	" Laptop Backpack"	0	0	7	0.8	1.3
"9183196"	" 4400mAh Power Bank"	0	0	7	0.8	1.3
"9183212"	"Android RFID Journal"	0	0	9	0.8	1.3
"9183219"	" Leather Journal"	0	0	9	0.8	1.3
"9184707"	" Women's Typography Short Sleeve Tee"	0	0	12	0.8	1.3
"9183188"	" High Capacity 10,400mAh Charger"	0	0	14	0.8	1.3
"9182599"	" Women's Long Sleeve Tee Lavender"	0	0	15	0.8	1.3
"9182717"	" Men's Short Sleeve Hero Tee Light Blue"	0	0	15	0.8	1.3
"9183229"	" Cam Outdoor Security Camera - USA"	0	0	18	0.8	1.3
"9183239"	"25L Classic Rucksack"	0	0	19	0.8	1.3
"9182741"	" Men's Airflow 1/4 Zip Pullover Lapis"	0	0	8	0.9	1.3
"9182745"	" Men's Quilted Insulated Vest Black"	0	0	9	0.9	1.3
"9183241"	"25L Classic Rucksack"	0	0	16	0.9	1.3
"9182806"	" Onesie Green"	0	0	17	0.9	1.3

### Query 2
Also, when I run this: 
```sql
SELECT * from all_sessions
WHERE productsku NOT LIKE '%GG%'
```
I find that all prices are set to $0.00. 

### **Query 2 Result**
"3.63353E+17"	"Direct"	0	"Hong Kong"	"Hong Kong"			29	2		"2017-02-12 00:00:00"	"1486902812"	"PAGE"			"$0.00"		"9182859"	"Google Toddler Raglan Shirt Blue Heather/Navy"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/BRIGHTtravels Seat Pack Organizer"		"/google+redesign/"	0	1	
"5.8145E+18"	"Direct"	87417	"United States"	"not available in demo dataset"			87	7		"2016-09-21 00:00:00"	"1474513949"	"PAGE"			"$0.00"		"9182752"	"Google Men's Short Sleeve Performance Badge Tee Charcoal"	"(not set)"	"(not set)"	"USD"					"Google Men's Watershed Full Zip Hoodie Grey"		"/google+redesign/"	0	1	
"3.36922E+18"	"Organic Search"	0	"Canada"	"not available in demo dataset"			145	3		"2016-09-22 00:00:00"	"1474548525"	"PAGE"			"$0.00"		"9182772"	"Google Women's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"Google Rucksack"		"/google+redesign/"	0	1	
"9.94731E+18"	"Organic Search"	78865	"Thailand"	"Bangkok"			144	6	1	"2017-07-09 00:00:00"	"1499655181"	"PAGE"			"$0.00"		"9182553"	"YouTube Men's Vintage Henley"	"(not set)"	"(not set)"	"USD"					"YouTube Men's Vintage Tank"		"/google+redesign/"	0	1	
"4.55958E+17"	"Organic Search"	17026	"Switzerland"	"not available in demo dataset"			81	4	1	"2017-07-14 00:00:00"	"1500036028"	"PAGE"			"$0.00"		"9182502"	"Google Women's Yoga Jacket Black"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"1.2477E+18"	"Direct"	0	"United States"	"Westlake Village"			399	4		"2017-04-11 00:00:00"	"1491933019"	"PAGE"			"$0.00"		"9180905"	"Google Men's Long Sleeve Raglan Ocean Blue"	"(not set)"	"(not set)"	"USD"					"Waze Dress Socks"		"/google+redesign/"	0	1	
"8.54355E+17"	"Direct"	0	"Switzerland"	"not available in demo dataset"			345	8		"2017-02-04 00:00:00"	"1486244189"	"PAGE"			"$0.00"		"9182739"	"Google Men's Watershed Full Zip Hoodie Grey"	"(not set)"	"(not set)"	"USD"					"YouTube Men's Skater Tee Charcoal"		"/google+redesign/"	0	1	
"4.70296E+18"	"Referral"	157776	"United States"	"Santa Clara"			238	10		"2017-01-21 00:00:00"	"1485014366"	"PAGE"			"$0.00"		"9182760"	"Google Women's Insulated Thermal Vest Navy"	"(not set)"	"(not set)"	"USD"					"Google Men's Weatherblock Shell Jacket Black"		"/google+redesign/"	0	1	
"4.32351E+17"	"Organic Search"	0	"New Zealand"	"not available in demo dataset"			46	3		"2017-03-23 00:00:00"	"1490292958"	"PAGE"			"$0.00"		"9182785"	"Google Women's Lightweight Microfleece Jacket"	"(not set)"	"(not set)"	"USD"					"Google Device Holder Sticky Pad"		"/google+redesign/"	0	1	
"8.81118E+18"	"Organic Search"	0	"India"	"Hyderabad"				1		"2016-11-30 00:00:00"	"1480514592"	"PAGE"			"$0.00"		"9182575"	"Android Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"Google Youth Short Sleeve T-shirt Royal Blue"		"/google+redesign/"	0	1	
"8.87571E+18"	"Organic Search"	46602	"United States"	"not available in demo dataset"			65	6		"2016-12-10 00:00:00"	"1481383926"	"PAGE"			"$0.00"		"9183191"	"Google 40 oz Insulated Monster Bottle"	"(not set)"	"(not set)"	"USD"					"Google Insulated Stainless Steel Bottle"		"/google+redesign/"	0	1	
"8.09964E+17"	"Organic Search"	70427	"Thailand"	"Bangkok"			151	8		"2017-04-09 00:00:00"	"1491726593"	"PAGE"			"$0.00"		"9182739"	"Google Men's Watershed Full Zip Hoodie Grey"	"(not set)"	"(not set)"	"USD"					"Android Men's Pep Rally Short Sleeve Tee Navy"		"/google+redesign/"	0	1	
"5.2724E+18"	"Organic Search"	0	"India"	"Chennai"				1	1	"2017-07-25 00:00:00"	"1501043387"	"PAGE"			"$0.00"		"9182714"	"Google Men's Long Sleeve Raglan Ocean Blue"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"9.59744E+18"	"Organic Search"	0	"Switzerland"	"Zurich"			23	2	1	"2017-07-19 00:00:00"	"1500452760"	"PAGE"			"$0.00"		"9182788"	"Yoga Mat"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"8.55116E+17"	"Organic Search"	0	"United States"	"Austin"				1		"2016-10-09 00:00:00"	"1476028833"	"PAGE"			"$0.00"		"9182994"	"Android 17oz Stainless Steel Sport Bottle"	"(not set)"	"(not set)"	"USD"					"Google Accent Insulated Stainless Steel Bottle"		"/google+redesign/"	0	1	
"4.45045E+18"	"Organic Search"	0	"Sweden"	"not available in demo dataset"				1	1	"2017-07-16 00:00:00"	"1500241234"	"PAGE"			"$0.00"		"9182788"	"Yoga Mat"	"(not set)"	"(not set)"	"USD"					"YouTube Twill Cap"		"/google+redesign/"	0	1	
"2.14967E+16"	"Organic Search"	0	"Belgium"	"not available in demo dataset"				1		"2017-02-24 00:00:00"	"1487953778"	"PAGE"			"$0.00"		"9182723"	"Google Men's 100% Cotton Short Sleeve Hero Tee White"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"4.27837E+18"	"Direct"	0	"United States"	"not available in demo dataset"			143	9		"2016-10-05 00:00:00"	"1475682402"	"PAGE"			"$0.00"		"9182723"	"Google Men's 100% Cotton Short Sleeve Hero Tee White"	"(not set)"	"(not set)"	"USD"					"Bluetooth Headphones"		"/google+redesign/"	0	1	
"7.2514E+18"	"Organic Search"	0	"United States"	"Sunnyvale"			12	2		"2016-10-12 00:00:00"	"1476325659"	"PAGE"			"$0.00"		"9183228"	"Nest¬Æ Cam Indoor Security Camera - USA"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Gift Card - $250.00"		"/google+redesign/"	0	1	
"8.44316E+18"	"Direct"	93473	"United States"	"not available in demo dataset"			180	5		"2016-12-10 00:00:00"	"1481391160"	"PAGE"			"$0.00"		"9182772"	"Google Women's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"YouTube Twill Cap"		"/google+redesign/"	0	1	
"9.65914E+18"	"Paid Search"	412454	"United States"	"Los Angeles"			418	16		"2017-04-24 00:00:00"	"1493025088"	"PAGE"			"$0.00"		"9182742"	"Google Men's Convertible Vest-Jacket Pewter"	"(not set)"	"(not set)"	"USD"					"Google Men's Short Sleeve Badge Tee Charcoal"		"/google+redesign/"	0	1	
"6.14548E+18"	"Organic Search"	64787	"United States"	"not available in demo dataset"			229	5		"2017-02-10 00:00:00"	"1486789049"	"PAGE"			"$0.00"		"9180771"	"Yoga Mat Purple"	"(not set)"	"(not set)"	"USD"					"SPF-15 Slim & Slender Lip Balm"		"/google+redesign/"	0	1	
"3.61037E+18"	"Paid Search"	98556	"United States"	"Palo Alto"			325	9	2	"2017-08-01 00:00:00"	"1501649603"	"PAGE"			"$0.00"		"9183213"	"Android Hard Cover Journal"	"(not set)"	"(not set)"	"USD"					"Switch Tone Color Crayon Pen"		"/google+redesign/"	0	1	
"3.23076E+18"	"Referral"	66979	"United States"	"Washington"			67	4		"2016-08-04 00:00:00"	"1470371701"	"PAGE"			"$0.00"		"9182668"	"YouTube Men's 3/4 Sleeve Henley"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Chevron Shopper"		"/google+redesign/"	0	1	
"6.45617E+18"	"Direct"	0	"United States"	"New York"			104	7		"2017-03-30 00:00:00"	"1490889910"	"PAGE"			"$0.00"		"9182173"	"Google Stylus Pen w/ LED Light"	"(not set)"	"(not set)"	"USD"					"Gel Roller Pen"		"/google+redesign/"	0	1	
"9.70795E+17"	"Direct"	1749087	"Indonesia"	"Jakarta"			1828	17	10	"2017-07-20 00:00:00"	"1500618567"	"PAGE"			"$0.00"		"9182771"	"Google Women's 1/4 Zip Jacket Charcoal"	"(not set)"	"(not set)"	"USD"					"Waze Pack of 9 Decal Set"		"/google+redesign/"	0	1	
"8.98765E+17"	"Organic Search"	0	"Russia"	"not available in demo dataset"				1	1	"2017-07-20 00:00:00"	"1500596780"	"PAGE"			"$0.00"		"9182771"	"Google Women's 1/4 Zip Jacket Charcoal"	"(not set)"	"(not set)"	"USD"					"Android 17oz Stainless Steel Sport Bottle"		"/google+redesign/"	0	1	
"8.87032E+18"	"Direct"	0	"United States"	"not available in demo dataset"			40	2		"2016-12-11 00:00:00"	"1481463396"	"PAGE"			"$0.00"		"9182771"	"Google Women's 1/4 Zip Jacket Charcoal"	"(not set)"	"(not set)"	"USD"					"Google Laptop and Cell Phone Stickers"		"/google+redesign/"	0	1	
"3.42867E+18"	"Organic Search"	0	"Slovenia"	"not available in demo dataset"				1		"2016-10-27 00:00:00"	"1477596745"	"PAGE"			"$0.00"		"9181570"	"Google Wool Heather Cap Heather/Navy"	"(not set)"	"(not set)"	"USD"					"Google Electronics Accessory Pouch"		"/google+redesign/"	0	1	
"7.19823E+18"	"Direct"	0	"United States"	"Kirkland"				1		"2017-05-31 00:00:00"	"1496254396"	"PAGE"			"$0.00"		"9182785"	"Google Women's Lightweight Microfleece Jacket"	"(not set)"	"(not set)"	"USD"					"Google Women's Vintage Hero Tee Platinum"		"/google+redesign/"	0	1	
"8.07987E+16"	"Organic Search"	0	"Italy"	"not available in demo dataset"				1		"2017-01-24 00:00:00"	"1485288762"	"PAGE"			"$0.00"		"9182599"	"Google Women's Long Sleeve Tee Lavender"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Pen Pencil & Highlighter Set"		"/google+redesign/"	0	1	
"2.99279E+18"	"Direct"	0	"United States"	"not available in demo dataset"				1		"2016-08-26 00:00:00"	"1472233265"	"PAGE"			"$0.00"		"9180792"	"20 oz Stainless Steel Insulated Tumbler"	"(not set)"	"(not set)"	"USD"					"Google Women's Short Sleeve V-Neck Tee Lavender"		"/google+redesign/"	0	1	
"8.98648E+18"	"Referral"	61726	"United States"	"New York"			62	5		"2016-11-07 00:00:00"	"1478556457"	"PAGE"			"$0.00"		"9182743"	"Google Men's Microfiber 1/4 Zip Pullover Blue/Indigo"	"(not set)"	"(not set)"	"USD"					"Nest Protect Smoke + CO White Battery Alarm-USA"		"/google+redesign/"	0	1	
"1.58107E+18"	"Direct"	0	"United States"	"New York"				1		"2017-02-17 00:00:00"	"1487370334"	"PAGE"			"$0.00"		"9182760"	"Google Women's Insulated Thermal Vest Navy"	"(not set)"	"(not set)"	"USD"					"BLM Sweatshirt"		"/google+redesign/"	0	1	
"6.34119E+18"	"Organic Search"	0	"United Kingdom"	"not available in demo dataset"				1		"2017-07-03 00:00:00"	"1499115717"	"PAGE"			"$0.00"		"9182723"	"Google Men's 100% Cotton Short Sleeve Hero Tee White"	"(not set)"	"(not set)"	"USD"					"Google Snapback Hat Black"		"/google+redesign/"	0	1	
"7.14941E+18"	"Organic Search"	147943	"New Zealand"	"not available in demo dataset"			148	2		"2016-11-12 00:00:00"	"1479014680"	"PAGE"			"$0.00"		"9183112"	"YouTube Men's Fleece Hoodie Black"	"(not set)"	"(not set)"	"USD"					"YouTube Twill Cap"		"/google+redesign/"	0	1	
"2.27242E+18"	"Direct"	0	"United States"	"not available in demo dataset"			61	4		"2017-03-17 00:00:00"	"1489765848"	"PAGE"			"$0.00"		"9180842"	"Maze Pen"	"(not set)"	"(not set)"	"USD"					"Google Men's Microfiber 1/4 Zip Pullover Blue/Indigo"		"/google+redesign/"	0	1	
"2.21262E+17"	"Organic Search"	167534	"Colombia"	"not available in demo dataset"			168	9		"2017-05-05 00:00:00"	"1494009320"	"PAGE"			"$0.00"		"9182575"	"Android Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"Android Men's Pep Rally Short Sleeve Tee Navy"		"/google+redesign/"	0	1	
"6.48234E+18"	"Direct"	0	"United States"	"not available in demo dataset"				1		"2017-05-20 00:00:00"	"1495312452"	"PAGE"			"$0.00"		"9183234"	"Nest¬Æ Learning Thermostat 3rd Gen-USA - Stainless Steel"	"(not set)"	"(not set)"	"USD"					"Waze Women's Typography Short Sleeve Tee"		"/google+redesign/"	0	1	
"9.75725E+17"	"Organic Search"	62797	"United States"	"not available in demo dataset"			78	6		"2017-05-11 00:00:00"	"1494549474"	"PAGE"			"$0.00"		"9182859"	"Google Toddler Raglan Shirt Blue Heather/Navy"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Malibu Sunglasses"		"/google+redesign/"	0	1	
"3.26246E+18"	"Organic Search"	83935	"United States"	"Los Angeles"			1043	3		"2017-05-23 00:00:00"	"1495597017"	"PAGE"			"$0.00"		"9184705"	"Waze Women's Typography Short Sleeve Tee"	"(not set)"	"(not set)"	"USD"					"YouTube Men's Fleece Hoodie Black"		"/google+redesign/"	0	1	
"5.38725E+18"	"Direct"	176771	"United States"	"Jersey City"			353	8		"2017-04-26 00:00:00"	"1493244227"	"PAGE"			"$0.00"		"9182737"	"Google Women's 3/4 Sleeve Baseball Raglan Heather/Black"	"(not set)"	"(not set)"	"USD"					"Google Accent Insulated Stainless Steel Bottle"		"/google+redesign/"	0	1	
"9.6959E+18"	"Direct"	0	"United States"	"Sunnyvale"				1		"2017-01-10 00:00:00"	"1484092931"	"PAGE"			"$0.00"		"9182859"	"Google Toddler Raglan Shirt Blue Heather/Navy"	"(not set)"	"(not set)"	"USD"					"Android Men's Take Charge Short Sleeve Tee Purple"		"/google+redesign/"	0	1	
"2.29023E+18"	"Direct"	0	"United States"	"Mountain View"			7	2	1	"2017-07-26 00:00:00"	"1501090425"	"PAGE"			"$0.00"		"9184720"	"Google Women's Short Sleeve Hero Tee Sky Blue"	"(not set)"	"(not set)"	"USD"					"25L Classic Rucksack"		"/google+redesign/"	0	1	
"2.99384E+18"	"Direct"	0	"United States"	"Los Angeles"				1		"2016-08-09 00:00:00"	"1470747420"	"PAGE"			"$0.00"		"9180861"	"Recycled Mouse Pad"	"(not set)"	"(not set)"	"USD"					"Google 3/4 Sleeve Raglan Henley Grey"		"/google+redesign/"	0	1	
"6.44386E+18"	"Direct"	0	"United States"	"Los Angeles"			11	2		"2016-12-05 00:00:00"	"1480954250"	"PAGE"			"$0.00"		"9182739"	"Google Men's Watershed Full Zip Hoodie Grey"	"(not set)"	"(not set)"	"USD"					"Google Men's Vintage Badge Tee White"		"/google+redesign/"	0	1	
"3.5854E+18"	"Organic Search"	63196	"United States"	"Santa Clara"			101	6		"2017-03-05 00:00:00"	"1488752908"	"PAGE"			"$0.00"		"9183202"	"Android Stretch Fit Hat Black"	"(not set)"	"(not set)"	"USD"					"20 oz Stainless Steel Insulated Tumbler"		"/google+redesign/"	0	1	
"9.47529E+17"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2017-03-20 00:00:00"	"1490010024"	"PAGE"			"$0.00"		"9182593"	"Google Men's Pullover Hoodie Grey"	"(not set)"	"(not set)"	"USD"					"Google Men's Vintage Badge Tee Black"		"/google+redesign/"	0	1	
"5.06172E+17"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2017-06-03 00:00:00"	"1496508076"	"PAGE"			"$0.00"		"9182575"	"Android Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"Google Flashlight"		"/google+redesign/"	0	1	
"9.46627E+18"	"Paid Search"	30594	"United States"	"not available in demo dataset"			31	2		"2017-06-19 00:00:00"	"1497884245"	"PAGE"			"$0.00"		"9183106"	"Google Women's Performance Hero Tee Gunmetal"	"(not set)"	"(not set)"	"USD"					"YouTube Women's Short Sleeve Hero Tee Charcoal"		"/google+redesign/"	0	1	
"1.85539E+18"	"Organic Search"	0	"Belgium"	"not available in demo dataset"			593	2		"2016-08-16 00:00:00"	"1471355389"	"PAGE"			"$0.00"		"10 31023"	"YouTube Unstructured Cap - Charcoal"	"YouTube"	"(not set)"	"USD"					"YouTube"		"/google+redesign/"	0	1	
"1.75607E+16"	"Organic Search"	44793	"United States"	"not available in demo dataset"			69	3	1	"2017-07-30 00:00:00"	"1501465964"	"PAGE"			"$0.00"		"9182765"	"Google Women's Convertible Vest-Jacket Sea Foam Green"	"(not set)"	"(not set)"	"USD"					"Google Executive Umbrella"		"/google+redesign/"	0	1	
"5.98195E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2016-11-20 00:00:00"	"1479692321"	"PAGE"			"$0.00"		"9180752"	"Android 24 oz Contigo Bottle"	"(not set)"	"(not set)"	"USD"					"26 oz Double Wall Insulated Bottle"		"/google+redesign/"	0	1	
"5.95913E+17"	"Organic Search"	0	"United States"	"Pittsburgh"			37	3		"2016-08-15 00:00:00"	"1471282561"	"PAGE"			"$0.00"		"9182721"	"Google Men's 100% Cotton Short Sleeve Hero Tee Black"	"(not set)"	"(not set)"	"USD"					"Google 22 oz Water Bottle"		"/google+redesign/"	0	1	
"8.50596E+18"	"Direct"	290072	"Japan"	"Yokohama"			290	6		"2016-10-08 00:00:00"	"1475980658"	"PAGE"			"$0.00"		"9182569"	"Google Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Windup Android"		"/google+redesign/"	0	1	
"3.26263E+18"	"Organic Search"	134138	"Canada"	"not available in demo dataset"			134	8		"2016-12-08 00:00:00"	"1481256794"	"PAGE"			"$0.00"		"9182723"	"Google Men's 100% Cotton Short Sleeve Hero Tee White"	"(not set)"	"(not set)"	"USD"					"YouTube Twill Cap"		"/google+redesign/"	0	1	
"2.69401E+18"	"Organic Search"	0	"United States"	"Mountain View"				1		"2017-05-16 00:00:00"	"1494977195"	"PAGE"			"$0.00"		"9182781"	"Google Women's Short Sleeve Hero Tee Black"	"(not set)"	"(not set)"	"USD"					"Waterproof Backpack"		"/google+redesign/"	0	1	
"4.66549E+18"	"Direct"	0	"United States"	"not available in demo dataset"				1		"2016-12-01 00:00:00"	"1480606491"	"PAGE"			"$0.00"		"9183234"	"Nest¬Æ Learning Thermostat 3rd Gen-USA - Stainless Steel"	"(not set)"	"(not set)"	"USD"					"Android 24 oz Contigo Bottle"		"/google+redesign/"	0	1	
"3.51787E+18"	"Organic Search"	0	"South Korea"	"not available in demo dataset"				1		"2016-10-28 00:00:00"	"1477647319"	"PAGE"			"$0.00"		"9180833"	"Rubber Grip Ballpoint Pen 4 Pack"	"(not set)"	"(not set)"	"USD"					"Google Electronics Accessory Pouch"		"/google+redesign/"	0	1	
"4.66161E+18"	"Direct"	0	"United States"	"San Jose"			14	2		"2016-12-02 00:00:00"	"1480714454"	"PAGE"			"$0.00"		"9183015"	"YouTube Onesie Heather"	"(not set)"	"(not set)"	"USD"					"Google Onesie Green"		"/google+redesign/"	0	1	
"5.05952E+18"	"Paid Search"	0	"United States"	"not available in demo dataset"				1		"2016-10-03 00:00:00"	"1475544630"	"PAGE"			"$0.00"		"9182994"	"Android 17oz Stainless Steel Sport Bottle"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/22 oz Android Bottle"		"/google+redesign/"	0	1	
"1.0304E+18"	"Organic Search"	0	"Malaysia"	"not available in demo dataset"				1	1	"2017-07-07 00:00:00"	"1499412876"	"PAGE"			"$0.00"		"9184734"	"Nest¬Æ Learning Thermostat 3rd Gen-USA - Copper"	"(not set)"	"(not set)"	"USD"					"Google Power Bank"		"/google+redesign/"	0	1	
"7.62733E+18"	"Direct"	27590	"United States"	"not available in demo dataset"			28	3		"2016-10-27 00:00:00"	"1477601201"	"PAGE"			"$0.00"		"9182771"	"Google Women's 1/4 Zip Jacket Charcoal"	"(not set)"	"(not set)"	"USD"					"Google Women's Lightweight Microfleece Jacket"		"/google+redesign/"	0	1	
"4.37554E+18"	"Referral"	16758	"Czechia"	"not available in demo dataset"			17	2		"2017-04-24 00:00:00"	"1493021237"	"PAGE"			"$0.00"		"9181573"	"Google Snapback Hat Black"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/22 oz Android Bottle"		"/google+redesign/"	0	1	
"7.00729E+18"	"Organic Search"	0	"United States"	"Mountain View"				1		"2016-12-14 00:00:00"	"1481748700"	"PAGE"			"$0.00"		"9182581"	"Google Women's Fleece Hoodie"	"(not set)"	"(not set)"	"USD"					"Google Bluetooth Speaker-Power Bank"		"/google+redesign/"	0	1	
"1.56748E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2017-06-01 00:00:00"	"1496362834"	"PAGE"			"$0.00"		"9182739"	"Google Men's Watershed Full Zip Hoodie Grey"	"(not set)"	"(not set)"	"USD"					"Google Snapback Hat Black"		"/google+redesign/"	0	1	
"1.52043E+18"	"Organic Search"	2331442	"Peru"	"(not set)"			2331	9		"2017-04-23 00:00:00"	"1493007061"	"PAGE"			"$0.00"		"9180766"	"Sport Bag"	"(not set)"	"(not set)"	"USD"					"YouTube Twill Cap"		"/google+redesign/"	0	1	
"6.29328E+18"	"Organic Search"	53036	"United States"	"San Francisco"			53	2		"2016-09-08 00:00:00"	"1473389839"	"PAGE"			"$0.00"		"9182721"	"Google Men's 100% Cotton Short Sleeve Hero Tee Black"	"(not set)"	"(not set)"	"USD"					"Leather and Metal Ballpoint Pen"		"/google+redesign/"	0	1	
"9.99162E+17"	"Organic Search"	15824	"Indonesia"	"not available in demo dataset"			233	5		"2017-02-14 00:00:00"	"1487080772"	"PAGE"			"$0.00"		"9182757"	"Google Men's Performance Polo Grey/Black"	"(not set)"	"(not set)"	"USD"					"Google Men's Microfiber 1/4 Zip Pullover Blue/Indigo"		"/google+redesign/"	0	1	
"9.97014E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"			35	3		"2017-01-08 00:00:00"	"1483925527"	"PAGE"			"$0.00"		"9184620"	"Google Men's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"Google Men's Convertible Vest-Jacket Pewter"		"/google+redesign/"	0	1	
"3.21243E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"			29	2		"2017-03-03 00:00:00"	"1488588904"	"PAGE"			"$0.00"		"9182778"	"Google Women's Softshell Jacket Black/Grey"	"(not set)"	"(not set)"	"USD"					"Google Women's Yoga Pants"		"/google+redesign/"	0	1	
"6.83104E+18"	"Direct"	12054	"United States"	"New York"			12	2	1	"2017-07-05 00:00:00"	"1499288168"	"PAGE"			"$0.00"		"9182714"	"Google Men's Long Sleeve Raglan Ocean Blue"	"(not set)"	"(not set)"	"USD"					"Google Alpine Style Backpack"		"/google+redesign/"	0	1	
"3.89765E+18"	"Organic Search"	1709787	"Spain"	"Madrid"			1710	2		"2017-06-27 00:00:00"	"1498599747"	"PAGE"			"$0.00"		"9182772"	"Google Women's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"5.35325E+18"	"Direct"	0	"Thailand"	"Bangkok"				1		"2016-08-30 00:00:00"	"1472564302"	"PAGE"			"$0.00"		"9180788"	"Insulated Bottle"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/7 Dog Safe Flyer"		"/google+redesign/"	0	1	
"7.24287E+18"	"Organic Search"	0	"Sri Lanka"	"not available in demo dataset"				1		"2017-03-09 00:00:00"	"1489054239"	"PAGE"			"$0.00"		"9183229"	"Nest¬Æ Cam Outdoor Security Camera - USA"	"(not set)"	"(not set)"	"USD"					"Google Laptop and Cell Phone Stickers"		"/google+redesign/"	0	1	
"9.12271E+18"	"Direct"	0	"Brazil"	"not available in demo dataset"			16	4	1	"2017-07-04 00:00:00"	"1499186292"	"PAGE"			"$0.00"		"9182751"	"Google Men's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"Google Alpine Style Backpack"		"/google+redesign/"	0	1	
"3.86418E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2016-12-05 00:00:00"	"1480947894"	"PAGE"			"$0.00"		"9180757"	"Yoga Block"	"(not set)"	"(not set)"	"USD"					"Spiral Notebook and Pen Set"		"/google+redesign/"	0	1	
"7.42796E+17"	"Organic Search"	0	"United Kingdom"	"not available in demo dataset"			88	5		"2017-05-28 00:00:00"	"1496014755"	"PAGE"			"$0.00"		"9183106"	"Google Women's Performance Hero Tee Gunmetal"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Pen Pencil & Highlighter Set"		"/google+redesign/"	0	1	
"7.17158E+18"	"Organic Search"	98498	"United Kingdom"	"not available in demo dataset"			141	5		"2017-02-05 00:00:00"	"1486341996"	"PAGE"			"$0.00"		"9182723"	"Google Men's 100% Cotton Short Sleeve Hero Tee White"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/14 oz Jumbo Ceramic Mug"		"/google+redesign/"	0	1	
"6.33313E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2017-02-22 00:00:00"	"1487781572"	"PAGE"			"$0.00"		"9180766"	"Sport Bag"	"(not set)"	"(not set)"	"USD"					"Google Power Bank"		"/google+redesign/"	0	1	
"6.75533E+18"	"Organic Search"	0	"Sweden"	"not available in demo dataset"			851	6		"2016-12-08 00:00:00"	"1481198761"	"PAGE"			"$0.00"		"9180797"	"Google 22 oz Water Bottle"	"(not set)"	"(not set)"	"USD"					"Nest¬Æ Learning Thermostat 3rd Gen-USA - Stainless Steel"		"/google+redesign/"	0	1	
"9.06868E+18"	"Organic Search"	0	"United Kingdom"	"London"				1		"2017-06-16 00:00:00"	"1497620163"	"PAGE"			"$0.00"		"9183106"	"Google Women's Performance Hero Tee Gunmetal"	"(not set)"	"(not set)"	"USD"					"Google Ballpoint Pen Black"		"/google+redesign/"	0	1	
"9.80128E+18"	"Organic Search"	447271	"United States"	"not available in demo dataset"			447	5		"2016-08-14 00:00:00"	"1471200442"	"PAGE"			"$0.00"		"9182635"	"Google Women's Short Sleeve V-Neck Tee Black"	"(not set)"	"(not set)"	"USD"					"Google Men's Bayside Graphic Tee"		"/google+redesign/"	0	1	
"6.54074E+18"	"Organic Search"	115276	"Israel"	"not available in demo dataset"			652	5		"2016-09-20 00:00:00"	"1474399014"	"PAGE"			"$0.00"		"9182724"	"Google Men's 100% Cotton Short Sleeve Hero Tee Red"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/22 oz Android Bottle"		"/google+redesign/"	0	1	
"1.27274E+17"	"Direct"	49383	"United States"	"Mountain View"			61	5		"2017-02-07 00:00:00"	"1486514643"	"PAGE"			"$0.00"		"9180766"	"Sport Bag"	"(not set)"	"(not set)"	"USD"					"Aluminum Handy Emergency Flashlight"		"/google+redesign/"	0	1	
"5.52374E+18"	"Direct"	31194	"United States"	"Los Angeles"			580	5		"2016-11-01 00:00:00"	"1478019871"	"PAGE"			"$0.00"		"9182736"	"Google Men's Heavyweight Long Sleeve Hero Tee Navy"	"(not set)"	"(not set)"	"USD"					"Waterproof Backpack"		"/google+redesign/"	0	1	
"6.20749E+18"	"Referral"	44156	"United States"	"Los Angeles"			114	5		"2016-12-20 00:00:00"	"1482295331"	"PAGE"			"$0.00"		"9183228"	"Nest¬Æ Cam Indoor Security Camera - USA"	"(not set)"	"(not set)"	"USD"					"Nest¬Æ Learning Thermostat 3rd Gen-USA - Stainless Steel"		"/google+redesign/"	0	1	
"6.81014E+18"	"Direct"	25255	"Israel"	"Tel Aviv-Yafo"			25	4		"2017-05-22 00:00:00"	"1495466817"	"PAGE"			"$0.00"		"9182784"	"Google Women's Short Sleeve Hero Tee White"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/7 Dog Safe Flyer"		"/google+redesign/"	0	1	
"5.57679E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"			100	5		"2016-11-07 00:00:00"	"1478559989"	"PAGE"			"$0.00"		"9182722"	"Google Men's 100% Cotton Short Sleeve Hero Tee Navy"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"4.92212E+18"	"Paid Search"	68763	"United States"	"Irvine"			69	5		"2016-12-20 00:00:00"	"1482270791"	"PAGE"			"$0.00"		"9180766"	"Sport Bag"	"(not set)"	"(not set)"	"USD"					"Google Men's Zip Hoodie"		"/google+redesign/"	0	1	
"3.53667E+18"	"Organic Search"	29579	"Netherlands"	"not available in demo dataset"			109	6		"2016-09-04 00:00:00"	"1473008796"	"PAGE"			"$0.00"		"9180854"	"Leatherette Journal"	"(not set)"	"(not set)"	"USD"					"Google Laptop Backpack"		"/google+redesign/"	0	1	
"4.73512E+18"	"Organic Search"	205982	"Australia"	"Melbourne"			206	10		"2016-08-18 00:00:00"	"1471563248"	"PAGE"			"$0.00"		"9182581"	"Google Women's Fleece Hoodie"	"(not set)"	"(not set)"	"USD"					"YouTube Men's Vintage Tank"		"/google+redesign/"	0	1	
"6.816E+18"	"Referral"	250598	"United States"	"Mountain View"			251	8		"2017-01-26 00:00:00"	"1485456428"	"PAGE"			"$0.00"		"9182714"	"Google Men's Long Sleeve Raglan Ocean Blue"	"(not set)"	"(not set)"	"USD"					"Google Laptop Backpack"		"/google+redesign/"	0	1	
"8.81525E+18"	"Direct"	176719	"United States"	"Salem"			177	4		"2017-01-18 00:00:00"	"1484759545"	"PAGE"			"$0.00"		"9182750"	"Google Men's Performance 1/4 Zip Pullover Heather/Black"	"(not set)"	"(not set)"	"USD"					"Google Infant Short Sleeve Tee Cornflower Blue"		"/google+redesign/"	0	1	
"6.20446E+18"	"Referral"	72937	"United States"	"Chicago"			164	6		"2017-06-21 00:00:00"	"1498059748"	"PAGE"			"$0.00"		"9184734"	"Nest¬Æ Learning Thermostat 3rd Gen-USA - Copper"	"(not set)"	"(not set)"	"USD"					"Women's YouTube Short Sleeve Hero Tee Black"		"/google+redesign/"	0	1	
"5.33745E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"			28	2		"2017-06-19 00:00:00"	"1497918923"	"PAGE"			"$0.00"		"9184720"	"Google Women's Short Sleeve Hero Tee Sky Blue"	"(not set)"	"(not set)"	"USD"					"Google Flashlight"		"/google+redesign/"	0	1	
"9.30833E+18"	"Direct"	0	"United States"	"Mountain View"				1		"2017-04-22 00:00:00"	"1492901322"	"PAGE"			"$0.00"		"9182714"	"Google Men's Long Sleeve Raglan Ocean Blue"	"(not set)"	"(not set)"	"USD"					"Google Laptop Backpack"		"/google+redesign/"	0	1	
"8.78176E+18"	"Direct"	243627	"Peru"	"(not set)"			511	3		"2017-07-03 00:00:00"	"1499135188"	"PAGE"			"$0.00"		"9182772"	"Google Women's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"Android Wool Heather Cap Heather/Black"		"/google+redesign/"	0	1	
"3.73921E+18"	"Organic Search"	92656	"Denmark"	"not available in demo dataset"			132	4		"2016-12-14 00:00:00"	"1481725497"	"PAGE"			"$0.00"		"9182722"	"Google Men's 100% Cotton Short Sleeve Hero Tee Navy"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/24 oz YouTube Sergeant Stripe Bottle"		"/google+redesign/"	0	1	
"5.15102E+18"	"Referral"	113921	"United States"	"not available in demo dataset"			114	3		"2017-06-16 00:00:00"	"1497625884"	"PAGE"			"$0.00"		"9182722"	"Google Men's 100% Cotton Short Sleeve Hero Tee Navy"	"(not set)"	"(not set)"	"USD"					"YouTube Women's Short Sleeve Hero Tee Charcoal"		"/google+redesign/"	0	1	
"9.60475E+18"	"Organic Search"	23520	"South Korea"	"not available in demo dataset"			24	3		"2017-02-14 00:00:00"	"1487093181"	"PAGE"			"$0.00"		"9182569"	"Google Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"Google Electronics Accessory Pouch"		"/google+redesign/"	0	1	
"8.23578E+18"	"Referral"	5444	"Australia"	"Brisbane"			115	6		"2017-06-12 00:00:00"	"1497325346"	"PAGE"			"$0.00"		"9182743"	"Google Men's Microfiber 1/4 Zip Pullover Blue/Indigo"	"(not set)"	"(not set)"	"USD"					"Google Women's 3/4 Sleeve Baseball Raglan Heather/Black"		"/google+redesign/"	0	1	
"5.8261E+18"	"Direct"	0	"United States"	"not available in demo dataset"				1	1	"2017-07-27 00:00:00"	"1501168131"	"PAGE"			"$0.00"		"9182785"	"Google Women's Lightweight Microfleece Jacket"	"(not set)"	"(not set)"	"USD"					"Google Alpine Style Backpack"		"/google+redesign/"	0	1	
"9.04469E+18"	"Organic Search"	118780	"United States"	"not available in demo dataset"			311	12		"2017-03-25 00:00:00"	"1490505907"	"PAGE"			"$0.00"		"9182663"	"Google Women's Short Sleeve Badge Tee Red Heather"	"(not set)"	"(not set)"	"USD"					"YouTube Men's Long Sleeve Pullover Badge Tee Heather"		"/google+redesign/"	0	1	
"9.03184E+18"	"Organic Search"	22021	"United States"	"not available in demo dataset"			49	3		"2017-01-07 00:00:00"	"1483816673"	"PAGE"			"$0.00"		"9182658"	"Google Women's Short Sleeve Hero Tee Sky Blue"	"(not set)"	"(not set)"	"USD"					"26 oz Double Wall Insulated Bottle"		"/google+redesign/"	0	1	
"6.6716E+18"	"Paid Search"	222698	"United States"	"not available in demo dataset"			287	9		"2016-12-13 00:00:00"	"1481646304"	"PAGE"			"$0.00"		"9182575"	"Android Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"Google Insulated Stainless Steel Bottle"		"/google+redesign/"	0	1	
"1.66912E+18"	"Direct"	0	"Canada"	"Toronto"				1		"2016-08-23 00:00:00"	"1471992601"	"PAGE"			"$0.00"		"9180871"	"Google Collapsible Pet Bowl"	"(not set)"	"(not set)"	"USD"					"Android 24 oz Contigo Bottle"		"/google+redesign/"	0	1	
"4.04442E+18"	"Organic Search"	0	"United Kingdom"	"not available in demo dataset"			41	2		"2017-01-24 00:00:00"	"1485271609"	"PAGE"			"$0.00"		"9182785"	"Google Women's Lightweight Microfleece Jacket"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"8.97012E+18"	"Organic Search"	8993	"United States"	"not available in demo dataset"			9	2		"2016-11-17 00:00:00"	"1479413439"	"PAGE"			"$0.00"		"9180819"	"Google Laptop and Cell Phone Stickers"	"(not set)"	"(not set)"	"USD"					"Gel Roller Pen"		"/google+redesign/"	0	1	
"4.73448E+18"	"Organic Search"	239975	"Japan"	"not available in demo dataset"			1471	3		"2017-02-13 00:00:00"	"1487057106"	"PAGE"			"$0.00"		"9182750"	"Google Men's Performance 1/4 Zip Pullover Heather/Black"	"(not set)"	"(not set)"	"USD"					"Google Twill Cap"		"/google+redesign/"	0	1	
"6.15309E+17"	"Organic Search"	0	"United Kingdom"	"London"				1		"2017-02-15 00:00:00"	"1487199840"	"PAGE"			"$0.00"		"9181573"	"Google Snapback Hat Black"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"3.86932E+18"	"Organic Search"	138167	"United States"	"New York"			268	17		"2017-05-27 00:00:00"	"1495879247"	"PAGE"			"$0.00"		"9182785"	"Google Women's Lightweight Microfleece Jacket"	"(not set)"	"(not set)"	"USD"					"Google Men's Zip Hoodie"		"/google+redesign/"	0	1	
"4.09371E+18"	"Direct"	932486	"United States"	"Mountain View"			932	6		"2016-12-05 00:00:00"	"1480976767"	"PAGE"			"$0.00"		"9182751"	"Google Men's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"Google 17oz Stainless Steel Sport Bottle"		"/google+redesign/"	0	1	
"9.98875E+16"	"Organic Search"	22020	"Netherlands"	"not available in demo dataset"			1172	9		"2016-11-15 00:00:00"	"1479227391"	"PAGE"			"$0.00"		"9182593"	"Google Men's Pullover Hoodie Grey"	"(not set)"	"(not set)"	"USD"					"Google Tube Power Bank"		"/google+redesign/"	0	1	
"4.59175E+17"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2016-12-07 00:00:00"	"1481162309"	"PAGE"			"$0.00"		"9180840"	"Satin Black Ballpoint Pen"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Pen Pencil & Highlighter Set"		"/google+redesign/"	0	1	
"8.91027E+18"	"Direct"	0	"United States"	"New York"				1		"2017-06-05 00:00:00"	"1496675203"	"PAGE"			"$0.00"		"9182785"	"Google Women's Lightweight Microfleece Jacket"	"(not set)"	"(not set)"	"USD"					"Android Lifted Men's Short Sleeve Tee Blue"		"/google+redesign/"	0	1	
"9.94914E+18"	"Referral"	270	"Canada"	"not available in demo dataset"			77	5		"2016-08-15 00:00:00"	"1471310024"	"PAGE"			"$0.00"		"9180751"	"Android 24 oz Contigo Bottle"	"(not set)"	"(not set)"	"USD"					"Google Laptop and Cell Phone Stickers"		"/google+redesign/"	0	1	
"3.7379E+18"	"Organic Search"	0	"United States"	"Sunnyvale"			16	2		"2017-05-16 00:00:00"	"1494962847"	"PAGE"			"$0.00"		"9182781"	"Google Women's Short Sleeve Hero Tee Black"	"(not set)"	"(not set)"	"USD"					"Google Men's Bike Short Sleeve Tee Charcoal"		"/google+redesign/"	0	1	
"8.51198E+18"	"Organic Search"	10489	"United States"	"not available in demo dataset"			10	2		"2017-02-15 00:00:00"	"1487185316"	"PAGE"			"$0.00"		"9182750"	"Google Men's Performance 1/4 Zip Pullover Heather/Black"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"7.84454E+17"	"Direct"	0	"United States"	"New York"				1		"2017-06-23 00:00:00"	"1498234601"	"PAGE"			"$0.00"		"9184620"	"Google Men's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"BLM Sweatshirt"		"/google+redesign/"	0	1	
"7.71821E+18"	"Organic Search"	0	"Germany"	"not available in demo dataset"				1		"2017-01-23 00:00:00"	"1485169008"	"PAGE"			"$0.00"		"9182785"	"Google Women's Lightweight Microfleece Jacket"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"3.34328E+18"	"Organic Search"	0	"India"	"Pune"				1	1	"2017-07-19 00:00:00"	"1500456946"	"PAGE"			"$0.00"		"9182788"	"Yoga Mat"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"6.00273E+18"	"Organic Search"	18175	"United States"	"New York"			18	4		"2016-09-29 00:00:00"	"1475169067"	"PAGE"			"$0.00"		"9180760"	"Electronics Accessory Pouch"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/22 oz YouTube Bottle Infuser"		"/google+redesign/"	0	1	
"7.04594E+17"	"Organic Search"	31511	"Indonesia"	"Jakarta"			32	2		"2017-03-31 00:00:00"	"1490961862"	"PAGE"			"$0.00"		"9182771"	"Google Women's 1/4 Zip Jacket Charcoal"	"(not set)"	"(not set)"	"USD"					"Google Men's Zip Hoodie"		"/google+redesign/"	0	1	
"7.56871E+17"	"Organic Search"	22498	"United States"	"Los Angeles"			35	3		"2017-06-08 00:00:00"	"1496971055"	"PAGE"			"$0.00"		"9182658"	"Google Women's Short Sleeve Hero Tee Sky Blue"	"(not set)"	"(not set)"	"USD"					"Waze Dress Socks"		"/google+redesign/"	0	1	
"7.68857E+18"	"Organic Search"	34047	"Ireland"	"Dublin"			116	4		"2017-03-16 00:00:00"	"1489683754"	"PAGE"			"$0.00"		"9184733"	"Nest¬Æ Learning Thermostat 3rd Gen-USA - White"	"(not set)"	"(not set)"	"USD"					"YouTube Onesie Heather"		"/google+redesign/"	0	1	
"8.69344E+18"	"Organic Search"	401353	"United States"	"not available in demo dataset"			458	7		"2017-06-12 00:00:00"	"1497301839"	"PAGE"			"$0.00"		"9180793"	"26 oz Double Wall Insulated Bottle"	"(not set)"	"(not set)"	"USD"					"Google Women's V-Neck Tee Charcoal"		"/google+redesign/"	0	1	
"8.95835E+18"	"Organic Search"	0	"United States"	"San Diego"				1		"2017-04-26 00:00:00"	"1493218676"	"PAGE"			"$0.00"		"9182721"	"Google Men's 100% Cotton Short Sleeve Hero Tee Black"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"4.74731E+18"	"Organic Search"	63989	"United States"	"Jersey City"			64	4		"2017-06-17 00:00:00"	"1497718336"	"PAGE"			"$0.00"		"9184677"	"Google 25 oz Red Stainless Steel Bottle"	"(not set)"	"(not set)"	"USD"					"Google Laptop Backpack"		"/google+redesign/"	0	1	
"1.551E+18"	"Organic Search"	0	"Thailand"	"not available in demo dataset"				1		"2016-09-03 00:00:00"	"1472905703"	"PAGE"			"$0.00"		"9180781"	"Suitcase Organizer Cubes"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Maze Pen"		"/google+redesign/"	0	1	
"2.50768E+18"	"Direct"	0	"United States"	"San Francisco"				1		"2017-02-15 00:00:00"	"1487187984"	"PAGE"			"$0.00"		"9182723"	"Google Men's 100% Cotton Short Sleeve Hero Tee White"	"(not set)"	"(not set)"	"USD"					"BLM Sweatshirt"		"/google+redesign/"	0	1	
"6.50132E+18"	"Direct"	10327	"Canada"	"not available in demo dataset"			16	2		"2017-05-01 00:00:00"	"1493645442"	"PAGE"			"$0.00"		"9184737"	"Waze Pack of 9 Decal Set"	"(not set)"	"(not set)"	"USD"					"Google 17oz Stainless Steel Sport Bottle"		"/google+redesign/"	0	1	
"9.65953E+18"	"Organic Search"	0	"United States"	"San Francisco"				1		"2017-03-26 00:00:00"	"1490556622"	"PAGE"			"$0.00"		"9182581"	"Google Women's Fleece Hoodie"	"(not set)"	"(not set)"	"USD"					"Android RFID Journal"		"/google+redesign/"	0	1	
"4.38973E+18"	"Organic Search"	0	"India"	"Ahmedabad"				1		"2017-06-26 00:00:00"	"1498474703"	"PAGE"			"$0.00"		"9182883"	"Google Youth Short Sleeve T-shirt Royal Blue"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Windup Android"		"/google+redesign/"	0	1	
"4.81375E+18"	"Referral"	58577	"United States"	"San Francisco"			59	4		"2016-08-16 00:00:00"	"1471371172"	"PAGE"			"$0.00"		"9182873"	"Android Toddler Short Sleeve T-shirt Pink"	"(not set)"	"(not set)"	"USD"					"Google Toddler Hoodie Royal Blue"		"/google+redesign/"	0	1	
"2.51537E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2017-04-23 00:00:00"	"1493005096"	"PAGE"			"$0.00"		"9184733"	"Nest¬Æ Learning Thermostat 3rd Gen-USA - White"	"(not set)"	"(not set)"	"USD"					"Google Men's Around The Block Short Sleeve Tee Ash"		"/google+redesign/"	0	1	
"9.5646E+17"	"Organic Search"	38083	"Canada"	"not available in demo dataset"			185	5		"2017-03-26 00:00:00"	"1490578242"	"PAGE"			"$0.00"		"9181138"	"Google Rucksack"	"(not set)"	"(not set)"	"USD"					"25L Classic Rucksack"		"/google+redesign/"	0	1	
"3.22797E+18"	"Organic Search"	41070	"United States"	"New York"			77	4		"2017-02-28 00:00:00"	"1488339324"	"PAGE"			"$0.00"		"9182772"	"Google Women's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"Android Men's Take Charge Short Sleeve Tee Purple"		"/google+redesign/"	0	1	
"4.49133E+18"	"Organic Search"	0	"India"	"not available in demo dataset"				1		"2016-12-08 00:00:00"	"1481208951"	"PAGE"			"$0.00"		"9180797"	"Google 22 oz Water Bottle"	"(not set)"	"(not set)"	"USD"					"Nest¬Æ Learning Thermostat 3rd Gen-USA - Stainless Steel"		"/google+redesign/"	0	1	
"8.09789E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2016-10-08 00:00:00"	"1475970149"	"PAGE"			"$0.00"		"9182593"	"Google Men's Pullover Hoodie"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Malibu Sunglasses"		"/google+redesign/"	0	1	
"7.21055E+18"	"Referral"	92737	"United States"	"San Jose"			280	8		"2016-12-15 00:00:00"	"1481828130"	"PAGE"			"$0.00"		"9182575"	"Android Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"Bluetooth Headphones"		"/google+redesign/"	0	1	
"3.62489E+18"	"Paid Search"	250676	"United States"	"Mountain View"			1082	12		"2016-11-18 00:00:00"	"1479516330"	"PAGE"			"$0.00"		"9180801"	"Engraved Ceramic Google Mug"	"(not set)"	"(not set)"	"USD"					"Waterproof Backpack"		"/google+redesign/"	0	1	
"9.82703E+18"	"Organic Search"	103037	"United States"	"Los Angeles"			103	5		"2016-10-25 00:00:00"	"1477414514"	"PAGE"			"$0.00"		"9182722"	"Google Men's 100% Cotton Short Sleeve Hero Tee Navy"	"(not set)"	"(not set)"	"USD"					"Google 17oz Stainless Steel Sport Bottle"		"/google+redesign/"	0	1	
"6.9736E+18"	"Organic Search"	0	"Denmark"	"not available in demo dataset"			8	2		"2016-09-23 00:00:00"	"1474617283"	"PAGE"			"$0.00"		"9182722"	"Google Men's 100% Cotton Short Sleeve Hero Tee Navy"	"(not set)"	"(not set)"	"USD"					"Google Electronics Accessory Pouch"		"/google+redesign/"	0	1	
"9.7263E+18"	"Organic Search"	0	"United States"	"Mountain View"			995	6		"2017-04-08 00:00:00"	"1491713474"	"PAGE"			"$0.00"		"9182771"	"Google Women's 1/4 Zip Jacket Charcoal"	"(not set)"	"(not set)"	"USD"					"Google Alpine Style Backpack"		"/google+redesign/"	0	1	
"3.90177E+18"	"Organic Search"	798447	"Greece"	"not available in demo dataset"			821	22		"2017-01-22 00:00:00"	"1485130005"	"PAGE"			"$0.00"		"9182785"	"Google Women's Lightweight Microfleece Jacket"	"(not set)"	"(not set)"	"USD"					"Google Luggage Tag"		"/google+redesign/"	0	1	
"3.64279E+18"	"Referral"	73938	"Mexico"	"not available in demo dataset"			198	9		"2016-12-25 00:00:00"	"1482700133"	"PAGE"			"$0.00"		"9183234"	"Nest¬Æ Learning Thermostat 3rd Gen-USA - Stainless Steel"	"(not set)"	"(not set)"	"USD"					"Google Rucksack"		"/google+redesign/"	0	1	
"1.29227E+18"	"Referral"	32192	"United States"	"San Jose"			307	9	11	"2017-07-07 00:00:00"	"1499496400"	"PAGE"			"$0.00"		"9182784"	"Google Women's Short Sleeve Hero Tee White"	"(not set)"	"(not set)"	"USD"					"Nest Cam Outdoor Security Camera - USA"		"/google+redesign/"	0	1	
"9.59877E+16"	"Direct"	74901	"United States"	"Sunnyvale"			84	6		"2016-08-30 00:00:00"	"1472588065"	"PAGE"			"$0.00"		"9180824"	"Foam Can and Bottle Cooler"	"(not set)"	"(not set)"	"USD"					"Google Men's Airflow 1/4 Zip Pullover Black"		"/google+redesign/"	0	1	
"8.64081E+17"	"Organic Search"	0	"Romania"	"not available in demo dataset"			143	7		"2017-06-28 00:00:00"	"1498655772"	"PAGE"			"$0.00"		"9180754"	"8 pc Android Sticker Sheet"	"(not set)"	"(not set)"	"USD"					"Waze Baby on Board Window Decal"		"/google+redesign/"	0	1	
"9.50676E+17"	"Organic Search"	0	"United States"	"not available in demo dataset"			964	18	54	"2017-07-06 00:00:00"	"1499386598"	"PAGE"			"$0.00"		"9182859"	"Google Toddler Raglan Shirt Blue Heather/Navy"	"(not set)"	"(not set)"	"USD"					"20 oz Stainless Steel Insulated Tumbler"		"/google+redesign/"	0	1	
"2.76949E+18"	"Direct"	0	"United States"	"not available in demo dataset"				1		"2017-04-29 00:00:00"	"1493490053"	"PAGE"			"$0.00"		"9180766"	"Sport Bag"	"(not set)"	"(not set)"	"USD"					"BLM Sweatshirt"		"/google+redesign/"	0	1	
"6.13063E+18"	"Direct"	685675	"Sweden"	"Stockholm"			686	6		"2017-02-07 00:00:00"	"1486492974"	"PAGE"			"$0.00"		"9182663"	"Google Women's Short Sleeve Badge Tee Red Heather"	"(not set)"	"(not set)"	"USD"					"Google Men's Vintage Badge Tee White"		"/google+redesign/"	0	1	
"3.52335E+18"	"Organic Search"	0	"Germany"	"not available in demo dataset"			15	2		"2017-06-01 00:00:00"	"1496328579"	"PAGE"			"$0.00"		"9182575"	"Android Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"Google Flashlight"		"/google+redesign/"	0	1	
"5.55295E+18"	"Direct"	32260	"United States"	"not available in demo dataset"			121	4		"2017-07-02 00:00:00"	"1499021536"	"PAGE"			"$0.00"		"9180793"	"26 oz Double Wall Insulated Bottle"	"(not set)"	"(not set)"	"USD"					"Waze Mood Happy Window Decal"		"/google+redesign/"	0	1	
"3.80584E+17"	"Direct"	0	"India"	"not available in demo dataset"				1		"2017-03-20 00:00:00"	"1490023281"	"PAGE"			"$0.00"		"9181019"	"Google Tri-blend Hoodie Grey"	"(not set)"	"(not set)"	"USD"					"Google 4400mAh Power Bank"		"/google+redesign/"	0	1	
"5.17934E+18"	"Referral"	12939	"United States"	"Sunnyvale"			13	2		"2017-05-09 00:00:00"	"1494370315"	"PAGE"			"$0.00"		"9182739"	"Google Men's Watershed Full Zip Hoodie Grey"	"(not set)"	"(not set)"	"USD"					"Google 4400mAh Power Bank"		"/google+redesign/"	0	1	
"5.01132E+18"	"Organic Search"	74085	"United States"	"Los Angeles"			90	6		"2016-12-01 00:00:00"	"1480665506"	"PAGE"			"$0.00"		"9182721"	"Google Men's 100% Cotton Short Sleeve Hero Tee Black"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Compact Selfie Stick"		"/google+redesign/"	0	1	
"6.22625E+18"	"Organic Search"	0	"Ukraine"	"not available in demo dataset"				1		"2017-06-11 00:00:00"	"1497171605"	"PAGE"			"$0.00"		"9183106"	"Google Women's Performance Hero Tee Gunmetal"	"(not set)"	"(not set)"	"USD"					"Google Tri-blend Hoodie Grey"		"/google+redesign/"	0	1	
"7.40554E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2016-10-26 00:00:00"	"1477507034"	"PAGE"			"$0.00"		"9182771"	"Google Women's 1/4 Zip Jacket Charcoal"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/1 oz Hand Sanitizer"		"/google+redesign/"	0	1	
"8.17341E+18"	"Organic Search"	0	"Italy"	"not available in demo dataset"				1		"2017-04-07 00:00:00"	"1491592569"	"PAGE"			"$0.00"		"9182737"	"Google Women's 3/4 Sleeve Baseball Raglan Heather/Black"	"(not set)"	"(not set)"	"USD"					"YouTube Hard Cover Journal"		"/google+redesign/"	0	1	
"6.97715E+18"	"Direct"	24301	"United States"	"Mountain View"			95	6	2	"2017-07-31 00:00:00"	"1501553484"	"PAGE"			"$0.00"		"9183230"	"Nest¬Æ Protect Smoke + CO White Battery Alarm-USA"	"(not set)"	"(not set)"	"USD"					"Nest Cam Outdoor Security Camera - USA"		"/google+redesign/"	0	1	
"7.9802E+18"	"Referral"	253477	"United States"	"Sunnyvale"			343	7	3	"2017-07-17 00:00:00"	"1500333584"	"PAGE"			"$0.00"		"9182771"	"Google Women's 1/4 Zip Jacket Charcoal"	"(not set)"	"(not set)"	"USD"					"Google Women's Long Sleeve Blended Cardigan Charcoal"		"/google+redesign/"	0	1	
"4.85047E+18"	"Direct"	0	"United States"	"Marlboro"			34	2		"2017-06-06 00:00:00"	"1496780556"	"PAGE"			"$0.00"		"9182743"	"Google Men's Microfiber 1/4 Zip Pullover Blue/Indigo"	"(not set)"	"(not set)"	"USD"					"Google Women's 3/4 Sleeve Baseball Raglan Heather/Black"		"/google+redesign/"	0	1	
"9.86269E+18"	"Direct"	0	"Uganda"	"not available in demo dataset"				1		"2016-08-30 00:00:00"	"1472574631"	"PAGE"			"$0.00"		"9182760"	"Google Women's Insulated Thermal Vest Navy"	"(not set)"	"(not set)"	"USD"					"Google Men's Zip Hoodie"		"/google+redesign/"	0	1	
"8.48422E+18"	"Organic Search"	143318	"United States"	"not available in demo dataset"			450	5		"2017-06-02 00:00:00"	"1496456758"	"PAGE"			"$0.00"		"9181019"	"Google Tri-blend Hoodie Grey"	"(not set)"	"(not set)"	"USD"							"/storeitem.html"	0	1	
"8.86648E+17"	"Organic Search"	98524	"United States"	"not available in demo dataset"			99	5	1	"2017-07-26 00:00:00"	"1501137399"	"PAGE"			"$0.00"		"9183219"	"Google Leather Journal"	"(not set)"	"(not set)"	"USD"					"Keyboard DOT Sticker"		"/google+redesign/"	0	1	
"7.79598E+18"	"Organic Search"	226959	"United States"	"not available in demo dataset"			305	9		"2016-10-05 00:00:00"	"1475696604"	"PAGE"			"$0.00"		"9180797"	"Google 22 oz Water Bottle"	"(not set)"	"(not set)"	"USD"					"Recycled Paper Journal Set"		"/google+redesign/"	0	1	
"1.88217E+18"	"Direct"	0	"United States"	"San Francisco"			2	5	3	"2017-07-05 00:00:00"	"1499273937"	"PAGE"			"$0.00"		"9182717"	"Google Men's Short Sleeve Hero Tee Light Blue"	"(not set)"	"(not set)"	"USD"					"Google Men's Short Sleeve Badge Tee Charcoal"		"/google+redesign/"	0	1	
"2.68978E+18"	"Organic Search"	5757	"United States"	"not available in demo dataset"			6	2		"2017-05-12 00:00:00"	"1494642282"	"PAGE"			"$0.00"		"9182781"	"Google Women's Short Sleeve Hero Tee Black"	"(not set)"	"(not set)"	"USD"					"Google Ballpoint Pen Black"		"/google+redesign/"	0	1	
"2.11407E+18"	"Organic Search"	209437	"Italy"	"not available in demo dataset"			209	7		"2016-08-15 00:00:00"	"1471244725"	"PAGE"			"$0.00"		"9180793"	"26 oz Double Wall Insulated Bottle"	"(not set)"	"(not set)"	"USD"					"Google Laptop Backpack"		"/google+redesign/"	0	1	
"7.28208E+18"	"Organic Search"	0	"United States"	"Portland"				1		"2016-12-01 00:00:00"	"1480653228"	"PAGE"			"$0.00"		"9182771"	"Google Women's 1/4 Zip Jacket Charcoal"	"(not set)"	"(not set)"	"USD"					"Google Women's Fleece Hoodie"		"/google+redesign/"	0	1	
"2.26329E+18"	"Organic Search"	0	"United States"	"Palo Alto"			37	3		"2017-05-16 00:00:00"	"1494965651"	"PAGE"			"$0.00"		"9182750"	"Google Men's Performance 1/4 Zip Pullover Heather/Black"	"(not set)"	"(not set)"	"USD"					"Google Men's Bayside Graphic Tee"		"/google+redesign/"	0	1	
"8.56373E+18"	"Direct"	0	"United States"	"Mountain View"				1		"2017-02-17 00:00:00"	"1487369909"	"PAGE"			"$0.00"		"9182838"	"Google Toddler Short Sleeve T-shirt Yellow"	"(not set)"	"(not set)"	"USD"					"BLM Sweatshirt"		"/google+redesign/"	0	1	
"1.95753E+18"	"Direct"	0	"India"	"Mumbai"				1		"2016-10-02 00:00:00"	"1475393309"	"PAGE"			"$0.00"		"9182599"	"Google Women's Tee Purple"	"(not set)"	"(not set)"	"USD"					"Google Men's Zip Hoodie"		"/google+redesign/"	0	1	
"8.52948E+18"	"Referral"	65950	"Switzerland"	"Zurich"			130	4		"2017-04-07 00:00:00"	"1491570248"	"PAGE"			"$0.00"		"9182785"	"Google Women's Lightweight Microfleece Jacket"	"(not set)"	"(not set)"	"USD"					"Google 22 oz Water Bottle"		"/google+redesign/"	0	1	
"9.73852E+18"	"Organic Search"	35087	"Canada"	"not available in demo dataset"			586	4		"2017-03-08 00:00:00"	"1489008813"	"PAGE"			"$0.00"		"9180833"	"Rubber Grip Ballpoint Pen 4 Pack"	"(not set)"	"(not set)"	"USD"					"Google High Capacity 10,400mAh Charger"		"/google+redesign/"	0	1	
"9.15573E+18"	"Direct"	0	"United States"	"San Jose"			153	7		"2016-12-08 00:00:00"	"1481226796"	"PAGE"			"$0.00"		"9183235"	"Google Collapsible Duffel"	"(not set)"	"(not set)"	"USD"					"Google Men's Vintage Tank"		"/google+redesign/"	0	1	
"8.92226E+17"	"Organic Search"	0	"Ireland"	"not available in demo dataset"			14	2		"2017-04-08 00:00:00"	"1491676872"	"PAGE"			"$0.00"		"9182688"	"Google Women's V-Neck Tee Grey"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Pen Pencil & Highlighter Set"		"/google+redesign/"	0	1	
"4.94103E+18"	"Organic Search"	37758	"United States"	"not available in demo dataset"			78	6		"2016-10-28 00:00:00"	"1477667150"	"PAGE"			"$0.00"		"9182781"	"Google Women's Short Sleeve Hero Tee Black"	"(not set)"	"(not set)"	"USD"					"Google Men's Quilted Insulated Vest Battleship Grey"		"/google+redesign/"	0	1	
"4.74461E+18"	"Organic Search"	0	"Serbia"	"not available in demo dataset"				1		"2017-03-22 00:00:00"	"1490204253"	"PAGE"			"$0.00"		"9182859"	"Google Toddler Raglan Shirt Blue Heather/Navy"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Leatherette Journal"		"/google+redesign/"	0	1	
"4.96512E+17"	"Organic Search"	0	"United States"	"Mountain View"			30	3		"2017-02-28 00:00:00"	"1488326414"	"PAGE"			"$0.00"		"9180766"	"Sport Bag"	"(not set)"	"(not set)"	"USD"					"Google Power Bank"		"/google+redesign/"	0	1	
"1.16939E+18"	"Direct"	0	"Switzerland"	"not available in demo dataset"				1		"2016-10-23 00:00:00"	"1477236677"	"PAGE"			"$0.00"		"9182746"	"Google Men's Quilted Insulated Vest Battleship Grey"	"(not set)"	"(not set)"	"USD"					"YouTube Men's Fleece Hoodie Black"		"/google+redesign/"	0	1	
"7.89028E+18"	"Referral"	53143	"India"	"Bengaluru"			53	3		"2017-03-16 00:00:00"	"1489661616"	"PAGE"			"$0.00"		"9184735"	"Nest¬Æ Learning Thermostat 3rd Gen-USA"	"(not set)"	"(not set)"	"USD"					"Google Women's 1/4 Zip Jacket Charcoal"		"/google+redesign/"	0	1	
"4.24978E+18"	"Direct"	103530	"United States"	"not available in demo dataset"			104	5		"2016-12-05 00:00:00"	"1480975226"	"PAGE"			"$0.00"		"9184620"	"Google Men's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"Google Men's Watershed Full Zip Hoodie Grey"		"/google+redesign/"	0	1	
"4.93238E+18"	"Direct"	181240	"United States"	"Mountain View"			181	2		"2016-10-19 00:00:00"	"1476917473"	"PAGE"			"$0.00"		"10 52233"	"Sports Water Bottle"	"Drinkware"	"(not set)"	"USD"					"Drinkware"		"/google+redesign/"	0	1	
"6.35979E+17"	"Organic Search"	203753	"Venezuela"	"not available in demo dataset"			225	4		"2017-02-19 00:00:00"	"1487519118"	"PAGE"			"$0.00"		"9182761"	"Google Women's Yoga Jacket Black"	"(not set)"	"(not set)"	"USD"					"Google Wool Heather Cap Heather/Navy"		"/google+redesign/"	0	1	
"4.93238E+18"	"Direct"	0	"United States"	"Mountain View"				1		"2017-01-25 00:00:00"	"1485385531"	"PAGE"			"$0.00"		"10 52237"	"24oz USA Made Aluminum Bottle"	"Drinkware"	"(not set)"	"USD"					"Drinkware"		"/google+redesign/"	0	1	
"3.21235E+18"	"Organic Search"	0	"United States"	"San Jose"				1		"2017-06-09 00:00:00"	"1497055684"	"PAGE"			"$0.00"		"9182737"	"Google Women's 3/4 Sleeve Baseball Raglan Heather/Black"	"(not set)"	"(not set)"	"USD"					"Google Laptop Backpack"		"/google+redesign/"	0	1	
"2.55463E+18"	"Organic Search"	0	"France"	"Paris"				1		"2017-05-29 00:00:00"	"1496059126"	"PAGE"			"$0.00"		"9180752"	"Android 24 oz Contigo Bottle"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Malibu Sunglasses"		"/google+redesign/"	0	1	
"5.9948E+17"	"Organic Search"	0	"Lithuania"	"not available in demo dataset"				1		"2017-06-01 00:00:00"	"1496328482"	"PAGE"			"$0.00"		"9181573"	"Google Snapback Hat Black"	"(not set)"	"(not set)"	"USD"					"Google Flashlight"		"/google+redesign/"	0	1	
"9.01734E+18"	"Direct"	0	"Bangladesh"	"(not set)"				1		"2017-03-04 00:00:00"	"1488637866"	"PAGE"			"$0.00"		"9182784"	"Google Women's Short Sleeve Hero Tee White"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Maze Pen"		"/google+redesign/"	0	1	
"1.4863E+18"	"Organic Search"	0	"Canada"	"Sherbrooke"				1		"2017-03-10 00:00:00"	"1489156577"	"PAGE"			"$0.00"		"9180905"	"Google Men's Long Sleeve Raglan Ocean Blue"	"(not set)"	"(not set)"	"USD"					"Nest¬Æ Learning Thermostat 3rd Gen-USA - Stainless Steel"		"/google+redesign/"	0	1	
"4.38816E+18"	"Organic Search"	0	"India"	"not available in demo dataset"				1		"2016-10-10 00:00:00"	"1476088531"	"PAGE"			"$0.00"		"9182775"	"Google Women's Zip Hoodie Grey"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"9.42178E+18"	"Direct"	0	"United States"	"not available in demo dataset"				1		"2016-11-24 00:00:00"	"1480043889"	"PAGE"			"$0.00"		"9180829"	"Google Sunglasses"	"(not set)"	"(not set)"	"USD"					"YouTube Custom Decals"		"/google+redesign/"	0	1	
"5.29957E+18"	"Direct"	39118	"United States"	"San Jose"			105	4	1	"2017-07-19 00:00:00"	"1500495485"	"PAGE"			"$0.00"		"9182765"	"Google Women's Convertible Vest-Jacket Sea Foam Green"	"(not set)"	"(not set)"	"USD"					"YouTube Men's Short Sleeve Hero Tee Charcoal"		"/google+redesign/"	0	1	
"8.99897E+17"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2017-03-08 00:00:00"	"1488987098"	"PAGE"			"$0.00"		"9182750"	"Google Men's Performance 1/4 Zip Pullover Heather/Black"	"(not set)"	"(not set)"	"USD"					"Google 22 oz Water Bottle"		"/google+redesign/"	0	1	
"2.79208E+18"	"Direct"	638	"United States"	"not available in demo dataset"			1	2		"2017-05-19 00:00:00"	"1495228355"	"PAGE"			"$0.00"		"9182575"	"Android Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"1.95812E+17"	"Direct"	0	"Vietnam"	"Ho Chi Minh City"				1		"2017-03-03 00:00:00"	"1488607374"	"PAGE"			"$0.00"		"9182775"	"Google Women's Zip Hoodie Grey"	"(not set)"	"(not set)"	"USD"					"Google Car Clip Phone Holder"		"/google+redesign/"	0	1	
"9.31239E+18"	"Organic Search"	128828	"United States"	"not available in demo dataset"			129	2		"2016-12-06 00:00:00"	"1481078671"	"PAGE"			"$0.00"		"9183234"	"Nest¬Æ Learning Thermostat 3rd Gen-USA - Stainless Steel"	"(not set)"	"(not set)"	"USD"					"Ballpoint Stylus Pen"		"/google+redesign/"	0	1	
"9.54429E+17"	"Direct"	0	"United States"	"New York"			202	2		"2017-02-20 00:00:00"	"1487611114"	"PAGE"			"$0.00"		"9182760"	"Google Women's Insulated Thermal Vest Navy"	"(not set)"	"(not set)"	"USD"					"BLM Sweatshirt"		"/google+redesign/"	0	1	
"7.12229E+18"	"Organic Search"	0	"Slovakia"	"Bratislava"				1		"2017-05-01 00:00:00"	"1493639162"	"PAGE"			"$0.00"		"9184734"	"Nest¬Æ Learning Thermostat 3rd Gen-USA - Copper"	"(not set)"	"(not set)"	"USD"					"Google Zipper-front Sports Bag"		"/google+redesign/"	0	1	
"7.85756E+18"	"Organic Search"	0	"United States"	"San Diego"			1106	2		"2017-04-06 00:00:00"	"1491505026"	"PAGE"			"$0.00"		"9180905"	"Google Men's Long Sleeve Raglan Ocean Blue"	"(not set)"	"(not set)"	"USD"					"Google Women's Fleece Hoodie"		"/google+redesign/"	0	1	
"8.12334E+18"	"Organic Search"	0	"Czechia"	"not available in demo dataset"			39	2		"2017-05-25 00:00:00"	"1495734943"	"PAGE"			"$0.00"		"9180766"	"Sport Bag"	"(not set)"	"(not set)"	"USD"					"Google Zipper-front Sports Bag"		"/google+redesign/"	0	1	
"2.12694E+17"	"Direct"	0	"Russia"	"Moscow"				1		"2017-04-21 00:00:00"	"1492777778"	"PAGE"			"$0.00"		"9182771"	"Google Women's 1/4 Zip Jacket Charcoal"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Leatherette Journal"		"/google+redesign/"	0	1	
"4.31587E+18"	"Direct"	32888	"Finland"	"not available in demo dataset"			48	3		"2016-11-08 00:00:00"	"1478599323"	"PAGE"			"$0.00"		"9183234"	"Nest¬Æ Learning Thermostat 3rd Gen-USA - Stainless Steel"	"(not set)"	"(not set)"	"USD"					"23 oz Wide Mouth Sport Bottle"		"/google+redesign/"	0	1	
"6.0517E+18"	"Direct"	0	"United States"	"not available in demo dataset"			9	2		"2017-04-04 00:00:00"	"1491321258"	"PAGE"			"$0.00"		"9182722"	"Google Men's 100% Cotton Short Sleeve Hero Tee Navy"	"(not set)"	"(not set)"	"USD"					"Google Men's 3/4 Sleeve Raglan Henley Grey"		"/google+redesign/"	0	1	
"7.69227E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2017-06-26 00:00:00"	"1498485807"	"PAGE"			"$0.00"		"9182723"	"Google Men's 100% Cotton Short Sleeve Hero Tee White"	"(not set)"	"(not set)"	"USD"					"Micro Wireless Earbud"		"/google+redesign/"	0	1	
"7.28208E+18"	"Organic Search"	0	"United States"	"Portland"				1		"2016-12-01 00:00:00"	"1480623763"	"PAGE"			"$0.00"		"9181019"	"Google Tri-blend Hoodie Grey"	"(not set)"	"(not set)"	"USD"					"Google Women's Fleece Hoodie"		"/google+redesign/"	0	1	
"7.36607E+17"	"Referral"	5292	"United States"	"San Jose"			180	6		"2017-03-17 00:00:00"	"1489791326"	"PAGE"			"$0.00"		"9182761"	"Google Women's Yoga Jacket Black"	"(not set)"	"(not set)"	"USD"					"Google Men's 3/4 Sleeve Raglan Henley Grey"		"/google+redesign/"	0	1	
"8.77909E+18"	"Direct"	393448	"China"	"not available in demo dataset"			393	2		"2016-08-26 00:00:00"	"1472267656"	"PAGE"			"$0.00"		"9182537"	"Google Women's Vintage T-Shirt Black"	"(not set)"	"(not set)"	"USD"					"Google Rucksack"		"/google+redesign/"	0	1	
"4.4614E+18"	"Organic Search"	22820	"Peru"	"not available in demo dataset"			23	4		"2016-08-26 00:00:00"	"1472225650"	"PAGE"			"$0.00"		"9182720"	"Google Men's Short Sleeve Badge Tee Charcoal"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Ballpoint LED Light Pen"		"/google+redesign/"	0	1	
"9.50033E+18"	"Organic Search"	14493	"United States"	"San Francisco"			14	4		"2017-03-06 00:00:00"	"1488843949"	"PAGE"			"$0.00"		"9182771"	"Google Women's 1/4 Zip Jacket Charcoal"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"8.01111E+18"	"Organic Search"	110777	"Canada"	"not available in demo dataset"			111	5		"2017-03-23 00:00:00"	"1490297997"	"PAGE"			"$0.00"		"9182739"	"Google Men's Watershed Full Zip Hoodie Grey"	"(not set)"	"(not set)"	"USD"					"Google Laptop Backpack"		"/google+redesign/"	0	1	
"2.95995E+17"	"Referral"	235033	"United States"	"Mountain View"			235	11		"2017-06-21 00:00:00"	"1498083046"	"PAGE"			"$0.00"		"9182502"	"Google Women's Yoga Jacket Black"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"1.27134E+18"	"Organic Search"	15748	"United States"	"Lake Oswego"			16	4		"2017-01-04 00:00:00"	"1483554269"	"PAGE"			"$0.00"		"9184620"	"Google Men's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"Android Onesie Baby Blue"		"/google+redesign/"	0	1	
"8.84426E+18"	"Organic Search"	131901	"United States"	"Sunnyvale"			247	9		"2016-08-01 00:00:00"	"1470083175"	"PAGE"			"$0.00"		"9181140"	"Google Trucker Hat"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Pen Pencil & Highlighter Set"		"/google+redesign/"	0	1	
"4.06402E+18"	"Organic Search"	57973	"United States"	"Santa Clara"			58	3		"2017-02-27 00:00:00"	"1488233585"	"PAGE"			"$0.00"		"9182737"	"Google Women's 3/4 Sleeve Baseball Raglan Heather/Black"	"(not set)"	"(not set)"	"USD"					"Google Luggage Tag"		"/google+redesign/"	0	1	
"1.82093E+18"	"Organic Search"	123102	"United States"	"not available in demo dataset"			151	5		"2017-05-02 00:00:00"	"1493779186"	"PAGE"			"$0.00"		"9182750"	"Google Men's Performance 1/4 Zip Pullover Heather/Black"	"(not set)"	"(not set)"	"USD"					"YouTube Men's Fleece Hoodie Black"		"/google+redesign/"	0	1	
"3.81354E+18"	"Direct"	83088	"United States"	"Seattle"			83	6		"2017-05-01 00:00:00"	"1493660450"	"PAGE"			"$0.00"		"9183228"	"Nest¬Æ Cam Indoor Security Camera - USA"	"(not set)"	"(not set)"	"USD"					"BLM Sweatshirt"		"/google+redesign/"	0	1	
"1.23048E+18"	"Organic Search"	0	"United Kingdom"	"not available in demo dataset"				1		"2016-09-09 00:00:00"	"1473456322"	"PAGE"			"$0.00"		"9182686"	"Google Women's V-Neck Tee Grey"	"(not set)"	"(not set)"	"USD"					"Google Laptop and Cell Phone Stickers"		"/google+redesign/"	0	1	
"3.06845E+18"	"Organic Search"	0	"Philippines"	"not available in demo dataset"				1		"2017-05-14 00:00:00"	"1494815418"	"PAGE"			"$0.00"		"9183234"	"Nest¬Æ Learning Thermostat 3rd Gen-USA - Stainless Steel"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Maze Pen"		"/google+redesign/"	0	1	
"2.26958E+18"	"Organic Search"	444991	"United States"	"not available in demo dataset"			445	7		"2016-09-21 00:00:00"	"1474476403"	"PAGE"			"$0.00"		"9180812"	"Google Power Bank"	"(not set)"	"(not set)"	"USD"					"Google PowerKit"		"/google+redesign/"	0	1	
"2.96047E+18"	"Referral"	99939	"India"	"(not set)"			100	4	1	"2017-07-29 00:00:00"	"1501397835"	"PAGE"			"$0.00"		"9182772"	"Google Women's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"Google Men's Short Sleeve Performance Badge Tee Pewter"		"/google+redesign/"	0	1	
"8.47435E+18"	"Organic Search"	0	"Saudi Arabia"	"not available in demo dataset"				1		"2017-01-23 00:00:00"	"1485214590"	"PAGE"			"$0.00"		"9182785"	"Google Women's Lightweight Microfleece Jacket"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"8.86282E+17"	"Direct"	0	"United States"	"Mountain View"				1		"2017-02-21 00:00:00"	"1487694854"	"PAGE"			"$0.00"		"9182569"	"Google Men's Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"BLM Sweatshirt"		"/google+redesign/"	0	1	
"5.86012E+18"	"Organic Search"	52326	"Australia"	"Sydney"			52	2		"2017-05-22 00:00:00"	"1495453954"	"PAGE"			"$0.00"		"9184720"	"Google Women's Short Sleeve Hero Tee Sky Blue"	"(not set)"	"(not set)"	"USD"					"YouTube Youth Short Sleeve Tee Red"		"/google+redesign/"	0	1	
"5.93982E+17"	"Organic Search"	0	"United States"	"Los Angeles"				1		"2017-06-02 00:00:00"	"1496420491"	"PAGE"			"$0.00"		"9181573"	"Google Snapback Hat Black"	"(not set)"	"(not set)"	"USD"					"Google Flashlight"		"/google+redesign/"	0	1	
"7.74864E+18"	"Direct"	0	"United States"	"San Jose"			2	2		"2016-08-15 00:00:00"	"1471282092"	"PAGE"			"$0.00"		"9180751"	"Android 24 oz Contigo Bottle"	"(not set)"	"(not set)"	"USD"					"Android Baby Essentials Baby Set"		"/google+redesign/"	0	1	
"2.71751E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2016-12-20 00:00:00"	"1482224977"	"PAGE"			"$0.00"		"9183234"	"Nest¬Æ Learning Thermostat 3rd Gen-USA - Stainless Steel"	"(not set)"	"(not set)"	"USD"					"YouTube Men's Short Sleeve Hero Tee Charcoal"		"/google+redesign/"	0	1	
"2.04631E+17"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2016-12-30 00:00:00"	"1483131689"	"PAGE"			"$0.00"		"9182714"	"Google Men's Long Sleeve Raglan Ocean Blue"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Windup Android"		"/google+redesign/"	0	1	
"1.27275E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2017-04-13 00:00:00"	"1492107148"	"PAGE"			"$0.00"		"9182771"	"Google Women's 1/4 Zip Jacket Charcoal"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Maze Pen"		"/google+redesign/"	0	1	
"5.68626E+18"	"Direct"	17531	"India"	"Hyderabad"			18	3		"2016-11-28 00:00:00"	"1480393479"	"PAGE"			"$0.00"		"9182771"	"Google Women's 1/4 Zip Jacket Charcoal"	"(not set)"	"(not set)"	"USD"					"Google Men's Pullover Hoodie Grey"		"/google+redesign/"	0	1	
"4.00099E+18"	"Organic Search"	0	"United States"	"Los Angeles"				1		"2017-01-25 00:00:00"	"1485381696"	"PAGE"			"$0.00"		"9182658"	"Google Women's Short Sleeve Hero Tee Sky Blue"	"(not set)"	"(not set)"	"USD"					"Google Tote Bag"		"/google+redesign/"	0	1	
"8.88371E+18"	"Direct"	919	"Puerto Rico"	"not available in demo dataset"			1	2		"2017-03-21 00:00:00"	"1490104210"	"PAGE"			"$0.00"		"9180819"	"Google Laptop and Cell Phone Stickers"	"(not set)"	"(not set)"	"USD"					"YouTube Custom Decals"		"/google+redesign/"	0	1	
"1.72898E+18"	"Organic Search"	0	"United States"	"Chicago"				1		"2017-06-01 00:00:00"	"1496341490"	"PAGE"			"$0.00"		"9182575"	"Android Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"Google Flashlight"		"/google+redesign/"	0	1	
"8.16123E+18"	"Organic Search"	0	"Italy"	"not available in demo dataset"				1		"2016-11-10 00:00:00"	"1478772189"	"PAGE"			"$0.00"		"9180806"	"Clip-on Compact Charger"	"(not set)"	"(not set)"	"USD"					"Google Tube Power Bank"		"/google+redesign/"	0	1	
"8.92006E+18"	"Organic Search"	57862	"Russia"	"Moscow"			58	2		"2016-10-31 00:00:00"	"1477945287"	"PAGE"			"$0.00"		"9182724"	"Google Men's 100% Cotton Short Sleeve Hero Tee Red"	"(not set)"	"(not set)"	"USD"					"Google Laptop Backpack"		"/google+redesign/"	0	1	
"8.75428E+18"	"Organic Search"	0	"Philippines"	"not available in demo dataset"				1		"2017-04-27 00:00:00"	"1493351040"	"PAGE"			"$0.00"		"9180793"	"26 oz Double Wall Insulated Bottle"	"(not set)"	"(not set)"	"USD"					"Micro Wireless Earbud"		"/google+redesign/"	0	1	
"1.45132E+18"	"Organic Search"	97058	"United States"	"Irvine"			120	6		"2017-06-27 00:00:00"	"1498581893"	"PAGE"			"$0.00"		"9182765"	"Google Women's Convertible Vest-Jacket Sea Foam Green"	"(not set)"	"(not set)"	"USD"					"YouTube RFID Journal"		"/google+redesign/"	0	1	
"9.45355E+18"	"Organic Search"	0	"Russia"	"Saint Petersburg"				1		"2016-11-11 00:00:00"	"1478895391"	"PAGE"			"$0.00"		"9182785"	"Google Women's Lightweight Microfleece Jacket"	"(not set)"	"(not set)"	"USD"					"Google Electronics Accessory Pouch"		"/google+redesign/"	0	1	
"4.38128E+18"	"Organic Search"	45595	"United States"	"not available in demo dataset"			329	7		"2017-06-12 00:00:00"	"1497271246"	"PAGE"			"$0.00"		"9183188"	"Google High Capacity 10,400mAh Charger"	"(not set)"	"(not set)"	"USD"					"Google 2200mAh Micro Charger"		"/google+redesign/"	0	1	
"3.23449E+18"	"Referral"	39492	"United States"	"not available in demo dataset"			44	3		"2017-06-01 00:00:00"	"1496341938"	"PAGE"			"$0.00"		"9182714"	"Google Men's Long Sleeve Raglan Ocean Blue"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"2.95396E+18"	"Organic Search"	27219	"United States"	"not available in demo dataset"			36	7		"2016-12-06 00:00:00"	"1481069735"	"PAGE"			"$0.00"		"9180844"	"Gunmetal Roller Ball Pen"	"(not set)"	"(not set)"	"USD"					"Google Stylus Pen w/ LED Light"		"/google+redesign/"	0	1	
"1.35997E+18"	"Direct"	0	"United States"	"not available in demo dataset"				1		"2017-03-24 00:00:00"	"1490382740"	"PAGE"			"$0.00"		"9182721"	"Google Men's 100% Cotton Short Sleeve Hero Tee Black"	"(not set)"	"(not set)"	"USD"					"Google Men's Airflow 1/4 Zip Pullover Lapis"		"/google+redesign/"	0	1	
"5.06633E+18"	"Organic Search"	0	"Slovakia"	"not available in demo dataset"				1		"2017-05-30 00:00:00"	"1496140952"	"PAGE"			"$0.00"		"9182784"	"Google Women's Short Sleeve Hero Tee White"	"(not set)"	"(not set)"	"USD"					"Google Zipper-front Sports Bag"		"/google+redesign/"	0	1	
"1.00011E+17"	"Direct"	132582	"United States"	"not available in demo dataset"			133	3		"2017-04-26 00:00:00"	"1493265687"	"PAGE"			"$0.00"		"9182569"	"Google Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"Bluetooth Headphones"		"/google+redesign/"	0	1	
"3.84561E+17"	"Organic Search"	1088585	"Japan"	"not available in demo dataset"			1130	7		"2017-06-26 00:00:00"	"1498469469"	"PAGE"			"$0.00"		"9180833"	"Rubber Grip Ballpoint Pen 4 Pack"	"(not set)"	"(not set)"	"USD"					"Android RFID Journal"		"/google+redesign/"	0	1	
"4.88581E+18"	"Direct"	0	"United States"	"San Francisco"				1		"2017-02-10 00:00:00"	"1486752821"	"PAGE"			"$0.00"		"9180752"	"Android 24 oz Contigo Bottle"	"(not set)"	"(not set)"	"USD"					"Spiral Notebook and Pen Set"		"/google+redesign/"	0	1	
"8.17703E+18"	"Organic Search"	0	"India"	"(not set)"				1		"2017-06-16 00:00:00"	"1497633248"	"PAGE"			"$0.00"		"9183106"	"Google Women's Performance Hero Tee Gunmetal"	"(not set)"	"(not set)"	"USD"					"Google 4400mAh Power Bank"		"/google+redesign/"	0	1	
"4.96003E+18"	"Organic Search"	80548	"United States"	"Los Angeles"			81	3		"2017-05-14 00:00:00"	"1494804603"	"PAGE"			"$0.00"		"9182722"	"Google Men's 100% Cotton Short Sleeve Hero Tee Navy"	"(not set)"	"(not set)"	"USD"					"Google Twill Cap"		"/google+redesign/"	0	1	
"7.71105E+18"	"Referral"	27622	"Sweden"	"not available in demo dataset"			158	11	17	"2017-07-17 00:00:00"	"1500281461"	"PAGE"			"$0.00"		"9182658"	"Google Women's Short Sleeve Hero Tee Sky Blue"	"(not set)"	"(not set)"	"USD"					"Nest Cam Outdoor Security Camera - USA"		"/google+redesign/"	0	1	
"1.20192E+18"	"Organic Search"	0	"Philippines"	"not available in demo dataset"			28	5		"2017-03-24 00:00:00"	"1490359775"	"PAGE"			"$0.00"		"9182663"	"Google Women's Short Sleeve Badge Tee Red Heather"	"(not set)"	"(not set)"	"USD"					"Android Onesie Baby Blue"		"/google+redesign/"	0	1	
"9.58677E+18"	"Organic Search"	19842	"United States"	"not available in demo dataset"			20	4		"2017-03-04 00:00:00"	"1488677580"	"PAGE"			"$0.00"		"9180842"	"Maze Pen"	"(not set)"	"(not set)"	"USD"					"Google Alpine Style Backpack"		"/google+redesign/"	0	1	
"1.0805E+18"	"Paid Search"	80936	"United States"	"Palo Alto"			94	9		"2016-11-03 00:00:00"	"1478210156"	"PAGE"			"$0.00"		"9182812"	"Google Infant Zip Hood Pink"	"(not set)"	"(not set)"	"USD"					"Google Laptop Backpack"		"/google+redesign/"	0	1	
"3.0133E+18"	"Organic Search"	0	"Canada"	"not available in demo dataset"			145	6		"2016-12-30 00:00:00"	"1483086717"	"PAGE"			"$0.00"		"9180819"	"Google Laptop and Cell Phone Stickers"	"(not set)"	"(not set)"	"USD"					"Google Stylus Pen w/ LED Light"		"/google+redesign/"	0	1	
"5.16566E+18"	"Organic Search"	236348	"United Kingdom"	"not available in demo dataset"			236	2		"2017-03-08 00:00:00"	"1489002702"	"PAGE"			"$0.00"		"9180809"	"Google Flashlight"	"(not set)"	"(not set)"	"USD"					"Google Power Bank"		"/google+redesign/"	0	1	
"3.35868E+18"	"Organic Search"	0	"Romania"	"not available in demo dataset"				1		"2017-05-28 00:00:00"	"1495999337"	"PAGE"			"$0.00"		"9182721"	"Google Men's 100% Cotton Short Sleeve Hero Tee Black"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Recycled Mouse Pad"		"/google+redesign/"	0	1	
"1.6035E+18"	"Organic Search"	56892	"United States"	"not available in demo dataset"			57	2	1	"2017-07-19 00:00:00"	"1500485709"	"PAGE"			"$0.00"		"9182761"	"Google Women's Yoga Jacket Black"	"(not set)"	"(not set)"	"USD"					"Google Women's Long Sleeve Tee Lavender"		"/google+redesign/"	0	1	
"6.8399E+18"	"Referral"	31885	"United States"	"San Jose"			32	3		"2017-02-09 00:00:00"	"1486702521"	"PAGE"			"$0.00"		"9182569"	"Google Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"Google Executive Umbrella"		"/google+redesign/"	0	1	
"6.69388E+18"	"Organic Search"	66421	"Singapore"	"(not set)"			66	2		"2017-03-26 00:00:00"	"1490518721"	"PAGE"			"$0.00"		"9180766"	"Sport Bag"	"(not set)"	"(not set)"	"USD"					"Google RFID Journal"		"/google+redesign/"	0	1	
"6.48481E+17"	"Organic Search"	0	"Canada"	"not available in demo dataset"			19	2		"2017-06-01 00:00:00"	"1496362428"	"PAGE"			"$0.00"		"9180905"	"Google Men's Long Sleeve Raglan Ocean Blue"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Pen Pencil & Highlighter Set"		"/google+redesign/"	0	1	
"8.80856E+18"	"Organic Search"	24699	"Estonia"	"not available in demo dataset"			34	3		"2017-03-20 00:00:00"	"1490034824"	"PAGE"			"$0.00"		"9183234"	"Nest¬Æ Learning Thermostat 3rd Gen-USA - Stainless Steel"	"(not set)"	"(not set)"	"USD"					"YouTube Onesie Heather"		"/google+redesign/"	0	1	
"2.31033E+18"	"Direct"	0	"United States"	"San Bruno"				1		"2017-05-03 00:00:00"	"1493844532"	"PAGE"			"$0.00"		"9182714"	"Google Men's Long Sleeve Raglan Ocean Blue"	"(not set)"	"(not set)"	"USD"					"BLM Sweatshirt"		"/google+redesign/"	0	1	
"9.73021E+18"	"Direct"	0	"United States"	"San Francisco"				1		"2017-02-15 00:00:00"	"1487174550"	"PAGE"			"$0.00"		"9182744"	"Google Men's Microfiber 1/4 Zip Pullover Grey/Black"	"(not set)"	"(not set)"	"USD"					"BLM Sweatshirt"		"/google+redesign/"	0	1	
"2.95201E+18"	"Direct"	24069	"United States"	"not available in demo dataset"			168	7	2	"2017-07-18 00:00:00"	"1500420086"	"PAGE"			"$0.00"		"9182581"	"Google Women's Fleece Hoodie"	"(not set)"	"(not set)"	"USD"					"Waterproof Backpack"		"/google+redesign/"	0	1	
"5.6849E+18"	"Organic Search"	294423	"United States"	"Mountain View"			348	8		"2016-09-20 00:00:00"	"1474380306"	"PAGE"			"$0.00"		"9180792"	"20 oz Stainless Steel Insulated Tumbler"	"(not set)"	"(not set)"	"USD"					"Reusable Shopping Bag"		"/google+redesign/"	0	1	
"3.91808E+18"	"Organic Search"	503779	"United States"	"Sunnyvale"			526	12		"2017-02-04 00:00:00"	"1486274408"	"PAGE"			"$0.00"		"9182775"	"Google Women's Zip Hoodie Grey"	"(not set)"	"(not set)"	"USD"					"Google Men's Short Sleeve Performance Badge Tee Black"		"/google+redesign/"	0	1	
"9.06598E+17"	"Direct"	167450	"United States"	"not available in demo dataset"			234	17		"2016-12-24 00:00:00"	"1482617121"	"PAGE"			"$0.00"		"9180829"	"Google Sunglasses"	"(not set)"	"(not set)"	"USD"					"Nest¬Æ Learning Thermostat 3rd Gen-USA - Stainless Steel"		"/google+redesign/"	0	1	
"5.12669E+18"	"Paid Search"	32558	"United States"	"New York"			125	7		"2017-02-11 00:00:00"	"1486872772"	"PAGE"			"$0.00"		"9182575"	"Android Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"Google Twill Cap"		"/google+redesign/"	0	1	
"5.35924E+18"	"Organic Search"	58826	"New Zealand"	"not available in demo dataset"			59	4		"2016-12-03 00:00:00"	"1480830287"	"PAGE"			"$0.00"		"9182772"	"Google Women's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"Google 4400mAh Power Bank"		"/google+redesign/"	0	1	
"4.75244E+17"	"Organic Search"	0	"Italy"	"not available in demo dataset"				1		"2017-06-01 00:00:00"	"1496356379"	"PAGE"			"$0.00"		"9182575"	"Android Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"Google Flashlight"		"/google+redesign/"	0	1	
"7.40108E+18"	"Organic Search"	69988	"Taiwan"	"(not set)"			70	2		"2016-10-05 00:00:00"	"1475658572"	"PAGE"			"$0.00"		"9180801"	"Engraved Ceramic Google Mug"	"(not set)"	"(not set)"	"USD"					"Google Electronics Accessory Pouch"		"/google+redesign/"	0	1	
"7.24161E+17"	"Organic Search"	0	"United States"	"Seattle"				1		"2017-06-08 00:00:00"	"1496938657"	"PAGE"			"$0.00"		"9183185"	"Google Bluetooth Headphones"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"2.50092E+18"	"Referral"	186278	"United States"	"San Francisco"			186	8		"2017-02-03 00:00:00"	"1486162976"	"PAGE"			"$0.00"		"9182775"	"Google Women's Zip Hoodie Grey"	"(not set)"	"(not set)"	"USD"					"Google Men's Long Sleeve Pullover Badge Tee Heather"		"/google+redesign/"	0	1	
"4.04084E+18"	"Direct"	81773	"Canada"	"Toronto"			147	7		"2017-03-24 00:00:00"	"1490368855"	"PAGE"			"$0.00"		"9182735"	"Google Men's Heavyweight Long Sleeve Hero Tee Burgundy"	"(not set)"	"(not set)"	"USD"					"Google Alpine Style Backpack"		"/google+redesign/"	0	1	
"4.81764E+17"	"Organic Search"	35648	"United States"	"Mountain View"			36	2		"2017-05-16 00:00:00"	"1494948935"	"PAGE"			"$0.00"		"9180905"	"Google Men's Long Sleeve Raglan Ocean Blue"	"(not set)"	"(not set)"	"USD"					"Google Women's Short Sleeve Hero Tee Black"		"/google+redesign/"	0	1	
"7.9826E+18"	"Organic Search"	0	"Canada"	"not available in demo dataset"				1		"2017-02-28 00:00:00"	"1488322696"	"PAGE"			"$0.00"		"9182999"	"Google Bongo Cupholder Bluetooth Speaker"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"5.89938E+18"	"Affiliates"	28468	"India"	"not available in demo dataset"			58	5		"2017-03-16 00:00:00"	"1489667805"	"PAGE"			"$0.00"		"9182838"	"Google Toddler Short Sleeve T-shirt Yellow"	"(not set)"	"(not set)"	"USD"					"Google Men's Softshell Jacket Black/Grey"		"/google+redesign/"	0	1	
"1.63423E+17"	"Organic Search"	17353	"United States"	"Atlanta"			17	2		"2017-02-14 00:00:00"	"1487108103"	"PAGE"			"$0.00"		"9182722"	"Google Men's 100% Cotton Short Sleeve Hero Tee Navy"	"(not set)"	"(not set)"	"USD"					"Android 24 oz Contigo Bottle"		"/google+redesign/"	0	1	
"5.88019E+18"	"Organic Search"	0	"Canada"	"not available in demo dataset"				1		"2017-05-15 00:00:00"	"1494892079"	"PAGE"			"$0.00"		"9182781"	"Google Women's Short Sleeve Hero Tee Black"	"(not set)"	"(not set)"	"USD"					"Google Men's Bike Short Sleeve Tee Charcoal"		"/google+redesign/"	0	1	
"2.08675E+18"	"Organic Search"	0	"Spain"	"not available in demo dataset"				1		"2016-12-18 00:00:00"	"1482096949"	"PAGE"			"$0.00"		"9182700"	"Android Men's 3/4 Sleeve Raglan Henley Black"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Windup Android"		"/google+redesign/"	0	1	
"9.83123E+18"	"Direct"	987975	"United States"	"Palo Alto"			1002	4		"2017-01-31 00:00:00"	"1485892692"	"PAGE"			"$0.00"		"9183186"	"Google G Noise-reducing Bluetooth Headphones"	"(not set)"	"(not set)"	"USD"					"Google Water Resistant Bluetooth Speaker"		"/google+redesign/"	0	1	
"8.20599E+17"	"Organic Search"	37368	"United States"	"not available in demo dataset"			37	3		"2016-12-03 00:00:00"	"1480829632"	"PAGE"			"$0.00"		"9183219"	"Google Leather Journal"	"(not set)"	"(not set)"	"USD"					"YouTube Hard Cover Journal"		"/google+redesign/"	0	1	
"3.29705E+18"	"Referral"	0	"Japan"	"not available in demo dataset"				1		"2016-12-02 00:00:00"	"1480739512"	"PAGE"			"$0.00"		"9182575"	"Android Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"Google Doodle Decal"		"/google+redesign/"	0	1	
"8.25111E+18"	"Direct"	136313	"United States"	"not available in demo dataset"			330	7		"2016-10-12 00:00:00"	"1476309318"	"PAGE"			"$0.00"		"9180793"	"26 oz Double Wall Insulated Bottle"	"(not set)"	"(not set)"	"USD"					"Google Stylus Pen w/ LED Light"		"/google+redesign/"	0	1	
"4.48292E+17"	"Direct"	12400	"United States"	"not available in demo dataset"			1083	3		"2016-10-23 00:00:00"	"1477279409"	"PAGE"			"$0.00"		"9182784"	"Google Women's Short Sleeve Hero Tee White"	"(not set)"	"(not set)"	"USD"					"Google Men's Microfiber 1/4 Zip Pullover Blue/Indigo"		"/google+redesign/"	0	1	
"3.84353E+18"	"Direct"	0	"Mexico"	"not available in demo dataset"				1		"2017-03-01 00:00:00"	"1488402146"	"PAGE"			"$0.00"		"9182723"	"Google Men's 100% Cotton Short Sleeve Hero Tee White"	"(not set)"	"(not set)"	"USD"					"Google 3/4 Sleeve Raglan Badge Henley Black"		"/google+redesign/"	0	1	
"7.96551E+18"	"Organic Search"	0	"United States"	"Salem"				1		"2017-01-12 00:00:00"	"1484228449"	"PAGE"			"$0.00"		"9180752"	"Android 24 oz Contigo Bottle"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Waterpoof Gear Bag"		"/google+redesign/"	0	1	
"2.19821E+16"	"Organic Search"	0	"Czechia"	"not available in demo dataset"				1		"2017-04-29 00:00:00"	"1493534051"	"PAGE"			"$0.00"		"9184734"	"Nest¬Æ Learning Thermostat 3rd Gen-USA - Copper"	"(not set)"	"(not set)"	"USD"					"Google Zipper-front Sports Bag"		"/google+redesign/"	0	1	
"3.0896E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2016-12-21 00:00:00"	"1482308111"	"PAGE"			"$0.00"		"9182723"	"Google Men's 100% Cotton Short Sleeve Hero Tee White"	"(not set)"	"(not set)"	"USD"					"Google Alpine Style Backpack"		"/google+redesign/"	0	1	
"7.72159E+18"	"Direct"	0	"United States"	"not available in demo dataset"				1		"2017-04-13 00:00:00"	"1492121204"	"PAGE"			"$0.00"		"9183228"	"Nest¬Æ Cam Indoor Security Camera - USA"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Windup Android"		"/google+redesign/"	0	1	
"9.85429E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2017-06-29 00:00:00"	"1498738247"	"PAGE"			"$0.00"		"9182743"	"Google Men's Microfiber 1/4 Zip Pullover Blue/Indigo"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"4.28333E+18"	"Direct"	1234153	"United States"	"Mountain View"			1234	7		"2016-11-09 00:00:00"	"1478731467"	"PAGE"			"$0.00"		"9182853"	"Google Toddler 1/4 Zip Fleece Pewter"	"(not set)"	"(not set)"	"USD"					"Google Toddler Short Sleeve T-shirt Royal Blue"		"/google+redesign/"	0	1	
"7.12937E+18"	"Direct"	0	"United States"	"San Francisco"				1		"2017-02-17 00:00:00"	"1487374088"	"PAGE"			"$0.00"		"9182838"	"Google Toddler Short Sleeve T-shirt Yellow"	"(not set)"	"(not set)"	"USD"					"BLM Sweatshirt"		"/google+redesign/"	0	1	
"9.38372E+18"	"Referral"	13878	"United States"	"Mountain View"			74	3		"2017-04-12 00:00:00"	"1492013303"	"PAGE"			"$0.00"		"9182569"	"Google Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"Suitcase Organizer Cubes"		"/google+redesign/"	0	1	
"1.27318E+18"	"Direct"	25794	"Thailand"	"not available in demo dataset"			26	2		"2017-02-18 00:00:00"	"1487476041"	"PAGE"			"$0.00"		"9180809"	"Google Four Color EDC Flashlight"	"(not set)"	"(not set)"	"USD"					"Google Device Holder Sticky Pad"		"/google+redesign/"	0	1	
"2.10105E+18"	"Referral"	102249	"United States"	"Mountain View"			125	5		"2017-05-03 00:00:00"	"1493833895"	"PAGE"			"$0.00"		"9180793"	"26 oz Double Wall Insulated Bottle"	"(not set)"	"(not set)"	"USD"					"Google Accent Insulated Stainless Steel Bottle"		"/google+redesign/"	0	1	
"3.07218E+18"	"Direct"	0	"United States"	"Los Angeles"				1		"2017-02-17 00:00:00"	"1487369112"	"PAGE"			"$0.00"		"9182569"	"Google Men's Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"BLM Sweatshirt"		"/google+redesign/"	0	1	
"6.42358E+18"	"Organic Search"	0	"Taiwan"	"not available in demo dataset"				1	1	"2017-07-21 00:00:00"	"1500699101"	"PAGE"			"$0.00"		"9180781"	"Suitcase Organizer Cubes"	"(not set)"	"(not set)"	"USD"					"UpCycled Handlebar Bag"		"/google+redesign/"	0	1	
"7.89323E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2017-06-20 00:00:00"	"1498006565"	"PAGE"			"$0.00"		"9180860"	"Recycled Paper Journal Set"	"(not set)"	"(not set)"	"USD"					"Google Flashlight"		"/google+redesign/"	0	1	
"9.54911E+18"	"Organic Search"	112896	"United States"	"not available in demo dataset"			133	5		"2016-12-02 00:00:00"	"1480702407"	"PAGE"			"$0.00"		"9182723"	"Google Men's 100% Cotton Short Sleeve Hero Tee White"	"(not set)"	"(not set)"	"USD"					"Google Men's Bayside Graphic Tee"		"/google+redesign/"	0	1	
"5.69657E+18"	"Organic Search"	0	"United States"	"Charlotte"				1		"2017-05-19 00:00:00"	"1495206968"	"PAGE"			"$0.00"		"9182575"	"Android Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"1.88217E+18"	"Direct"	0	"United States"	"San Francisco"			2	5	3	"2017-07-05 00:00:00"	"1499273937"	"PAGE"			"$0.00"		"9181573"	"Google Snapback Hat Black"	"(not set)"	"(not set)"	"USD"					"Google Men's Short Sleeve Badge Tee Charcoal"		"/google+redesign/"	0	1	
"5.77877E+18"	"Organic Search"	0	"Argentina"	"not available in demo dataset"				1		"2016-10-06 00:00:00"	"1475767260"	"PAGE"			"$0.00"		"9180779"	"1 oz Hand Sanitizer"	"(not set)"	"(not set)"	"USD"					"Suitcase Organizer Cubes"		"/google+redesign/"	0	1	
"3.5966E+18"	"Referral"	38068	"United States"	"New York"			61	3		"2017-03-03 00:00:00"	"1488563733"	"PAGE"			"$0.00"		"9182772"	"Google Women's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Red Shine 15 oz Mug"		"/google+redesign/"	0	1	
"6.33976E+18"	"Organic Search"	205535	"United States"	"not available in demo dataset"			206	8		"2016-11-25 00:00:00"	"1480109959"	"PAGE"			"$0.00"		"9182742"	"Google Men's Convertible Vest-Jacket Pewter"	"(not set)"	"(not set)"	"USD"					"Google Men's Long Sleeve Pullover Badge Tee Heather"		"/google+redesign/"	0	1	
"9.80128E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2016-08-21 00:00:00"	"1471824153"	"PAGE"			"$0.00"		"9180769"	"Google Laptop Backpack"	"(not set)"	"(not set)"	"USD"					"Google Women's 1/4 Zip Performance Pullover Black"		"/google+redesign/"	0	1	
"1.34832E+18"	"Organic Search"	11980	"Turkey"	"Antalya"			23	3		"2017-05-16 00:00:00"	"1494976204"	"PAGE"			"$0.00"		"9180813"	"Google Tube Power Bank"	"(not set)"	"(not set)"	"USD"					"Google 4400mAh Power Bank"		"/google+redesign/"	0	1	
"3.56392E+18"	"Organic Search"	0	"United States"	"San Francisco"				1		"2017-06-01 00:00:00"	"1496354597"	"PAGE"			"$0.00"		"9183226"	"Android Luggage Tag"	"(not set)"	"(not set)"	"USD"					"Google Luggage Tag"		"/google+redesign/"	0	1	
"9.3669E+17"	"Organic Search"	42941	"United States"	"not available in demo dataset"			43	2		"2017-05-25 00:00:00"	"1495744263"	"PAGE"			"$0.00"		"9182772"	"Google Women's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"Google High Capacity 10,400mAh Charger"		"/google+redesign/"	0	1	
"5.69408E+18"	"Organic Search"	81988	"United States"	"Sunnyvale"			82	6		"2016-11-30 00:00:00"	"1480549820"	"PAGE"			"$0.00"		"9180801"	"Engraved Ceramic Google Mug"	"(not set)"	"(not set)"	"USD"					"Google Women's Scoop Neck Tee Green"		"/google+redesign/"	0	1	
"1.65344E+18"	"Paid Search"	14082	"United States"	"not available in demo dataset"			14	2		"2017-07-02 00:00:00"	"1499015529"	"PAGE"			"$0.00"		"9183222"	"Google Leather Perforated Journal"	"(not set)"	"(not set)"	"USD"					"Google Leather Journal"		"/google+redesign/"	0	1	
"6.50735E+18"	"Organic Search"	0	"Russia"	"not available in demo dataset"				1		"2017-03-14 00:00:00"	"1489483103"	"PAGE"			"$0.00"		"9184733"	"Nest¬Æ Learning Thermostat 3rd Gen-USA - White"	"(not set)"	"(not set)"	"USD"					"Google Power Bank"		"/google+redesign/"	0	1	
"6.85482E+18"	"Direct"	0	"Taiwan"	"(not set)"			64	2		"2017-06-03 00:00:00"	"1496473632"	"PAGE"			"$0.00"		"9180905"	"Google Men's Long Sleeve Raglan Ocean Blue"	"(not set)"	"(not set)"	"USD"					"Google Alpine Style Backpack"		"/google+redesign/"	0	1	
"2.25412E+18"	"Referral"	63004	"United States"	"Mountain View"			202	13		"2017-04-03 00:00:00"	"1491241690"	"PAGE"			"$0.00"		"9182714"	"Google Men's Long Sleeve Raglan Ocean Blue"	"(not set)"	"(not set)"	"USD"					"Google Men's 3/4 Sleeve Raglan Henley Grey"		"/google+redesign/"	0	1	
"6.14993E+18"	"Organic Search"	385997	"Peru"	"La Victoria"			629	7	1	"2017-07-13 00:00:00"	"1499993080"	"PAGE"			"$0.00"		"9184682"	"Waze Mobile Phone Vent Mount"	"(not set)"	"(not set)"	"USD"					"Google Device Holder Sticky Pad"		"/google+redesign/"	0	1	
"5.28942E+18"	"Direct"	0	"United States"	"not available in demo dataset"				1		"2017-02-12 00:00:00"	"1486928664"	"PAGE"			"$0.00"		"9182739"	"Google Men's Watershed Full Zip Hoodie Grey"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"2.13928E+17"	"Organic Search"	0	"United States"	"Houston"			17	3		"2016-10-20 00:00:00"	"1477015430"	"PAGE"			"$0.00"		"9180761"	"Large Zipper Top Tote Bag"	"(not set)"	"(not set)"	"USD"					"Google Lunch Bag"		"/google+redesign/"	0	1	
"8.03743E+18"	"Direct"	0	"United States"	"New York"				1		"2017-06-05 00:00:00"	"1496675520"	"PAGE"			"$0.00"		"9182721"	"Google Men's 100% Cotton Short Sleeve Hero Tee Black"	"(not set)"	"(not set)"	"USD"					"Android Lifted Men's Short Sleeve Tee Blue"		"/google+redesign/"	0	1	
"4.52249E+18"	"Referral"	75664	"United States"	"Mountain View"			109	4		"2017-05-25 00:00:00"	"1495756877"	"PAGE"			"$0.00"		"9183106"	"Google Women's Performance Hero Tee Gunmetal"	"(not set)"	"(not set)"	"USD"					"Google Rucksack"		"/google+redesign/"	0	1	
"3.84385E+18"	"Direct"	69243	"United States"	"Mountain View"			69	4		"2016-09-07 00:00:00"	"1473296358"	"PAGE"			"$0.00"		"9180769"	"Google Laptop Backpack"	"(not set)"	"(not set)"	"USD"					"Waterproof Backpack"		"/google+redesign/"	0	1	
"4.99316E+17"	"Organic Search"	0	"United States"	"not available in demo dataset"				1		"2017-05-23 00:00:00"	"1495559213"	"PAGE"			"$0.00"		"9183228"	"Nest¬Æ Cam Indoor Security Camera - USA"	"(not set)"	"(not set)"	"USD"					"Google Alpine Style Backpack"		"/google+redesign/"	0	1	
"3.84177E+18"	"Direct"	0	"United States"	"not available in demo dataset"				1		"2017-04-26 00:00:00"	"1493235495"	"PAGE"			"$0.00"		"9180905"	"Google Men's Long Sleeve Raglan Ocean Blue"	"(not set)"	"(not set)"	"USD"					"Waze Dress Socks"		"/google+redesign/"	0	1	
"4.01116E+17"	"Direct"	0	"United States"	"Mountain View"				1		"2017-02-17 00:00:00"	"1487383572"	"PAGE"			"$0.00"		"9182569"	"Google Men's Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"BLM Sweatshirt"		"/google+redesign/"	0	1	
"1.41458E+18"	"Organic Search"	100681	"Czechia"	"not available in demo dataset"			101	5		"2017-01-19 00:00:00"	"1484831530"	"PAGE"			"$0.00"		"9182593"	"Google Men's Pullover Hoodie Grey"	"(not set)"	"(not set)"	"USD"					"Android 24 oz Contigo Bottle"		"/google+redesign/"	0	1	
"5.43721E+18"	"Organic Search"	18951	"United States"	"San Bruno"			19	3		"2016-11-29 00:00:00"	"1480463288"	"PAGE"			"$0.00"		"9180824"	"Foam Can and Bottle Cooler"	"(not set)"	"(not set)"	"USD"					"Android BTTF Moonshot Shirt"		"/google+redesign/"	0	1	
"7.23102E+18"	"Organic Search"	0	"United States"	"San Jose"			5	2	1	"2017-07-06 00:00:00"	"1499387674"	"PAGE"			"$0.00"		"9182785"	"Google Women's Lightweight Microfleece Jacket"	"(not set)"	"(not set)"	"USD"					"Google Men's Zip Hoodie"		"/google+redesign/"	0	1	
"7.59724E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"			67	2		"2017-03-13 00:00:00"	"1489450965"	"PAGE"			"$0.00"		"9180824"	"Foam Can and Bottle Cooler"	"(not set)"	"(not set)"	"USD"					"Google Men's Convertible Vest-Jacket Pewter"		"/google+redesign/"	0	1	
"5.48562E+18"	"Referral"	36336	"United States"	"New York"			92	4		"2017-05-18 00:00:00"	"1495119762"	"PAGE"			"$0.00"		"9180824"	"Foam Can and Bottle Cooler"	"(not set)"	"(not set)"	"USD"					"Nest Protect Smoke + CO White Wired Alarm-USA"		"/google+redesign/"	0	1	
"3.1564E+18"	"Paid Search"	137307	"United States"	"not available in demo dataset"			257	10		"2016-10-02 00:00:00"	"1475444763"	"PAGE"			"$0.00"		"9182724"	"Google Men's 100% Cotton Short Sleeve Hero Tee Red"	"(not set)"	"(not set)"	"USD"					"Google Women's Lightweight Microfleece Jacket"		"/google+redesign/"	0	1	
"1.48224E+18"	"Organic Search"	0	"Indonesia"	"not available in demo dataset"			122	3		"2017-03-19 00:00:00"	"1489946860"	"PAGE"			"$0.00"		"9183228"	"Nest¬Æ Cam Indoor Security Camera - USA"	"(not set)"	"(not set)"	"USD"					"Google Men's Performance Full Zip Jacket Black"		"/google+redesign/"	0	1	
"1.14214E+17"	"Organic Search"	74091	"United States"	"not available in demo dataset"			288	6		"2017-02-21 00:00:00"	"1487714963"	"PAGE"			"$0.00"		"9182772"	"Google Women's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"Google Women's Long Sleeve Tee Lavender"		"/google+redesign/"	0	1	
"6.01412E+18"	"Organic Search"	50717	"India"	"Chennai"			51	3		"2016-12-26 00:00:00"	"1482823249"	"PAGE"			"$0.00"		"9183228"	"Nest¬Æ Cam Indoor Security Camera - USA"	"(not set)"	"(not set)"	"USD"					"YouTube Men's Short Sleeve Hero Tee Black"		"/google+redesign/"	0	1	
"6.67863E+18"	"Organic Search"	156815	"United States"	"Mountain View"			157	8		"2017-05-11 00:00:00"	"1494530759"	"PAGE"			"$0.00"		"9182658"	"Google Women's Short Sleeve Hero Tee Sky Blue"	"(not set)"	"(not set)"	"USD"					"Google Doodle Decal"		"/google+redesign/"	0	1	
"8.27011E+18"	"Direct"	115567	"United States"	"not available in demo dataset"			1450	10		"2017-06-18 00:00:00"	"1497845452"	"PAGE"			"$0.00"		"9182785"	"Google Women's Lightweight Microfleece Jacket"	"(not set)"	"(not set)"	"USD"					"Google Metallic Notebook Set"		"/google+redesign/"	0	1	
"3.21243E+18"	"Referral"	1498124	"United States"	"Mountain View"			1498	9		"2017-06-25 00:00:00"	"1498375049"	"PAGE"			"$0.00"		"9184734"	"Nest¬Æ Learning Thermostat 3rd Gen-USA - Copper"	"(not set)"	"(not set)"	"USD"					"Nest Protect Smoke + CO White Wired Alarm-USA"		"/google+redesign/"	0	1	
"8.79573E+18"	"Organic Search"	44530	"United States"	"not available in demo dataset"			76	10		"2017-06-23 00:00:00"	"1498283990"	"PAGE"			"$0.00"		"9182785"	"Google Women's Lightweight Microfleece Jacket"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Red Spiral Google Notebook"		"/google+redesign/"	0	1	
"6.15482E+18"	"Organic Search"	231479	"United States"	"not available in demo dataset"			346	12		"2016-09-27 00:00:00"	"1475013064"	"PAGE"			"$0.00"		"9182635"	"Google Women's Short Sleeve V-Neck Tee Black"	"(not set)"	"(not set)"	"USD"					"Google Car Clip Phone Holder"		"/google+redesign/"	0	1	
"5.91744E+18"	"Organic Search"	179433	"Canada"	"not available in demo dataset"			179	4		"2017-02-04 00:00:00"	"1486219282"	"PAGE"			"$0.00"		"9182581"	"Google Women's Fleece Hoodie"	"(not set)"	"(not set)"	"USD"					"YouTube Custom Decals"		"/google+redesign/"	0	1	
"7.42797E+17"	"Direct"	375627	"United States"	"Vancouver"			708	16		"2017-05-05 00:00:00"	"1494005164"	"PAGE"			"$0.00"		"9182581"	"Google Women's Fleece Hoodie"	"(not set)"	"(not set)"	"USD"					"Android Women's Short Sleeve Hero Tee Black"		"/google+redesign/"	0	1	
"4.18701E+18"	"Organic Search"	52303	"United States"	"not available in demo dataset"			185	14		"2017-03-02 00:00:00"	"1488479844"	"PAGE"			"$0.00"		"9182737"	"Google Women's 3/4 Sleeve Baseball Raglan Heather/Black"	"(not set)"	"(not set)"	"USD"					"Waterproof Backpack"		"/google+redesign/"	0	1	
"9.35346E+18"	"Organic Search"	164686	"United States"	"not available in demo dataset"			246	13		"2016-08-13 00:00:00"	"1471131270"	"PAGE"			"$0.00"		"9181139"	"Waterproof Backpack"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Malibu Sunglasses"		"/google+redesign/"	0	1	
"7.15008E+18"	"Organic Search"	0	"France"	"Paris"			116	2		"2017-04-27 00:00:00"	"1493288360"	"PAGE"			"$0.00"		"9184737"	"Waze Pack of 9 Decal Set"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"4.24443E+18"	"Organic Search"	22442	"United States"	"not available in demo dataset"			42	5		"2016-12-20 00:00:00"	"1482270651"	"PAGE"			"$0.00"		"9183228"	"Nest¬Æ Cam Indoor Security Camera - USA"	"(not set)"	"(not set)"	"USD"					"Nest¬Æ Learning Thermostat 3rd Gen-USA - Stainless Steel"		"/google+redesign/"	0	1	
"1.1326E+18"	"Direct"	0	"Ukraine"	"not available in demo dataset"				1		"2017-04-08 00:00:00"	"1491643743"	"PAGE"			"$0.00"		"9184710"	"Waze Women's Typography Short Sleeve Tee"	"(not set)"	"(not set)"	"USD"					"Waze Dress Socks"		"/google+redesign/"	0	1	
"7.37116E+18"	"Direct"	0	"Poland"	"Warsaw"				1		"2017-03-01 00:00:00"	"1488438855"	"PAGE"			"$0.00"		"9180793"	"26 oz Double Wall Insulated Bottle"	"(not set)"	"(not set)"	"USD"					"Google Rucksack"		"/google+redesign/"	0	1	
"9.16222E+18"	"Direct"	30831	"Taiwan"	"not available in demo dataset"			31	2		"2017-02-05 00:00:00"	"1486351934"	"PAGE"			"$0.00"		"9182569"	"Google Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/22 oz Android Bottle"		"/google+redesign/"	0	1	
"9.73693E+18"	"Organic Search"	66306	"United States"	"not available in demo dataset"			66	4		"2016-12-05 00:00:00"	"1480969397"	"PAGE"			"$0.00"		"9184620"	"Google Men's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"Google Men's Watershed Full Zip Hoodie Grey"		"/google+redesign/"	0	1	
"7.18172E+18"	"Organic Search"	0	"Ireland"	"not available in demo dataset"				1		"2017-02-15 00:00:00"	"1487153236"	"PAGE"			"$0.00"		"9182750"	"Google Men's Performance 1/4 Zip Pullover Heather/Black"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Recycled Mouse Pad"		"/google+redesign/"	0	1	
"6.59018E+18"	"Direct"	0	"United Kingdom"	"not available in demo dataset"				1		"2017-02-17 00:00:00"	"1487342554"	"PAGE"			"$0.00"		"9182721"	"Google Men's 100% Cotton Short Sleeve Hero Tee Black"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Windup Android"		"/google+redesign/"	0	1	
"9.78745E+18"	"Direct"	1029529	"United States"	"San Francisco"			1030	2	1	"2017-07-19 00:00:00"	"1500523643"	"PAGE"			"$0.00"		"9180824"	"Foam Can and Bottle Cooler"	"(not set)"	"(not set)"	"USD"					"Waterproof Backpack"		"/google+redesign/"	0	1	
"3.22827E+18"	"Paid Search"	14053	"United States"	"not available in demo dataset"			39	3		"2017-03-25 00:00:00"	"1490511296"	"PAGE"			"$0.00"		"9182575"	"Android Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"Google Men's Airflow 1/4 Zip Pullover Black"		"/google+redesign/"	0	1	
"1.46458E+18"	"Organic Search"	0	"United States"	"not available in demo dataset"			180	8		"2017-04-26 00:00:00"	"1493234095"	"PAGE"			"$0.00"		"9184737"	"Waze Pack of 9 Decal Set"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Google G Noise-reducing Bluetooth Headphones"		"/google+redesign/"	0	1	
"5.05251E+18"	"Organic Search"	0	"Bulgaria"	"not available in demo dataset"				1		"2017-01-05 00:00:00"	"1483604872"	"PAGE"			"$0.00"		"9182663"	"Google Women's Short Sleeve Badge Tee Red Heather"	"(not set)"	"(not set)"	"USD"					"Google Electronics Accessory Pouch"		"/google+redesign/"	0	1	
"3.08708E+18"	"Direct"	100677	"United States"	"San Francisco"			512	5		"2017-01-31 00:00:00"	"1485912426"	"PAGE"			"$0.00"		"9183106"	"Google Women's Performance Hero Tee Gunmetal"	"(not set)"	"(not set)"	"USD"					"Recycled Paper Journal Set"		"/google+redesign/"	0	1	
"8.80628E+18"	"Organic Search"	120235	"United States"	"not available in demo dataset"			137	3		"2017-02-26 00:00:00"	"1488178261"	"PAGE"			"$0.00"		"9182751"	"Google Men's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"YouTube Men's Fleece Hoodie Black"		"/google+redesign/"	0	1	
"1.95746E+18"	"Display"	184700	"United States"	"not available in demo dataset"			185	8		"2017-05-16 00:00:00"	"1494941775"	"PAGE"			"$0.00"		"9182581"	"Google Women's Fleece Hoodie"	"(not set)"	"(not set)"	"USD"					"YouTube Spiral Journal with Pen"		"/google+redesign/"	0	1	
"1.81753E+18"	"Organic Search"	0	"Germany"	"Hamburg"				1		"2017-05-17 00:00:00"	"1495028673"	"PAGE"			"$0.00"		"9183106"	"Google Women's Performance Hero Tee Gunmetal"	"(not set)"	"(not set)"	"USD"					"Google Power Bank"		"/google+redesign/"	0	1	
"2.49576E+18"	"Direct"	208886	"Canada"	"not available in demo dataset"			209	2		"2016-11-30 00:00:00"	"1480527371"	"PAGE"			"$0.00"		"9180801"	"Engraved Ceramic Google Mug"	"(not set)"	"(not set)"	"USD"					"Google Bib Red"		"/google+redesign/"	0	1	
"5.13674E+18"	"Organic Search"	96526	"United States"	"not available in demo dataset"			97	5		"2017-03-15 00:00:00"	"1489621948"	"PAGE"			"$0.00"		"9180833"	"Rubber Grip Ballpoint Pen 4 Pack"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Fashion Sunglasses & Pouch"		"/google+redesign/"	0	1	
"4.99691E+17"	"Referral"	0	"United States"	"Sunnyvale"			29	3		"2016-10-30 00:00:00"	"1477878848"	"PAGE"			"$0.00"		"9182736"	"Google Men's Heavyweight Long Sleeve Hero Tee Navy"	"(not set)"	"(not set)"	"USD"					"Google Women's 3/4 Sleeve Baseball Raglan Heather/Black"		"/google+redesign/"	0	1	
"2.59009E+18"	"Direct"	88043	"United States"	"New York"			88	4		"2017-04-18 00:00:00"	"1492549002"	"PAGE"			"$0.00"		"9182785"	"Google Women's Lightweight Microfleece Jacket"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Fashion Sunglasses & Pouch"		"/google+redesign/"	0	1	
"5.23884E+18"	"Paid Search"	0	"United States"	"not available in demo dataset"				1		"2017-02-04 00:00:00"	"1486229234"	"PAGE"			"$0.00"		"9182658"	"Google Women's Short Sleeve Hero Tee Sky Blue"	"(not set)"	"(not set)"	"USD"					"Android Women's Fleece Hoodie"		"/google+redesign/"	0	1	
"6.03391E+18"	"Organic Search"	0	"United States"	"Atlanta"			21	2		"2017-06-08 00:00:00"	"1496914839"	"PAGE"			"$0.00"		"9182723"	"Google Men's 100% Cotton Short Sleeve Hero Tee White"	"(not set)"	"(not set)"	"USD"					"The Google Merchandise Store/Pen Pencil & Highlighter Set"		"/google+redesign/"	0	1	
"5.00376E+18"	"Direct"	0	"United States"	"New York"				1		"2016-10-25 00:00:00"	"1477410373"	"PAGE"			"$0.00"		"9182800"	"Google Onesie Royal Blue"	"(not set)"	"(not set)"	"USD"					"YouTube Onesie Heather"		"/google+redesign/"	0	1	
"7.17348E+18"	"Direct"	0	"United States"	"New York"				1	1	"2017-07-26 00:00:00"	"1501091655"	"PAGE"			"$0.00"		"9182784"	"Google Women's Short Sleeve Hero Tee White"	"(not set)"	"(not set)"	"USD"					"Google Alpine Style Backpack"		"/google+redesign/"	0	1	
"3.25272E+18"	"Paid Search"	0	"United States"	"not available in demo dataset"				1		"2017-06-10 00:00:00"	"1497086828"	"PAGE"			"$0.00"		"9180824"	"Foam Can and Bottle Cooler"	"(not set)"	"(not set)"	"USD"					"Google Men's Vintage Badge Tee White"		"/google+redesign/"	0	1	
"2.8437E+18"	"Organic Search"	0	"United States"	"(not set)"				1	1	"2017-07-19 00:00:00"	"1500529947"	"PAGE"			"$0.00"		"9182575"	"Android Men's  Zip Hoodie"	"(not set)"	"(not set)"	"USD"					"Yoga Mat"		"/google+redesign/"	0	1	
"9.3902E+17"	"Referral"	0	"United States"	"San Francisco"			6	2		"2017-04-11 00:00:00"	"1491936191"	"PAGE"			"$0.00"		"9182774"	"Google Women's Yoga Pants"	"(not set)"	"(not set)"	"USD"					"Google Women's Performance Full Zip Jacket Black"		"/google+redesign/"	0	1	
"6.8612E+18"	"Direct"	96804	"Taiwan"	"(not set)"			216	5		"2017-02-03 00:00:00"	"1486116248"	"PAGE"			"$0.00"		"9182772"	"Google Women's Performance Full Zip Jacket Black"	"(not set)"	"(not set)"	"USD"					"Google Women's Short Sleeve Hero Tee White"		"/google+redesign/"	0	1	
"6.54904E+18"	"Organic Search"	0	"India"	"not available in demo dataset"				1		"2016-08-30 00:00:00"	"1472547377"	"PAGE"			"$0.00"		"9182581"	"Google Women's Fleece Hoodie"	"(not set)"	"(not set)"	"USD"					"Google Youth Tee Fruit Games Banana"		"/google+redesign/"	0	1	
"6.66626E+17"	"Organic Search"	47111	"United States"	"New York"			47	3	1	"2017-07-31 00:00:00"	"1501519405"	"PAGE"			"$0.00"		"9182765"	"Google Women's Convertible Vest-Jacket Sea Foam Green"	"(not set)"	"(not set)"	"USD"					"Android Stretch Fit Hat"		"/google+redesign/"	0	1	
"7.35681E+18"	"Organic Search"	0	"United States"	"Mountain View"				1		"2017-05-15 00:00:00"	"1494874375"	"PAGE"			"$0.00"		"9182781"	"Google Women's Short Sleeve Hero Tee Black"	"(not set)"	"(not set)"	"USD"					"Google Men's Bike Short Sleeve Tee Charcoal"		"/google+redesign/"	0	1	
"2.87281E+18"	"Organic Search"	73478	"Canada"	"not available in demo dataset"			73	4		"2017-01-29 00:00:00"	"1485750702"	"PAGE"			"$0.00"		"9182701"	"Android Men's Long Sleeve Badge Crew Tee Heather"	"(not set)"	"(not set)"	"USD"					"YouTube Men's Skater Tee Charcoal"		"/google+redesign/"	0	1	
"6.25399E+18"	"Organic Search"	21676	"Indonesia"	"not available in demo dataset"			66	4		"2017-06-18 00:00:00"	"1497780001"	"PAGE"			"$0.00"		"9183106"	"Google Women's Performance Hero Tee Gunmetal"	"(not set)"	"(not set)"	"USD"					"YouTube Women's Short Sleeve Hero Tee Charcoal"		"/google+redesign/"	0	1	


### Answer:
the modified format without "GG" as prefix suggests it is the format used for items no longer stocked. Woudl suggest adding a column to identify these items as current or discontinued? 



Question 4: no time

SQL Queries:

Answer:



Question 5: no time

SQL Queries:

Answer:
