                          TAKING A CLOSER LOOK AT THE NUMBER OF EVICTION NOTICES FILED IN CA-34TH DISTRICT
![CA_34](https://github.com/dxk613/evictmap/assets/49661961/b189cd1b-627a-435c-8bf1-617ec383b3a1)
Map - https://dxk613.github.io/evictmap/

Dashboard - https://public.tableau.com/app/profile/daniel1600/viz/Eviction_Notices_In_CA_34th_District/Dashboard2?publish=yes

Project's Objective: Examine how many eviction notices were filed within California's Congressional 34th District 
out of 39,677 eviction notices in Los Angeles from February to July 2023. 

To accomplish my goal, I used these three sources: 
1. LA City Controller's Open Data on Eviction Notices - https://evictions.lacontroller.io/ (accessed data on August 28, 2023) 
2. Zip Data Maps - https://www.zipdatamaps.com/politics/national/district/california-34th-congressional-district
3. Final CD Shapefiles (ZIP) - https://wedrawthelines.ca.gov/final-maps/

I started by importing the LA City Controller's Eviction Notices data to SQL. 
The main task of SQL was to match all of the zip codes within LA City Controller's eviction notice table with that of Zip Data Maps. 

Once I imported the eviction notices data, I used SQL to create a new table to include all of 32 zip codes in Zip Data Maps.

![zipcodetable](https://github.com/dxk613/evictmap/assets/49661961/c7d3a5f0-d9a0-429f-ba05-9dc631314f11)

From there, I used the Inner Join function with the zip code columns from both Eviction Notices and Zip Data Maps
to receive the table that contained these following information within CA-34th District:
1. Notice Date
2. Rent Owed
3. Bedroom Count
4. Notice Type
5. Address

![innerjoinfunction](https://github.com/dxk613/evictmap/assets/49661961/fb7f93d7-1412-4c31-b090-0564a60445cc)
* side note: I converted the date format to make things simple

Once I saved my new queried table that contained the zip codes within CA-34th District, I exported the table to
an Excel spreadsheet where I decided to remove the Bedroom Count since there were too many incomplete data
to gain valuable insights.

To check if the adddresses were within CA-34th District's boundary, I used the LA Times Congressional Map 
as a cross-referencing tool with couple of addresses within the Excel spreadsheet.

![LAMap](https://github.com/dxk613/evictmap/assets/49661961/b2afe7c8-9e05-4568-9713-2b5f0915eac8)
https://www.latimes.com/projects/california-congressional-district-map-2021/

After testing couple of the addresses, I observed that there were addresses outside of the
CA-34th District's boundary. Therefore, I used Python on Google Colab to ensure that 
only the addresses within the CA-34th District's boundary remained.

These were my main objectives I wanted to accomplish with Python: 
1. Geocode all of the addresses to gain latitude and longitude for each address
2. Use the newly populated latitudes and longitudes to ensure only the addresses within CA-34th District remained
3. Create an interactive map that displays all of the addresses within CA-34th District boundary

In my first step in geocoding the addresses, I went to Google Cloud Console to sign up my account
and activate my personal API key specifically for geocoding purposes. 

Once I completed that step, I applied the following codes to retrieve my geocoded addresses:
![image](https://github.com/dxk613/evictmap/assets/49661961/074f15d4-5877-4eda-8b85-eaea5b8fe6e4)
![image](https://github.com/dxk613/evictmap/assets/49661961/ed0b067c-a6d0-4632-b6ba-0c3c332e0be6)
![image](https://github.com/dxk613/evictmap/assets/49661961/34a20998-fdfc-464f-8a6c-f9869f3ef504)
![image](https://github.com/dxk613/evictmap/assets/49661961/bcd075c9-c4f4-480d-bc2c-1ea20f2f3d64)
![image](https://github.com/dxk613/evictmap/assets/49661961/be10654c-f143-4cad-b79a-1d700eadb59c)

Once I downloaded the new Excel file with the populated latitudes and longitudes, I used
Google Colab to run the following codes to remove the addresses outside of 
the CA-34th District's border and keep only the ones within the district:  
![image](https://github.com/dxk613/evictmap/assets/49661961/8c5abf3e-5b8b-48ad-bf12-97c7954c1369)
![image](https://github.com/dxk613/evictmap/assets/49661961/ee5e7ee6-5a1d-4c72-b8b0-d5a99f83a9f0)
![image](https://github.com/dxk613/evictmap/assets/49661961/0302251b-4e10-43e1-8af0-a706256bec09)
![image](https://github.com/dxk613/evictmap/assets/49661961/8cc19ccb-0333-4059-a38a-1fe4c23b478e)

After I removed the addresses that were outside of the district's boundary, only 9,084 addresses remained. 
For my final step, I created my map using the following codes:
![image](https://github.com/dxk613/evictmap/assets/49661961/b02d2685-e2f0-4533-ac62-35a10728e7db)
![image](https://github.com/dxk613/evictmap/assets/49661961/baf9b470-e629-4f7d-ace6-0da0eb2ba451)
![image](https://github.com/dxk613/evictmap/assets/49661961/054fc6e1-db70-40c4-92f1-c82f29d6cefe)

Once I downloaded my map into my local computer, I used my Github account to publish my map. 

After that, I used Pivot Table on Excel for the remaining addresses to uncover various
trends with the eviction notice data and publish them on Tableau:

![image](https://github.com/dxk613/evictmap/assets/49661961/06837e8a-811d-407d-b47c-b3102786297a)
![image](https://github.com/dxk613/evictmap/assets/49661961/71337341-b7bd-48bb-abc6-b893b80e71ed)
![image](https://github.com/dxk613/evictmap/assets/49661961/fa2a5e92-071d-4876-8e51-0df9066c5f24)
![image](https://github.com/dxk613/evictmap/assets/49661961/4d191ceb-d941-4d92-9d1e-9e2ff065bf6e)

The end result:
an interactive map and a dashboard














 

