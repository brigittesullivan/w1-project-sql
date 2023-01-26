Answer the following questions and provide the SQL queries used to find the answer.

    
## **Question 1: Which cities and countries have the highest level of transaction revenues on the site?**

```sql
SELECT 
"country", 
"city", 
sum("transactionrevenue")
FROM all_sessions
GROUP BY
"city",
"country"
HAVING sum("transactionrevenue") IS NOT NULL
ORDER BY "country"
```
Answer:
"United States"	"Sunnyvale"	"$200,000,000.00"
"United States"	"not available in demo dataset"	"$2,190,950,000.00"

almost no data for transaction revenue only **4** rows have a not null value out of 15,134. 
I removed this column during my data cleaning, so the result is using the uncleaned raw data
QA: 
```sql
SELECT 
"country", 
"city", 
"transactionrevenue"
FROM
all_sessions
WHERE "transactionrevenue" IS NOT NULL
```




## **Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:
```sql 
SELECT 
"country",
"city",
ROUND(avg("productquantity"),2) as avg
FROM
all_sessions
GROUP BY 
"country",
"city"
HAVING sum("productquantity") IS NOT NULL
ORDER BY "country", "city"
```

QA CHECK:
```sql 
SELECT 
"country",
"city",
sum("productquantity"),ROUND(avg("productquantity"),2) as avg,count("productquantity")
FROM
all_sessions
GROUP BY 
"country",
"city"
HAVING sum("productquantity") IS NOT NULL
ORDER BY "country", "city"
```

Answer:
[Q2 answer image](/Users/brigitteasullivan/Desktop/w1-project-sql/Question_2_answer.png)

"Argentina"		1.00
"Canada"		1.00
"Colombia"		1.00
"Finland"		1.00
"France"		1.00
"India"	"Bengaluru"	1.00
"Ireland"	"Dublin"	1.00
"Mexico"		1.00
"Spain"	"Madrid"	10.00
"United States"	"Ann Arbor"	1.00
"United States"	"Atlanta"	4.00
"United States"	"Chicago"	1.00
"United States"	"Columbus"	1.00
"United States"	"Dallas"	1.00
"United States"	"Detroit"	1.00
"United States"	"Houston"	2.00
"United States"	"Los Angeles"	1.00
"United States"	"Mountain View"	1.00
"United States"	"New York"	1.17
"United States"	"Palo Alto"	1.00
"United States"	"Salem"	8.00
"United States"	"San Francisco"	1.00
"United States"	"San Jose"	1.00
"United States"	"Seattle"	1.00
"United States"	"Sunnyvale"	1.00
"United States"		9.85





## **Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





## **Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**

### SQL Query 1:

