# Project03
This is project-03 for lede program.
<br>
Link to the project-03 (https://akiha1224.github.io/Project3/)
<br>
Repository for data and code(https://github.com/AKIHA1224/Project3/tree/main/data)

## Title
Visualizing School Accidents
<br>Recurring School Accidents-Uncovering the Hidden Dangers in Places of Learning

## Aim
The Japan Sport Council has maintained a dataset on school-related accidents since 2005. It includes records of tragic incidents in which children lost their lives or suffered severe disabilities at schools—places meant to be safe learning environments. By analyzing this data, I hoped to identify patterns and consider potential preventive measures to avoid similar accidents in the future.
In 2023, Japan’s public broadcaster NHK conducted a similar data analysis and reported on school accidents using this dataset. Inspired by their work, I decided to conduct my own analysis to see if I could replicate their approach. This project also serves as a reference for conducting similar investigations at my own news organization in the future.

## Findings

1. When classifying the school accidents, approximately 48% of the fatal and disabling incidents occurred during "class hours and recess."
2. Through clustering analysis, I found recurring patterns in accidents involving keywords such as "school lunch," "choking," and "children," as well as "PE class," "heart," and "endurance run."

## Data
These are the sources for my data:

| What I plotted  | Data source |
| ------------- | ------------- |
|School accident data|Japan Sport Council, Disaster Mutual Aid Benefit Web — School Accident Case Search Database|

## Data Collection Process
⚫︎ School Accident Data
I downloaded the dataset from the Japan Sport Council’s Disaster Mutual Aid Benefit Web (School Accident Case Search Database), focusing on cases involving death benefits and disability benefits available as of January 31, 2025. The analysis was conducted based on this data.

## Data Analysis Process

### 1. Downloading Data from the Japan Sport Council

[Japan Sport Council – School Accident Case Search Database](https://www.jpnsport.go.jp/anzen/anzen_school/anzen_school/tabid/822/Default.aspx)
Each accident was categorized into one of five groups based on the context in which it occurred:

* **Commute**
* **Class Hours and Recess**
* **Extracurricular Activities**
* **School Events**
* **Other**

Initial classification was performed using Python. Ambiguous or overlapping cases were manually reviewed and reassigned. The percentage distribution of each category was then calculated.

### 2. Trends in Fatal and Disabling Accidents by Year

The dataset used fiscal years, which were converted to calendar years using Python. Annual totals were aggregated and visualized using [Observable](https://observablehq.com).

### 3. Clustering Analysis for “Class Hours and Recess”

To identify patterns within this category, I focused on text fields such as:

* **Situation at Time of Accident**
* **Type**
* **Condition**
* **Activity (Sport/Event)**

Using [fugashi](https://github.com/polm/fugashi), a morphological analysis tool for Python, I:

* Extracted meaningful nouns and keywords
* Removed stopwords and noise words
* Vectorized the text using **TF-IDF**
* Applied **KMeans clustering** to group similar cases
* Determined the optimal number of clusters using **silhouette scores**

### 4. Network Analysis

From each cluster, I extracted representative keywords and visualized co-occurrence networks:

* Nodes represent keywords
* Edges represent co-occurrence relationships
* Networks were used to explore thematic differences between clusters

### 5. Visualization

**Tools used:** D3.js, Observable, Scrollama

* Created an interactive block chart (1 case = 1 block)
* Integrated scroll-driven storytelling with [Scrollama](https://github.com/russellgoldenberg/scrollama)
* Added supporting visualizations:

  * **Bubble charts** to highlight key terms
  * **Network diagrams** to illustrate co-occurrences

## Skills Gained and Personal Growth
1.One of my goals was to learn D3.js, and I was able to create an interactive web page using this tool. Building a visually engaging and functional presentation marked significant growth for me.

2.By observing the work of my peers, I realized that even without using maps, effective use of scrolling, layout, and background colors could enhance storytelling. This inspired me to pay more attention to design and user experience.

3.I also challenged myself with a new analytical method—clustering. It was my first time trying this technique, and being able to visualize the results was a valuable learning experience.

## Future Work
* One of the main goals of this project was to learn D3.js, but I encountered difficulties in adjusting container sizes and making the visualizations fully responsive. For example, the “one person = one block” SVG chart displayed well in full screen but became overly elongated vertically when the browser window was reduced to less than half width. I was unable to resolve these layout issues completely.

* While the project focused on learning new techniques, I now question whether clustering was the most suitable analytical method. Incorporating additional factors such as school grade level might have led to deeper and more nuanced insights.

* Moving forward, I feel it is essential to complement the data analysis with interviews with experts and stakeholders, in order to better understand the underlying causes of recurring accidents and explore what preventative measures are truly needed.

* Additionally, I see the need for focused analysis on specific types of incidents that are frequently reported—such as swimming pool accidents and heatstroke cases—which may benefit from targeted investigation.
