# The Gang 3 (486 points)
## Writeup Author - h1tok1r11

---

### Task

Can you find out where the OG meetup point is? The flag is in the format n00bz{lat,long} with upto 3 decimal places, rounded. Continue where you left off... Note: Wikipedia can be wrong sometimes ;) Author: NoobMaster

---

### Solution

Go to John Doe's page on X. You'll see a new post:

![](./assets/twitter.png)

So, we need to decrypt AES in GCM mode. Go to cyberchef and choose operation "AES Decrypt" and change mode to GCM:

![](./assets/aes_decrypt.png)

We know ciphertext (**1762841d1888f6b02581990abdf0aaba375c85fd3811a6fb405775fb8d**), GCM Tag (**d5e749da6b02c75cb4c763939632503a**). We need key and  IV to decrypt ciphertext. Let-s try to find another osint challenge about John Doe. Go to n00bzunit3d github. There are writeups for 2022 and 2023 year. 

![](./assets/official_writeups.png)	

There is a task "John Doe" in n00bzctf2022. 

![](./assets/2022.png)

We found a city where John Doe met someone in 2022, hence we know IV (**46.720,33.154**)
 
![](./assets/lat_long.png)

And now let's find the key. There is a task called "John Doe Strikes Again" in n00bzctf2023. 

![](./assets/2023.png)

There is a secret key (**YouCanNeverCatchJohnDoe!**) in task description.

Let's try do decrypt ciphertext.

![](./assets/discord.png)

So, open this link. We find ourselves in a secret discord server **"The Hangout"**. We can see that John Doe is planning to meet with OGs in Bengaluru:

![](./assets/bengaluru.png)
![](./assets/og_meetup.png)

Ok, now we know what to look for (110 feet tall statue in Banguluru). Google and find that there is 108 feet tall Statue of Prosperity in Bengalore in honor of Kempe Gowda that stands in  Kempegowda International Airport. The description of the statue meets the criteria.

![](./assets/statue.png)

Let's try commit "n00bz{13.199,77.707}", but it's not applied.

Remember this note from task description.

> Note: Wikipedia can be wrong sometimes ;)

![](./assets/map.png)

Doing some Google Maps and find real coordinates.

### Flag

```
n00bz{13.199,77.682}
```