``` sql
-- Top Selling Product by city
--- sum_total_ordered = most popular item ordered
SELECT country, city, p.name, sum_total_ordered
FROM (
	SELECT country, city, productSKU, sum_total_ordered, city_max
	FROM (
			SELECT 
				country, 
				city,
				productSKU, 
				SKU, 
				sum_total_ordered,
			-- 	max(sum_total_ordered) OVER (PARTITION BY  ac3."city") as city_max
			max(sum_total_ordered) OVER (PARTITION BY city) as city_max
			FROM 
				(SELECT 
					ac3."country" as country
					, ac3."city" AS city
					, ac3."productsku" AS productSKU
					, sbk."SKU" AS SKU
					, sum(sbk."total_ordered") AS sum_total_ordered
				FROM all_sessions_clean3 AS ac3
				JOIN sales_by_sku AS sbk
				ON ac3."productsku" = sbk."SKU"
				GROUP BY 	
					ac3."country"
					, ac3."city" 
					, ac3."productsku"
					, sbk."SKU"
				ORDER BY ac3."city")  
				AS subq1
		) AS subq2
	WHERE sum_total_ordered = city_max
		 ) AS subq2
JOIN products AS p
ON productSKU = P."SKU"
ORDER BY country, city_max DESC
```
### Answer to Query 1:
"Argentina"	"Buenos Aires"	"Sport Bag"	70
"Argentina"	"Santa Fe"	"SPF-15 Slim & Slender Lip Balm"	60
"Argentina"	"Rosario"	" Men's Vintage Badge Tee Black"	1
"Australia"	"Sydney"	" Blackout Cap"	189
"Australia"	"Melbourne"	" Hard Cover Journal"	170
"Australia"	"Perth"	" Custom Decals"	30
"Australia"	"Brisbane"	" Twill Cap"	9
"Australia"	"Adelaide"	" Men's Watershed Full Zip Hoodie Grey"	3
"Austria"	"Vienna"	" Men's 100% Cotton Short Sleeve Hero Tee White"	15
"Belgium"	"Ghent"	"Windup Android"	16
"Belgium"	"Brussels"	" Men's 100% Cotton Short Sleeve Hero Tee Black"	4
"Belgium"	"Antwerp"	"Colored Pencil Set"	3
"Brazil"	"Rio de Janeiro"	" Blackout Cap"	189
"Brazil"	"Sao Paulo"	"7 Dog Frisbee"	104
"Brazil"	"Belo Horizonte"	"Collapsible Shopping Bag"	43
"Brazil"	"Fortaleza"	"Android Luggage Tag"	0
"Canada"	"Toronto"	" 17oz Stainless Steel Sport Bottle"	334
"Canada"	"Sherbrooke"	" Blackout Cap"	189
"Canada"	"Montreal"	"Android 17oz Stainless Steel Sport Bottle"	167
"Canada"	"Vancouver"	" Hard Cover Journal"	85
"Canada"	"Kitchener"	"Keyboard DOT Sticker"	53
"Canada"	"Mississauga"	"Collapsible Shopping Bag"	43
"Canada"	"Calgary"	"Recycled Mouse Pad"	39
"Canada"	"Quebec City"	" Custom Decals"	30
"Canada"	"Burnaby"	" Men's 100% Cotton Short Sleeve Hero Tee White"	15
"Canada"	"Edmonton"	" Stylus Pen w/ LED Light"	2
"Canada"	"St. John's"	" 2200mAh Micro Charger"	0
"Canada"	"Waterloo"	" Men's Long Sleeve Raglan Ocean Blue"	0
"Chile"	"Santiago"	"Sport Bag"	70
"China"	"Beijing"	" Men's Airflow 1/4 Zip Pullover Lapis"	0
"Colombia"	"Bogota"	" Learning Thermostat 3rd Gen-USA - Stainless Steel"	94
"Colombia"	"Medellin"	"Bottle Opener Clip"	11
"Croatia"	"Zagreb"	" Men's Watershed Full Zip Hoodie Grey"	6
"Czechia"	"Brno"	"Leatherette Journal"	319
"Czechia"	"Prague"	" Men's 100% Cotton Short Sleeve Hero Tee White"	30
"Czechia"	"Prague"	" Custom Decals"	30
"Denmark"	"Copenhagen"	"Rocket Flashlight"	16
"El Salvador"	"San Salvador"	" Device Holder Sticky Pad"	0
"Finland"	"Helsinki"	"Android Onesie Gold"	6
"France"	"Paris"	"Android 17oz Stainless Steel Sport Bottle"	167
"France"	"Montreuil"	"Collapsible Shopping Bag"	43
"France"	"Courbevoie"	" Men's 100% Cotton Short Sleeve Hero Tee White"	15
"France"	"Marseille"	" Men's 100% Cotton Short Sleeve Hero Tee Black"	4
"France"	"Villeneuve-d'Ascq"	" Snapback Hat Black"	1
"Germany"	"Munich"	"Foam Can and Bottle Cooler"	253
"Germany"	"Hamburg"	" Blackout Cap"	189
"Germany"	"Berlin"	" Doodle Decal"	34
"Germany"	"Berlin"	"Switch Tone Color Crayon Pen"	34
"Germany"	"Frankfurt"	" Bib White"	7
"Greece"	"Athens"	" Hard Cover Journal"	85
"Greece"	"Thessaloniki"	" Bib Red"	7
"Hong Kong"	"Hong Kong"	"Leatherette Journal"	319
"Hungary"	"Budapest"	"Recycled Mouse Pad"	39
"India"	"Pune"	"Ballpoint LED Light Pen"	456
"India"	"Mumbai"	"Leatherette Journal"	319
"India"	"Hyderabad"	" Hard Cover Journal"	255
"India"	"Chennai"	" Hard Cover Journal"	255
"India"	"New Delhi"	" Hard Cover Journal"	85
"India"	"Indore"	" Hard Cover Journal"	85
"India"	"Bengaluru"	" Hard Cover Journal"	85
"India"	"Kolkata"	" Leather Journal"	82
"India"	"Ahmedabad"	" Canvas Tote Natural/Navy"	62
"India"	"Gurgaon"	" 22 oz Water Bottle"	40
"India"	"Jaipur"	" Men's 100% Cotton Short Sleeve Hero Tee White"	15
"India"	"Chandigarh"	" Men's 100% Cotton Short Sleeve Hero Tee Navy"	13
"India"	"Kharagpur"	" Tri-blend Hoodie Grey"	11
"India"	"Nanded"	" Men's Short Sleeve Hero Tee Charcoal"	6
"India"	"Patna"	"22 oz Android Bottle"	2
"India"	"Lucknow"	" Men's Vintage Tank"	0
"India"	"Lucknow"	"Android Men's Short Sleeve Tri-blend Hero Tee Grey"	0
"Indonesia"	"Jakarta"	"22 oz  Bottle Infuser"	100
"Indonesia"	"Bandung"	" Men's Short Sleeve Hero Tee Charcoal"	6
"Ireland"	"Dublin"	" 17oz Stainless Steel Sport Bottle"	334
"Ireland"	"Cork"	" Custom Decals"	30
"Israel"	"Tel Aviv-Yafo"	"Android 17oz Stainless Steel Sport Bottle"	334
"Italy"	"Rome"	"Leatherette Journal"	319
"Italy"	"Milan"	"22 oz  Bottle Infuser"	100
"Japan"	"Shinjuku"	" 17oz Stainless Steel Sport Bottle"	334
"Japan"	"Minato"	" Sunglasses"	146
"Japan"	"Osaka"	" Protect Smoke + CO White Wired Alarm-USA"	42
"Japan"	"Yokohama"	" Slim Utility Travel Bag"	13
"Japan"	"Chuo"	" Women's Scoop Neck Tee Black"	0
"Japan"	"Shibuya"	" Men's Vintage Badge Tee Sage"	0
"Japan"	"Nagoya"	" Women's Convertible Vest-Jacket Sea Foam Green"	0
"Kenya"	"Nairobi"	" Men's Long & Lean Tee Grey"	0
"Kenya"	"Nairobi"	" Flashlight"	0
"Lithuania"	"Vilnius"	" Men's 100% Cotton Short Sleeve Hero Tee Red"	1
"Malaysia"	"Kuala Lumpur"	"26 oz Double Wall Insulated Bottle"	97
"Malaysia"	"Ipoh"	"Bottle Opener Clip"	11
"Malaysia"	"Petaling Jaya"	" Women's 1/4 Zip Performance Pullover Black"	3
"Malaysia"	"Petaling Jaya"	" Women's Short Sleeve Hero Tee Black"	3
"Mexico"	"Mexico City"	" Learning Thermostat 3rd Gen-USA - Stainless Steel"	94
"Mexico"	"Culiacan"	" Men's Short Sleeve Hero Tee Black"	8
"Netherlands"	"Amsterdam"	" Hard Cover Journal"	85
"New Zealand"	"Auckland"	" Women's Lightweight Microfleece Jacket"	0
"New Zealand"	"Auckland"	" G Noise-reducing Bluetooth Headphones"	0
"Norway"	"Oslo"	" Men's 100% Cotton Short Sleeve Hero Tee Red"	1
"Pakistan"	"Lahore"	" Tube Power Bank"	1
"Pakistan"	"Karachi"	" Men's Long Sleeve Raglan Ocean Blue"	0
"Pakistan"	"Karachi"	"Ballpoint Stylus Pen"	0
"Paraguay"	"Asuncion"	" Men's 100% Cotton Short Sleeve Hero Tee Navy"	13
"Peru"	"La Victoria"	"22 oz  Bottle Infuser"	50
"Philippines"	"Taguig"	"Metal Texture Roller Pen"	48
"Philippines"	"Manila"	"8 pc Android Sticker Sheet"	19
"Philippines"	"Quezon City"	" Men's 100% Cotton Short Sleeve Hero Tee Navy"	13
"Philippines"	"Makati"	" G Noise-reducing Bluetooth Headphones"	0
"Poland"	"Warsaw"	"Keyboard DOT Sticker"	106
"Poland"	"Poznan"	" Men's 100% Cotton Short Sleeve Hero Tee Black"	4
"Portugal"	"Lisbon"	" Blackout Cap"	189
"Qatar"	"Doha"	" Men's 100% Cotton Short Sleeve Hero Tee Black"	4
"Romania"	"Bucharest"	" Canvas Tote Natural/Navy"	62
"Romania"	"Timisoara"	" Screen Cleaning Cloth"	12
"Romania"	"Cluj-Napoca"	" Men's 100% Cotton Short Sleeve Hero Tee Black"	4
"Romania"	"Iasi"	" Men's Vintage Henley"	2
"Russia"	"Saint Petersburg"	"Leatherette Journal"	319
"Russia"	"Vladivostok"	" Canvas Tote Natural/Navy"	62
"Russia"	"Moscow"	"SPF-15 Slim & Slender Lip Balm"	60
"Saudi Arabia"	"Riyadh"	"Leatherette Journal"	319
"Singapore"	"Singapore"	" Blackout Cap"	189
"Slovakia"	"Bratislava"	" Learning Thermostat 3rd Gen-USA - Copper"	0
"South Africa"	"Westville"	"Sport Bag"	70
"South Korea"	"Seoul"	"Ballpoint LED Light Pen"	456
"Spain"	"Madrid"	"SPF-15 Slim & Slender Lip Balm"	120
"Spain"	"Barcelona"	"26 oz Double Wall Insulated Bottle"	97
"Spain"	"Pozuelo de Alarcon"	" Hard Cover Journal"	85
"Sri Lanka"	"Colombo"	" Men's 100% Cotton Short Sleeve Hero Tee White"	15
"Sweden"	"Stockholm"	"Metal Texture Roller Pen"	48
"Switzerland"	"Zurich"	"Sport Bag"	140
"Taiwan"	"Longtan District"	"26 oz Double Wall Insulated Bottle"	97
"Taiwan"	"Zhongli District"	" Hard Cover Journal"	85
"Thailand"	"Bangkok"	"Foam Can and Bottle Cooler"	253
"Turkey"	"Istanbul"	" Hard Cover Journal"	85
"Turkey"	"Izmir"	" Women's Short Sleeve Hero Tee White"	4
"Ukraine"	"Kiev"	"Keyboard DOT Sticker"	53
"Ukraine"	"Kharkiv"	" Women's V-Neck Tee Charcoal"	4
"United Arab Emirates"	"Dubai"	"Leatherette Journal"	319
"United Kingdom"	"London"	" 17oz Stainless Steel Sport Bottle"	668
"United Kingdom"	"Wrexham"	" Laptop and Cell Phone Stickers"	13
"United Kingdom"	"Salford"	" Car Clip Phone Holder"	2
"United Kingdom"	"Coventry"	" Youth Short Sleeve Tee Red"	0
"United Kingdom"	"Manchester"	" G Noise-reducing Bluetooth Headphones"	0
"United States"		" 17oz Stainless Steel Sport Bottle"	6680
"United States"	"Mountain View"	" Cam Indoor Security Camera - USA"	2448
"United States"	"Los Angeles"	" 17oz Stainless Steel Sport Bottle"	1336
"United States"	"Palo Alto"	" 17oz Stainless Steel Sport Bottle"	1002
"United States"	"New York"	" 17oz Stainless Steel Sport Bottle"	1002
"United States"	"San Francisco"	"Android 17oz Stainless Steel Sport Bottle"	1002
"United States"	"Sunnyvale"	" Cam Outdoor Security Camera - USA"	672
"United States"	"Salem"	" 17oz Stainless Steel Sport Bottle"	668
"United States"	"Chicago"	" 17oz Stainless Steel Sport Bottle"	668
"United States"	"Seattle"	"Ballpoint LED Light Pen"	456
"United States"	"Boston"	"Ballpoint LED Light Pen"	456
"United States"	"San Jose"	"Ballpoint LED Light Pen"	456
"United States"	"Santa Clara"	"Ballpoint LED Light Pen"	456
"United States"	"Rexburg"	" 17oz Stainless Steel Sport Bottle"	334
"United States"	"San Antonio"	"Android 17oz Stainless Steel Sport Bottle"	334
"United States"	"Philadelphia"	"Leatherette Journal"	319
"United States"	"Austin"	"Leatherette Journal"	319
"United States"	"Ann Arbor"	"Foam Can and Bottle Cooler"	253
"United States"	"San Bruno"	"Foam Can and Bottle Cooler"	253
"United States"	"Charlotte"	"7 Dog Frisbee"	208
"United States"	"Houston"	" Blackout Cap"	189
"United States"	"Avon"	" Blackout Cap"	189
"United States"	"Sacramento"	" Blackout Cap"	189
"United States"	"Irvine"	"Android 17oz Stainless Steel Sport Bottle"	167
"United States"	"Dallas"	" Sunglasses"	146
"United States"	"Atlanta"	" Protect Smoke + CO White Wired Alarm-USA"	126
"United States"	"Cambridge"	" Cam Outdoor Security Camera - USA"	112
"United States"	"Pittsburgh"	" Cam Outdoor Security Camera - USA"	112
"United States"	"Kalamazoo"	"Satin Black Ballpoint Pen"	105
"United States"	"Washington"	"7 Dog Frisbee"	104
"United States"	"Phoenix"	" Cam Indoor Security Camera - USA"	102
"United States"	"Redwood City"	" Cam Indoor Security Camera - USA"	102
"United States"	"Cupertino"	" Cam Indoor Security Camera - USA"	102
"United States"	"Menlo Park"	" Cam Indoor Security Camera - USA"	102
"United States"	"Bellingham"	" Learning Thermostat 3rd Gen-USA - Stainless Steel"	94
"United States"	"Nashville"	" Learning Thermostat 3rd Gen-USA - Stainless Steel"	94
"United States"	"Kirkland"	" Learning Thermostat 3rd Gen-USA - Stainless Steel"	94
"United States"	"Bellflower"	" Custom Decals"	60
"United States"	"Oakland"	"Keyboard DOT Sticker"	53
"United States"	"Redmond"	"22 oz  Bottle Infuser"	50
"United States"	"Lake Oswego"	"Recycled Mouse Pad"	39
"United States"	"San Diego"	"Recycled Mouse Pad"	39
"United States"	"Fremont"	" Protect Smoke + CO White Battery Alarm-USA"	24
"United States"	"Detroit"	" 22 oz Water Bottle"	23
"United States"	"Tempe"	"Windup Android"	16
"United States"	"Denver"	"Crunch Noise Dog Toy"	14
"United States"	"Milpitas"	"Crunch Noise Dog Toy"	14
"United States"	"The Dalles"	" Laptop and Cell Phone Stickers"	13
"United States"	"LaFayette"	" Men's 100% Cotton Short Sleeve Hero Tee Navy"	13
"United States"	"Akron"	" Men's 100% Cotton Short Sleeve Hero Tee Navy"	13
"United States"	"Portland"	" Men's 100% Cotton Short Sleeve Hero Tee Navy"	13
"United States"	"Santa Monica"	" Slim Utility Travel Bag"	13
"United States"	"Eau Claire"	" Men's Short Sleeve Hero Tee Charcoal"	12
"United States"	"South San Francisco"	" Rucksack"	11
"United States"	"Boulder"	"Bottle Opener Clip"	11
"United States"	"San Mateo"	" Tri-blend Hoodie Grey"	11
"United States"	"South San Francisco"	"Android Sticker Sheet Ultra Removable"	11
"United States"	"Orlando"	" Men's Short Sleeve Hero Tee Black"	8
"United States"	"Jersey City"	" Youth Short Sleeve Tee White"	7
"United States"	"East Lansing"	"25L Classic Rucksack"	7
"United States"	"St. Louis"	" Bib Red"	7
"United States"	"Oviedo"	" 5-Panel Snapback Cap"	7
"United States"	"University Park"	"Waterproof Backpack"	5
"United States"	"Norfolk"	"Suitcase Organizer Cubes"	5
"United States"	"Ashburn"	"Compact Selfie Stick"	5
"United States"	"Jacksonville"	" Device Stand"	5
"United States"	"Columbia"	" Device Stand"	5
"United States"	"Las Vegas"	" Men's 100% Cotton Short Sleeve Hero Tee Black"	4
"United States"	"Richardson"	"Micro Wireless Earbud"	4
"United States"	"Madison"	" Tote Bag"	3
"United States"	"Druid Hills"	"Colored Pencil Set"	3
"United States"	"Council Bluffs"	" Kick Ball"	3
"United States"	"Stanford"	" Men's  Zip Hoodie"	3
"United States"	"Wellesley"	"Colored Pencil Set"	3
"United States"	"Chico"	"Android Men's Long Sleeve Badge Crew Tee Heather"	2
"United States"	"Kansas City"	" Women's Short Sleeve Hero Tee Heather"	1
"United States"	"Piscataway Township"	" Men's 100% Cotton Short Sleeve Hero Tee Red"	1
"United States"	"Kansas City"	" Women's Short Sleeve Hero Tee Red Heather"	1
"United States"	"Greer"	" Men's Quilted Insulated Vest Black"	1
"United States"	"Indianapolis"	"Ballpoint Stylus Pen"	0
"United States"	"Tampa"	"Android Wool Heather Cap Heather/Black"	0
"United States"	"Hayward"	" Men's Vintage Badge Tee White"	0
"United States"	"South El Monte"	" Men's Vintage Badge Tee White"	0
"United States"	"Pleasanton"	"Electronics Accessory Pouch"	0
"United States"	"Forest Park"	" Men's Microfiber 1/4 Zip Pullover Blue/Indigo"	0
"United States"	"Marlboro"	" Men's Microfiber 1/4 Zip Pullover Blue/Indigo"	0
"United States"	"Minneapolis"	"Android Men's Short Sleeve Tri-blend Hero Tee Grey"	0
"United States"	"Westlake Village"	" Men's Long Sleeve Raglan Ocean Blue"	0
"United States"	"Panama City"	" Men's Convertible Vest-Jacket Pewter"	0
"United States"	"Minneapolis"	" Men's Vintage Badge Tee White"	0
"United States"	"Goose Creek"	"Android Wool Heather Cap Heather/Black"	0
"Uruguay"	"Montevideo"	" Men's 100% Cotton Short Sleeve Hero Tee White"	15
"Venezuela"	"Maracaibo"	"Android Men's Vintage Henley"	2
"Vietnam"	"Hanoi"	"26 oz Double Wall Insulated Bottle"	97
"Vietnam"	"Ho Chi Minh City"	"Keyboard DOT Sticker"	53

