## Nashville Housing- A Data Cleaning Project in SQL


### Introduction
My aim for this project is to clean and make the dataset ready for analysis. Real world data are often messy data and insights drawn from a messy or questionable data can lead to poor business decisions.  This singular action can draw a business down the wrong path, and it can also reduce business productivity. Safe to say that insights from any data are only as good as the quality of the data, no wonder research have shown that about 80% of an analyst’s time goes to data cleansing and preparation. Data cleaning is performed between data collection and the data analyses.





### Problem description
What exactly do you look out for in a data? Some of the common tasks to do when you get a data include but not limited to:

•	Remove irrelevant data

•	Remove duplicate data

•	Fix structural errors

•	Do type conversion

•	Handle missing data

•	Deal with outliers

•	Standardize/Normalize data

•	Validate data





### Data
The dataset used for this Data Cleaning project is a 19 column table for Nashville and it can be found [[here](https://github.com/Tolulope-Akinmoju/NashvilleHousing-Data-clean-in-SQL/blob/main/Nashville%20Housing%20Data%20for%20Data%20Cleaning.xlsx)] 




### Analyses

I started out by checking to get an overview of the data

![image](https://user-images.githubusercontent.com/114532273/211410268-076e6388-fc90-49c8-b9ce-020e21a832c4.png)

 

![image](https://user-images.githubusercontent.com/114532273/211410314-4ebe3e42-6523-4a5f-8ed2-805b2a650541.png)



**My first task was to standardize the ‘SaleDate’ column.** The current format is in YYYY-MM-DD HH:MM:SS but since the value of HH:MM:SS are all zeros in the original data, I thought it will be okay to remove the HH:MM:SS. To do this I used the **CONVERT** statement

 ![image](https://user-images.githubusercontent.com/114532273/211410509-f6570ea8-e176-4578-8c78-9734cafd33ba.png)

![image](https://user-images.githubusercontent.com/114532273/211410543-dd23aeef-06d7-4ee7-9f96-999f758ae8e4.png)

 


**Another structural error I thought to fix was to change Y and N to YES and NO in "Sold as Vacant" column.** The initial column shows four different categorical values (Y, N, Yes, No) instead of two categories.

![image](https://user-images.githubusercontent.com/114532273/211410571-0c350bde-b44b-482e-9e42-f0115705e787.png)

 
![image](https://user-images.githubusercontent.com/114532273/211410641-5f8a2e6b-9a4d-4a3e-9a4d-6663ae33accd.png)

 

To format this to give just two categories, The conditional statement **CASE** was used.
 
![image](https://user-images.githubusercontent.com/114532273/211410678-b42dc7fb-1038-463f-8560-98a360fbc12a.png)

 
![image](https://user-images.githubusercontent.com/114532273/211410750-3b46d765-5184-4938-adf6-4629865305df.png)








**Next task was to populate the missing PropertyAddress data**
 
![image](https://user-images.githubusercontent.com/114532273/211410797-61fc8d8e-893f-494a-82ae-f929498cdaee.png)

![image](https://user-images.githubusercontent.com/114532273/211410822-d20c7174-4170-443b-9cb7-bf7900c457b4.png)

 


From the output above we can see that the PropertyAddress column has a lot of null values.

If we take a closer look the ParcelID column (ParcelID 44/45, 61/62), we will realize that when the ParcelID are the same, the PropertyAddress are also the same. It is safe to use the ParcelID as a reference for populating the missing value in the PropertyAddress column as shown below.

 
![image](https://user-images.githubusercontent.com/114532273/211410919-0a66f258-1f96-4f7c-b7b7-84a831364dae.png)

 
![image](https://user-images.githubusercontent.com/114532273/211410940-9a6e09ca-86a4-435c-ad1c-9e7f9322a780.png)


To do this, the query below was used to populate the missing PropertyAddress using a **SELFJOIN** on the table such that If a.ParcelID = b.ParcelID, then populate missing a.PropertyAddress to be = b.PropertyAddress provided a.UniqueID <>b.UniqueID.
 

 ![image](https://user-images.githubusercontent.com/114532273/211410993-2065dfb9-007e-4ad9-a726-813b3397a1ab.png)


![image](https://user-images.githubusercontent.com/114532273/211411030-854f8ac7-2666-4ef7-bb7d-329e65241e24.png)

It works, rows 8 and 9 shows the update was successful.

Then I updated the PropertyAddress with the query below
 
![image](https://user-images.githubusercontent.com/114532273/211411057-28b028c8-02a2-4de3-9859-c213353d0e83.png)




From the last task I saw that the PropertyAddress isn’t formatted correctly, **I decided to parse the long-formatted by breaking it down into individual column Address, City**. To do this, I split the PropertyAddress such that a column has the address while the other has the city.

 

![image](https://user-images.githubusercontent.com/114532273/211411111-8adcbf34-fec9-4648-8339-5dc03765d9ac.png)


  ![image](https://user-images.githubusercontent.com/114532273/211411142-7158b386-454a-4394-9516-c12ac4ff25e2.png)


 ![image](https://user-images.githubusercontent.com/114532273/211411184-0bced50b-cbcc-4929-8f60-ae496a3105b1.png)


 ![image](https://user-images.githubusercontent.com/114532273/211411208-184f83ce-f26b-4f69-80ed-1f23f24eed97.png)

 



In the same vein, I decided to fix the **OwnerAddress** as it was formatted to include Address, City and State in a single Column. I opted to split entire address to contain individual columns.
 
![image](https://user-images.githubusercontent.com/114532273/211411319-51891cd5-a6c1-4432-ba65-0e0a12c502dd.png)

![image](https://user-images.githubusercontent.com/114532273/211411345-e62fce55-2f0e-440b-9823-42d9d9c7fd16.png)


![image](https://user-images.githubusercontent.com/114532273/211411363-76816ca1-3918-4bdc-88d0-a04fd6a508a6.png)

![image](https://user-images.githubusercontent.com/114532273/211411406-68229fbe-620a-4a47-a6eb-0123ccd90baa.png)







**I also wanted to remove duplicate rows from my table and to do this I will use CTE and window ranking function Row_Number().**

 
 ![image](https://user-images.githubusercontent.com/114532273/211411449-a74ee8c8-aa8f-437c-9555-443a22768302.png)

![image](https://user-images.githubusercontent.com/114532273/211411477-c1359ab0-b3aa-476f-8599-dece3cef7c2f.png)




 


The last column on the output table shows the duplicate rows, now to do the actual delete from the table, I used the query below.
 
![image](https://user-images.githubusercontent.com/114532273/211411506-ecd526d8-2e03-4f3d-b291-e5b34090ebd1.png)





**Finally, I removed the unused column from the table using the DROP statement.** I did this manly because I had created a better format for the columns during my analysis and as such, I have no need for them.
 
![image](https://user-images.githubusercontent.com/114532273/211411575-fac7fbf7-3745-4628-98c7-b2c31733e3ae.png)



**Please note that it is not a good practice to delete columns from the table especially if you are working with raw data from the database.**  If you must do this, please create a backup of your original data because once it is deleted, the data is gone.

And it’s a wrap. The dataset is cleaned and set for further analysis.



### Recap
In this project I standardized date format, fixed structural errors, populated missing values, split long-formatted address column, removed duplicates, and lastly deleted unused columns.

All my codes are linked here in my [[github](https://github.com/Tolulope-Akinmoju/NashvilleHousing-Data-clean-in-SQL/blob/main/Data%20Cleaning%20In%20SQL.sql)].

Thank you for following me thus far and I hope it was a good read. Please do well to follow my data progress [[here](https://tolulope-akinmoju.github.io/)] and you can also connect with me on [[LinkedIn](https://www.linkedin.com/in/tolulope-akinmoju)]


Reference
Guided Project- [[Alex the Analyst](https://www.youtube.com/watch?v=8rO7ztF4NtU&list=PLUaB-1hjhk8H48Pj32z4GZgGWyylqv85f&index=4)]
