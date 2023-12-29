# SQL-ISLAND

**Hello friends, I want to show you the solution to the quest.Here you will find screenshots of the execution and the necessary code.**

**1 step. It seems there are a few people living in these villages. How can I see a list of all inhabitants?**

```
 Select * from INHABITANT
```
![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/70e8cca6-e55b-499b-8717-ddfb9069e8bc)

**2 step. Thank you, Edward! Okay, let's see who is friendly on this island...**

```
SELECT * FROM inhabitant WHERE state  = 'friendly'
```

![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/dec0b743-51fc-41f4-81cd-d2ac18aee162)

**3 step. Here is no way around getting a sword for myself. I will now try to find a friendly weaponsmith to forge me one. (Hint: You can combine predicates in the WHERE clause with AND)**

```
SELECT * FROM inhabitant WHERE state  = 'friendly' AND job = 'weaponsmith
```
![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/7541c3bc-d076-4323-970f-446446cc5be1)


**4step. Oh, that does not look good. Maybe other friendly smiths can help you out, e.g. a blacksmith. Try out: job LIKE '%smith' to find all inhabitants whose job ends with 'smith' (% is a wildcard for any number of characters).**


```
SELECT * FROM inhabitant WHERE state  = 'friendly' AND job LIKE  '%smith'
```

![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/25bf2608-1e50-4cf9-b710-1e7e96c03da7)

**5 step. No need to call me stranger! What's my personid? (Hint: In former queries, the * stands for: all columns. Instead of the star, you can also address one or more columns (seperated by a comma) and you will only get the columns you need.)**

```
SELECT personid FROM INHABITANT
WHERE name = 'Stranger'
```
![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/adc9cc4a-d96e-4cbb-b899-5ab9793c5658)

**6 step.I can offer to make you a sword for 150 gold. That's the cheapest you will find! How much gold do you have?**

```
SELECT gold FROM INHABITANT
WHERE name = 'Stranger'
```
![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/2e9ce83c-0db0-4395-8e1d-d188690b13f1)

**7step. Find free stuff**
```
SELECT * FROM ITEM
WHERE owner is NULL
```
![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/a126f649-90ca-4209-904a-b194908007c9)

**8 step.Do you know a trick how to collect all the ownerless items?**
```
UPDATE item
SET owner = 20
WHERE owner is NULL
```
![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/c55de53a-d0a2-4018-b804-47c657b765c9)

**9step. show all stuff then l have**
```
SELECT * FROM ITEM WHERE owner = 20
```
![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/f7e1dc20-906b-4fa2-ac30-ed306adb9442)

**10 step.Find a friendly inhabitant who is either a dealer or a merchant. Maybe they want to buy some of my items. (Hint: When you use both AND and OR, don't forget to put brackets correctly!)**

```
SELECT * FROM INHABITANT WHERE state = 'friendly' 
AND job = 'dealer' OR job = 'merchant'
```

![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/e17c255b-17be-450a-9787-5eab0cf031eb)

**11 step.I'd like to get the ring and the teapot. The rest is nothing but scrap. Please give me the two items. My personid is 15.**

```
Update ITEM
Set owner = 15
WHERE item = 'ring' OR item = 'teapot'
```
![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/2157c78e-214a-4207-9fd3-6c87971aea6a)

**12 step.Unfortunately, that's not enough gold to buy a sword. Seems like I do have to work after all. Maybe it's not a bad idea to change my name from Stranger to my real name before I will apply for a job.**

```
Update INHABITANT 
SET name = 'RADION'
WHERE personid = 20
```
![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/844a8453-af48-4253-81b7-33b999a25d93)

**13 step. Find the richer baker**

```
SELECT * FROM INHABITANT
WHERE job = 'baker'
ORDER BY gold DESC
```
![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/30efd359-a76d-440a-a81f-4bae31045934)

**14 step.find pilot**

```
SELECT * FROM INHABITANT
WHERE  job = 'pilot'
```

![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/8af0bc2d-6c00-42ff-8f14-f8f5251072ef)

**15 step.Thanks for the hint! I can use the join to find out the chief's name of the village Onionville. (Hint: In the column 'chief' in the village table, the personid of the chief is stored)**


```
SELECT inhabitant.name FROM INHABITANT,VILLAGE
WHERE  chief = personid
AND village.name = 'Onionville'
```
![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/c0738e70-877f-496d-81aa-bf1d3a55ad96)

**16 step.Hello RADION, the pilot is held captive by Dirty Dieter in his sister's house. Shall I tell you how many women there are in Onionville? Nah, you can figure it out by yourself! (Hint: Women show up as gender = 'f')**

```
SELECT COUNT(*)  FROM INHABITANT
WHERE gender = 'f'
AND villageid = 3
```

![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/4b0e155d-2204-4a78-89fd-2b99f4b7484e)

**17 step. find this girl**

```
SELECT  name  FROM INHABITANT
WHERE gender = 'f'
AND villageid = 3
```

![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/ae190d31-0cf6-4955-814f-7d285d8a293d)

**18 step. Oh no, baking bread alonecan't solve my problems.continue working and sellinitems though, I could earnmore gold than the worth ofgold inventories of albakers, dealers andmerchants together. How much gold is that?**

```
SELECT SUM(gold) FROM inhabitant WHERE job = 'baker' OR job = 'merchant' OR job = 'dealer'
```
![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/6416eea5-013d-43d7-951c-5fdf521553fb)

**19 step. Very interesting: For some reason, butchers own the most gold. How much gold do different inhabitants have on average, depending on their state (friendly, ...)?**

```
SELECT state, AVG(inhabitant.gold) 
FROM inhabitant
GROUP BY state
```

![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/e375cdf6-506f-4745-b59f-ed6ff5c841c7)

**20 step. Heeeey! Now I'm very angry! What will you do next, RADION?**

```
DELETE FROM 
inhabitant 
WHERE name = 'Dirty Diane'
```

![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/bc9e2171-b3f0-4b4f-b374-90479f86e4a0)

**21 step.Yeah! Now I release the pilot!**

```
UPDATE inhabitant 
set state = 'friendly'
WHERE personid = 8
```
![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/9724db0e-e4ec-49c3-88a2-b850d8a968fc)


![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/68bf2fde-a6b8-40f9-9e30-67b40f3deb63)

**FINAL**

![image](https://github.com/Hordiychuk-Radion/SQL-ISLAND/assets/139583782/904bb26e-1410-4c3b-b86a-081c629ff316)