### SQL Query 2:

```sql

-- Top Selling Product by country
SELECT 
	country
	, p.name
	, sum_total_ordered
	
FROM (
	SELECT country, productSKU, sum_total_ordered 
	FROM
	(
		SELECT country, 
			productSKU, 
			SKU, 
			sum_total_ordered,
			max(sum_total_ordered) OVER (PARTITION BY country) as country_max
		FROM 
			(SELECT 
				ac3."country" as country
				, ac3."productsku" AS productSKU
				, sbk."SKU" AS SKU
				, sum(sbk."total_ordered") AS sum_total_ordered
			FROM all_sessions_clean3 AS ac3
			JOIN sales_by_sku AS sbk
			ON ac3."productsku" = sbk."SKU"
			GROUP BY 	ac3."country"
						, ac3."productsku"
						, sbk."SKU"
			ORDER BY ac3."country" ) AS subq1
		GROUP BY country, productSKU, SKU, sum_total_ordered
		ORDER BY country) AS subq2
	WHERE sum_total_ordered = country_max  ) as subq2
JOIN products AS p
ON productSKU = p."SKU"
ORDER BY sum_total_ordered DESC
```


### Answer to Query 2:
```
"United States"	" 17oz Stainless Steel Sport Bottle"	14362
"United Kingdom"	" Hard Cover Journal"	1785
"Germany"	"Ballpoint LED Light Pen"	1368
"Canada"	" 17oz Stainless Steel Sport Bottle"	1336
"India"	" 17oz Stainless Steel Sport Bottle"	1002
"Italy"	"Leatherette Journal"	957
"Japan"	"Ballpoint LED Light Pen"	912
"Hong Kong"	"Leatherette Journal"	638
"Australia"	" Hard Cover Journal"	510
"Czechia"	" Hard Cover Journal"	510
"Brazil"	"Foam Can and Bottle Cooler"	506
"Switzerland"	"Ballpoint LED Light Pen"	456
"Taiwan"	"Ballpoint LED Light Pen"	456
"Spain"	"Ballpoint LED Light Pen"	456
"South Korea"	"Ballpoint LED Light Pen"	456
"Netherlands"	"Ballpoint LED Light Pen"	456
"Mexico"	"Ballpoint LED Light Pen"	456
"Croatia"	"Ballpoint LED Light Pen"	456
"Malaysia"	"Ballpoint LED Light Pen"	456
"Denmark"	" Hard Cover Journal"	425
"Turkey"	" Hard Cover Journal"	340
"Ireland"	" 17oz Stainless Steel Sport Bottle"	334
"Saudi Arabia"	" 17oz Stainless Steel Sport Bottle"	334
"France"	"Android 17oz Stainless Steel Sport Bottle"	334
"Singapore"	" 17oz Stainless Steel Sport Bottle"	334
"Belgium"	" 17oz Stainless Steel Sport Bottle"	334
"Kuwait"	" 17oz Stainless Steel Sport Bottle"	334
"Israel"	"Android 17oz Stainless Steel Sport Bottle"	334
"Ireland"	"Android 17oz Stainless Steel Sport Bottle"	334
"United Arab Emirates"	"Leatherette Journal"	319
"Greece"	"Leatherette Journal"	319
"Russia"	"Leatherette Journal"	319
"Indonesia"	"22 oz  Bottle Infuser"	300
"Colombia"	" Hard Cover Journal"	255
"Ukraine"	" Hard Cover Journal"	255
"Romania"	"Foam Can and Bottle Cooler"	253
"Thailand"	"Foam Can and Bottle Cooler"	253
"Poland"	"7 Dog Frisbee"	208
"Pakistan"	"22 oz  Bottle Infuser"	200
"Guatemala"	" Blackout Cap"	189
"Portugal"	" Blackout Cap"	189
"Laos"	" Hard Cover Journal"	170
"Argentina"	" Hard Cover Journal"	170
"Slovakia"	" Hard Cover Journal"	170
"Venezuela"	" Hard Cover Journal"	170
"Philippines"	"Android 17oz Stainless Steel Sport Bottle"	167
"New Zealand"	"22 oz  Bottle Infuser"	150
"Sweden"	" Cam Outdoor Security Camera - USA"	112
"Honduras"	" Cam Outdoor Security Camera - USA"	112
"Peru"	"22 oz  Bottle Infuser"	100
"Vietnam"	"26 oz Double Wall Insulated Bottle"	97
	"26 oz Double Wall Insulated Bottle"	97
"Morocco"	" Learning Thermostat 3rd Gen-USA - Stainless Steel"	94
"Georgia"	" Custom Decals"	90
"Oman"	" Hard Cover Journal"	85
"Ethiopia"	" Hard Cover Journal"	85
"Trinidad & Tobago"	" Hard Cover Journal"	85
"Slovenia"	" Hard Cover Journal"	85
"Papua New Guinea"	" Hard Cover Journal"	85
"South Africa"	"Sport Bag"	70
"Chile"	"Sport Bag"	70
"Bulgaria"	"Spiral Notebook and Pen Set"	69
"C√¥te d‚ÄôIvoire"	" Custom Decals"	60
"Costa Rica"	" Power Bank"	56
"Mauritius"	" Power Bank"	56
"Finland"	"Keyboard DOT Sticker"	53
"Bangladesh"	"Keyboard DOT Sticker"	53
"Nigeria"	"Keyboard DOT Sticker"	53
"Norway"	"22 oz  Bottle Infuser"	50
"Panama"	"22 oz  Bottle Infuser"	50
"Hungary"	"22 oz  Bottle Infuser"	50
"Dominican Republic"	"22 oz  Bottle Infuser"	50
"Nepal"	"22 oz  Bottle Infuser"	50
"San Marino"	"22 oz  Bottle Infuser"	50
"Albania"	"22 oz  Bottle Infuser"	50
"Lithuania"	"22 oz  Bottle Infuser"	50
"Macedonia (FYROM)"	"22 oz  Bottle Infuser"	50
"Egypt"	"22 oz  Bottle Infuser"	50
"Tunisia"	"22 oz  Bottle Infuser"	50
"Uruguay"	"22 oz  Bottle Infuser"	50
"Myanmar (Burma)"	"22 oz  Bottle Infuser"	50
"Kazakhstan"	"Collapsible Shopping Bag"	43
"Serbia"	"Switch Tone Color Crayon Pen"	34
"R√©union"	" Doodle Decal"	34
"Moldova"	" Custom Decals"	30
"Mali"	" Custom Decals"	30
"Montenegro"	" Custom Decals"	30
"Puerto Rico"	" Custom Decals"	30
"Sri Lanka"	" Men's 100% Cotton Short Sleeve Hero Tee White"	30
"Sri Lanka"	" Custom Decals"	30
"Austria"	" Custom Decals"	30
"Kyrgyzstan"	"Rocket Flashlight"	16
"Armenia"	"Windup Android"	16
"Bahrain"	" Men's 100% Cotton Short Sleeve Hero Tee White"	15
"China"	" Men's 100% Cotton Short Sleeve Hero Tee White"	15
"China"	"Android Hard Cover Journal"	15
"Ghana"	" Men's 100% Cotton Short Sleeve Hero Tee White"	15
"Paraguay"	" Men's 100% Cotton Short Sleeve Hero Tee Navy"	13
"Uganda"	" Laptop and Cell Phone Stickers"	13
"El Salvador"	" Men's 100% Cotton Short Sleeve Hero Tee Navy"	13
"Zimbabwe"	" Screen Cleaning Cloth"	12
"Jersey"	" Tri-blend Hoodie Grey"	11
"Tanzania"	" Twill Cap"	9
"Algeria"	" Twill Cap"	9
"Latvia"	" Twill Cap"	9
"Cambodia"	" Twill Cap"	9
"Estonia"	" Men's Short Sleeve Hero Tee Black"	8
"Bolivia"	" Men's Short Sleeve Hero Tee Black"	8
"Jordan"	"Suitcase Organizer Cubes"	5
"Botswana"	"Waterproof Backpack"	5
"Cyprus"	"Suitcase Organizer Cubes"	5
"Nicaragua"	"Compact Selfie Stick"	5
"Qatar"	" Men's 100% Cotton Short Sleeve Hero Tee Black"	4
"Palestine"	" Laptop Backpack"	3
"Ecuador"	" Men's  Zip Hoodie"	3
"Ecuador"	" Men's Watershed Full Zip Hoodie Grey"	3
"Bahamas"	" Twill Cap"	3
"Macau"	" Twill Cap"	3
"Jamaica"	" Men's  Zip Hoodie"	3
"Belarus"	" Stylus Pen w/ LED Light"	2
"Brunei"	" Toddler Short Sleeve Tee Red"	2
"Brunei"	" Men's Vintage Henley"	2
"Kenya"	" Women's Short Sleeve Hero Tee Grey"	2
"Sint Maarten"	" Stylus Pen w/ LED Light"	2
"Bosnia & Herzegovina"	" Toddler Short Sleeve Tee Red"	2
"Gibraltar"	" Men's Vintage Henley"	2
"Belarus"	" Women's Performance Full Zip Jacket Black"	2
"Martinique"	" Men's Fleece Hoodie Black"	2
"Iraq"	" Men's Vintage Badge Tee Black"	1
"Kosovo"	" Men's Vintage Badge Tee Black"	1
"Maldives"	" Men's Performance Full Zip Jacket Black"	1
"Iceland"	" Insulated Stainless Steel Bottle"	0
"Malta"	" Women's Fleece Hoodie Black"	0
``` 




