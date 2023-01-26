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

Question 2: # Question 1: Which product category do people spend the most time on the site for? 

SQL Queries (expand)
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



Answer: expand
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


Question 3: 

SQL Queries:

Answer:



Question 4: 

SQL Queries:

Answer:



Question 5: 

SQL Queries:

Answer:
