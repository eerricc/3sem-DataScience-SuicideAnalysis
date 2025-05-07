# 3sem - Global Suicide Rates (1984–2016) - Data Science Project
> hi, im Eric! this is a data science project i recently worked on. I used a dataset from Kaggle that tracks global suicide rates from 1984 to 2016. I chose this topic because i felt it could have something meaningful.

> This project is presented in a storytelling style, so you can follow my thought process step by step.

**Project Highlights**  

1) Data Preprocessing – Cleaning and preparing the dataset for analysis  
2) Exploratory Data Analysis – Understanding the data through patterns and trends  
3) Data Visualization – Communicating insights through charts and plots  
4) Conclusions – Summarizing key takeaways and potential implications

---

![image](https://github.com/user-attachments/assets/fa98caad-16b9-4ac0-b8d7-01f54231fd34)

---

## 🔧 Setup  

- first things first, I imported all the libraries I needed

![image](https://github.com/user-attachments/assets/1c8eefb5-b1ac-4162-807a-902c98678a2e)


## 🧹 Data Prep

- i started by using `.head()` to take a quick look at the first few rows just to get a sense of what I’m working with
- then, I used `.info()` to check the data types and spot any missing values or weird formatting
- right away, I noticed the HDI column had issues

![image](https://github.com/user-attachments/assets/ada99dc8-eee4-4a74-8ee6-489afcbf7631)

- turns out the HDI column was mostly empty
- about 70% of it was missing—so I decided to drop it

![image](https://github.com/user-attachments/assets/16f91d2f-cb08-4112-bb7e-9f21c3cf1662)

- i also dropped a few other columns and cleaned up the formatting


## 📊 EDA

### 🚦 correlation matrix
- i started things off with a correlation matrix to check for any obvious relationships between the variables
- i took some quick notes, but a few things really stood out i'll circle back to those a bit later. For now, just take a look at the plot

![image](https://github.com/user-attachments/assets/c2757729-7f50-4a01-b363-2e5086f6130c)

### 🌍 Continent Breakdown
- next, i grouped the countries by continent and plotted the total suicides
- what stood out here is that more developed continents seem to have a much higher suicide number, even though they have very different population sizes
- this made me start questioning the reliability of the dataset

### 📉 Data Distribution
- to dig deeper, I looked at how much data we actually had for each country and the gap is huge
- some countries have tons of data, while others barely show up

![image](https://github.com/user-attachments/assets/c968f634-094f-405d-bbe0-28e0f0914cdb)
> this is just a tiny part, there is a lot more countries but the pic would be too big

### 🗺️ World Map – Total Suicides
- i plotted a world map showing total suicides per country
- it really highlighted the data gaps, especially in Africa and parts of Asia—many of those countries barely had any data at all

![image](https://github.com/user-attachments/assets/c11bcd9f-185f-424d-8186-f39a5a30ab5c)

### ⚠️ Population Bias in Map
- there’s one problem with that first map though: it favors countries with big populations
- for example, France has around 300,000 recorded cases, which is a lot, but on the map, it seems like a mid-range country just because it’s not as big as, say, US or Russia

### 🗺️ World Map – Suicide Rate (Per Population)
- so I made a second map, this time showing suicide rates relative to population
- now the picture changes. France, for instance, shows up as a much more serious case when adjusted for population
- this map gives us a way more accurate view of the situation across countries

![image](https://github.com/user-attachments/assets/01582b1d-8314-434f-8d1c-36d542094ecd)

## 📊 EDA 2 – Deeper Dive into GDP & Suicide Rates

### 💵 GDP vs Suicide Numbers
- earlier, in the correlation matrix, we saw that GDP didn’t have a strong correlation with suicide rates
- but instead of just leaving it at that, i plotted a few graphs to get a better look

![image](https://github.com/user-attachments/assets/2c1a84de-004c-4e88-8936-d6d5025218fb)
> a bit unusual, but it still showed a clear trend: as GDP increases, suicide rates tend to go down

- to explore this further, I split GDP into bins—going from 0 to 120k in jumps of 20k—and grouped the suicide numbers accordingly
- then I calculated the average number of suicides in each bin and plotted a bar graph

![image](https://github.com/user-attachments/assets/f6880441-c2bb-4410-8eac-0f2a06a3680b)

- at first, I expected to see a clean downward trend. But instead, I got this strange pyramid shape—where suicides actually peak in the middle GDP ranges, and then drop off at the higher end
> my guess? This might be because there’s just not enough data from very low-income countries

### 📉 GDP vs Suicide Rate
- next, I did the same thing but looked at suicide rate instead of total numbers

![image](https://github.com/user-attachments/assets/0bd230d1-cfc2-41a1-af73-d721eb1ba9d6)
> starting with a scatter plot, we again see a general downward trend, but it’s messy, with lots of outliers

- so I grouped the data into GDP bins again and plotted the average suicide rate

![image](https://github.com/user-attachments/assets/d7e84690-9fca-48d2-b3e4-8fafb87295b3)

- and here it gets weird again

instead of a clean line, we get this sort of waveform:  

      1.Low rates at the lowest incomes 
      2.Rising toward the middle  
      3.Dipping slightly  
      4.And then rising again at the highest income levels  
      
> One theory I have is that very high-income regions might come with more pressure, expectations, and stress—which could affect suicide risk

### 🧑‍🤝‍🧑 Gender Differences
- of course, these graphs were all separated by gender, and you probably noticed, men have a much higher suicide rate than women

![image](https://github.com/user-attachments/assets/4239be22-0462-420f-bcbc-c161d8673abe)

- we already saw this in the scatter plot, but it really stands out—men had about three times the suicide rate compared to women

![image](https://github.com/user-attachments/assets/2f9ae114-a43d-4924-8ff7-d1868c0629e4)

> made me wonder: has this always been the case?

![image](https://github.com/user-attachments/assets/05e3e198-fb63-4c58-bcaa-870b2658ec12)
> so I looked into it and yes, it has. The gap between male and female suicide rates has been consistent over time

### 📉 A Curious Trend Over Time
- but here’s something interesting: there’s a noticeable peak in the 1990s, followed by a decline into 2016

      im not complaining about the drop—fewer suicides is always a good thing—but from a data perspective, it’s worth looking into
  
- It raises questions about what might have changed globally around those times—policy, awareness, support systems, or reporting methods

### 📈 Shifting Focus: Totals Over Time
- alright, now let’s switch things up and look at the total suicide numbers and rates over the years, rather than separating by gender

- i plotted both the total suicides and suicide rates side by side and while they’re a bit different, they follow the same overall trend

![image](https://github.com/user-attachments/assets/489ea378-3017-4e87-ab4e-7062c5b60e04)
> we still get those strange peaks and that sharp drop in 2016

- so, to better understand what’s going on, i decided to dive into the stats

### 📊 What the Stats Tell Us
- here’s what stood out when I looked at the statistical breakdown:

![image](https://github.com/user-attachments/assets/c176d6e0-09fa-4c0d-b716-ec4914ded9c2)

    1. the median staying close to zero suggests that most countries reported very low suicide numbers
    1. this fits with what we saw earlier—lots of missing data or underreporting from certain regions

    2. the mean, on the other hand, stays between 200 and 400, which is way higher than the median
    2. this gap confirms there are some serious outliers pulling the average up
    
    3. standard deviation is also quite high—starting at around 600, peaking in 1994, and then dropping off
    3. this again points to a few countries reporting extremely high numbers, while most didn’t

- And of course, 2016 shows a clear dip across the board in all measures—total, rate, mean, and deviation

### 📉 Minimum and Maximum Suicide Rates
- now let’s look at the min/max over time:

![image](https://github.com/user-attachments/assets/d7b054bb-b86e-4b39-9ce7-df92f614b776)

    The minimum is zero across all years—which is probably more about missing data than actual zero suicides

    But the maximum is interesting. There’s a huge spike in 1994, and here’s why...

### 📌 The 1994 Peak: What Happened?

- turns out the main contributor was the Russian Federation

![image](https://github.com/user-attachments/assets/201c6563-546f-491a-8e2d-a7e06a4677a3)

- after a quick search, I found that this spike coincides with the collapse of the Soviet Union and the First Chechen War
> that period saw intense political instability, economic collapse, and a lot of social disruption—all of which likely drove suicide rates up

### 🧓 Who Was Affected Most?

- interestingly, the age group hit hardest during this time was 35 to 54 years old

![image](https://github.com/user-attachments/assets/33f37478-51ac-4dfe-8829-340d60d0f469)

- so next up, let’s zoom in on the age breakdown and see what else we can learn

![image](https://github.com/user-attachments/assets/4abfd943-4ad0-462f-8577-d6013b6c9465)

## 🎯 Wrapping It All Up

### So, here’s a quick recap of what we found through this analysis

- One of the biggest takeaways was the major spike in suicides around 1994—and we traced that back to the collapse of the Soviet Union, especially in Russia. After that, overall rates gradually declined
- That said, the sharp drop we saw in 2016 wasn’t really a positive trend—it was mostly due to missing data

---

- Looking at age groups, we found that people aged 34 to 54 consistently had the highest suicide rates. This raises questions about what’s going on during midlife things like job stress, financial pressure, or life satisfaction could be contributing factors

---

- When we dug into the relationship between GDP and suicide, the story got a bit more complex:
- At first, it looked like higher GDP meant lower suicides
- But after grouping countries by income levels, we saw a peak in suicide rates at the medium GDP range, and then a drop off as GDP increased
- Even more interesting, when we looked at suicide rates (instead of raw numbers), the pattern turned into a sort of wave low at the bottom, rising in the middle, dipping, then rising again at the top
- That might suggest different stress factors are at play depending on a country's income level

---

- Breaking it down by gender, we saw a huge gap: men have significantly higher suicide rates than women across nearly every graph we looked at. This points to deeper, gender related mental health issues and social expectations

---

- Lastly, we have to acknowledge the data limitations. A lot of underdeveloped countries had incomplete or missing data, especially in regions like Africa and parts of Asia. That means we should take some of these results with caution they give insight, but they’re definitely not the whole picture