## **Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:
```sql 
-- update all_sessions_clean3.visitid to integer from varchar to perform join on visitid
ALTER TABLE all_sessions_clean3
ALTER COLUMN visitid TYPE int
USING visitid::integer;

-- Question 5: Can we summarize the impact of revenue generated from each city/country?**
SELECT country, city, city_rev, total_rev, round(100*(city_rev/total_rev),2) AS impact_percent
FROM
	(SELECT 
		country
		, city
		, city_rev
		,sum(city_rev) OVER () AS total_rev 
	FROM 
	(SELECT country, city, sum(rev) as city_rev
	FROM 
		(SELECT 
			a3.visitid AS anlytics_visitid
			, sessions.visitid AS sessions_visitid
			, sessions.country
			, sessions.city
			, a3.units_sold
			, a3.unit_price_clean
			, a3.units_sold*a3.unit_price_clean AS rev
		FROM analytics_clean3 AS a3
		JOIN all_sessions_clean3 AS sessions
		ON a3.visitid = sessions.visitid
		WHERE units_sold IS NOT NULL) AS subq1
	GROUP BY city, country
	ORDER BY country, sum(rev) DESC, city ) AS subq2
	 ) AS subq3
ORDER BY impact_percent DESC, country, city
```	



Answer:
```
"United States"		3401.51	10119.51	33.61
"United States"	"Mountain View"	1523.05	10119.51	15.05
"United States"	"Chicago"	1196.79	10119.51	11.83
"United States"	"Sunnyvale"	672.13	10119.51	6.64
"United States"	"San Jose"	616.00	10119.51	6.09
"United States"	"New York"	396.95	10119.51	3.92
"Sweden"		336.99	10119.51	3.33
"Canada"		316.96	10119.51	3.13
"United States"	"Palo Alto"	278.00	10119.51	2.75
"United Kingdom"	"London"	249.00	10119.51	2.46
"United States"	"San Francisco"	245.32	10119.51	2.42
"United States"	"San Bruno"	217.47	10119.51	2.15
"Ireland"	"Dublin"	99.99	10119.51	0.99
"Maldives"		99.99	10119.51	0.99
"Egypt"		76.44	10119.51	0.76
"Israel"	"Tel Aviv-Yafo"	58.61	10119.51	0.58
"United States"	"Seattle"	55.99	10119.51	0.55
"United States"	"Ann Arbor"	35.98	10119.51	0.36
"Netherlands"		29.99	10119.51	0.30
"India"		28.97	10119.51	0.29
"Belgium"		24.99	10119.51	0.25
"Denmark"		24.99	10119.51	0.25
"Hong Kong"	"Hong Kong"	18.99	10119.51	0.19
"Mexico"		18.99	10119.51	0.19
"Vietnam"		16.99	10119.51	0.17
"Austria"		12.99	10119.51	0.13
"Germany"	"Berlin"	12.99	10119.51	0.13
"Switzerland"	"Zurich"	12.99	10119.51	0.13
"Taiwan"		12.99	10119.51	0.13
"Germany"	"Munich"	10.99	10119.51	0.11
"United States"	"Austin"	10.99	10119.51	0.11
"United States"	"Detroit"	2.99	10119.51	0.03
"Japan"		1.50	10119.51	0.01
```





