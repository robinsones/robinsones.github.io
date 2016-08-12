### The Bright Blue Horror

Coming into Metis, I knew one of the hardest parts would be switching from R to Python. Beyond simply having much more experience in R, I had come to rely on Hadley Wickham's great set of R packages for data science. One of these is ggplot2, a data visualization package. While there is a version of [ggplot2 for python](http://ggplot.yhathq.com), I decided to learn the main plotting system in Python, matplotlib. Then I actually created and saw my first matplotlib graph:

<p align="center">
  <img src="https://github.com/robinsones/robinsones.github.io/blob/draft-post-3/images/blog_post_ugly_plot.png" alt="Matplotlib Default"/>
</p>

I was **horrified**. I hated the color, the tick marks on all four sides of the plot, the white background. I promptly sent my brother the following texts: 

<p align="center">
  <img src="https://github.com/robinsones/robinsones.github.io/blob/draft-post-3/images/Dave-test.png" alt="Text"/>
</p>

Fortunately, he wrote back quickly suggesting I try seaborn, and my boot camp experience was saved. Six weeks later, I've become known in my Metis cohort as a seaborn evangelist. On presentation days at Metis, not a plot goes by without me marking down if it has base matplotlib aesthetics. I then follow up with the presenters afterwards, asking them why they don't use seaborn. Usually this is followed by, “Is it to make me sad?" 

These strong opinions on plotting actually follow a family tradition. Back in February, my brother David Robinson, a data scientist at Stack Overflow, became part of a flare-up in a long-running debate on ggplot2 versus base R graphics. 

### The Great ggplot2 Versus Base R War

<p align="center">
  <img src="https://github.com/robinsones/robinsones.github.io/blob/draft-post-3/images/joker_pic.png" alt="Joker Picture"/>
</p>

Back in February, Jeff Leek, an Associate Professor of Biostatistics and Oncology at John Hopkins and co-director of the popular John Hopkins specialization in data science on cousera, made a blog post entitled ["Why I don't use ggplot2"](http://simplystatistics.org/2016/02/11/why-i-dont-use-ggplot2/). The post wasn't even out two days before David, one of the people Jeff Leek had called out for giving him grief about not using ggplot2, followed up with a post of his own on [why he uses ggplot2]((http://varianceexplained.org/r/why-I-use-ggplot2/). Another data scientist, Nathan Yau, joined in a month later with an [extensive post](https://flowingdata.com/2016/03/22/comparing-ggplot2-and-r-base-graphics/) comparing ggplot2 and R base graphics for a variety of plots. Ben Casselman of FiveThirtyEight joined the fray in a ["tweetstorm"](https://twitter.com/bencasselman/status/712405057388601344). It settled down after that, but still simmers under the surface, bubbling up in places like the Joint Statistical Meetings this month, where Jeff Leek used the above image in his presentation. 

I bring this up not only to illustrate some family resemblance, but also to set up a contrast to seaborn versus matplotlib. While Base R graphics and ggplot2 require completely different syntax, seaborn is *based on* matplotlib, and so starting to use seaborn is as easy as importing it. 

### The Advantages of Seaborn

[Seaborn](https://stanford.edu/~mwaskom/software/seaborn/) is a data visualization library in Python based on matplotlib. The seaborn website has some great documentation, including a [tutorial](https://stanford.edu/~mwaskom/software/seaborn/tutorial.html). And like the rest of your programming questions, anything you can't find on that website can generally be found on the Stack Overflow page that is your first google result. 

To get started with seaborn, you're going to need to install it in the terminal with either `pip install seaborn` or `conda install seaborn`. Then at the top of your python file, simply run `import seaborn as sns`.

#### Better Default Aesthetics

One of the biggest advantages of seaborn is that its default aesthetics are much more visually appealing than matplotlib. If I import seaborn at the top of my python file and re-run the same exact commands that generated this post's earlier plot, I now get this: 

<p align="center">
  <img src="https://github.com/robinsones/robinsones.github.io/blob/draft-post-3/images/blog_post_pretty_plot.png" alt="Nice Plot"/>
</p>

That's right: you can run **the exact same code** you've already written and get prettier plots, no extra code or new syntax required. Recently I was horrified when a more senior data scientist, and much better Python programmer, presented with default matplotlib aesthetics. When I asked him why he didn't use seaborn, he said "It's on my list of things to learn, I just haven't gotten around to it."
But this isn't a valid excuse! All you need to do to start benefitting from seaborn is import it. There is a lot more functionality you can add that, but just this already ofers an exponential improvement. 

#### Easily Customizable Aesthetics

If you want to change either the background or the colors of all your graphs, you can do so easily with two commands: `sns.set_style` and `sns.set_palette`. 

- `sns.set_style` takes one of five arguments: `white`, `dark`, `whitegrid`, `darkgrid`, and `ticks`. These are the five options for the background of your plot; the default one is darkgrid. Play around and see what you like best!

- `sns.set_palette` will change the color palette. Use `sns.palplot` to print out a set of colors before you change your default colors to them. For example, try `sns.palplot(sns.light_palette("green"))`. If you decide you like those colors, run `sns.set_palette(sns.light_palette("green"))` to change your graphs. Check out a great set of possible color palettes [here](https://stanford.edu/~mwaskom/software/seaborn/tutorial/color_palettes.html). This page also gives a great tip on how you can divide color palettes into three different categories, and which one is appropriate for which type of data: 
  - **Qualitative color palettes**, where you want to distinguish between distinct data that doesn't have an ordering. These color palettes are just a variety of different colors. 
<p align="center">
<img src="https://github.com/robinsones/robinsones.github.io/blob/draft-post-3/images/qualitative_color_palette.png" alt="Qualitative Color"/>
</p>
  - **Sequential color palettes**, where your data range goes from relatively uninteresting or low values to relatively interesting of high values. These color palettes go from light to dark or dark to light in one color or similar colors. 
<p align="center">
<img src="https://github.com/robinsones/robinsones.github.io/blob/draft-post-3/images/sequential_color_palette.png" alt="Sequential Color"/>
</p>
  - **Diverging color palettes**, where the interesting points are on either end and you want to under-emphasize the middle points. These color palettes are dark at the end and light in the middle, with a different color for each side. 
<p align="center">
<img src="https://github.com/robinsones/robinsones.github.io/blob/draft-post-3/images/divergent_color_palette.png" alt="Divergent Color"/>
</p>

#### Seaborn-Specific Plots 

The other great advantage of seaborn is that seaborn has some built-in plots that matplotlib does not. Most of these can be done by hacking away at matplotlib, but they're not built in and require much more code. These include [facet plots](https://stanford.edu/~mwaskom/software/seaborn/generated/seaborn.FacetGrid.html) and [regression plots](https://stanford.edu/~mwaskom/software/seaborn/generated/seaborn.regplot.html). 

What I love about seaborn is that making plots generally match your intuition for what the syntax would be. For example, to make a barchart with confidence intervals, you can make a bar chart using the tips dataset from seaborn (`tips = sns.load_dataset("tips")`):
```
barplot = sns.barplot(x = "day", y = "total_bill", data = tips, order = ["Thur", "Fri", "Sat", "Sun"])
barplot.set(xlabel = "Day", ylabel = "Average Total Bill", title = "Total Bill by Day")
```

<p align="center">
<img src="https://github.com/robinsones/robinsones.github.io/blob/draft-post-3/images/pretty_bar_chart.png" alt="Sequential Color"/>
</p>

Meanwhile, in matplotlib you actually have to create a new dataset with your means (and standard deviations if you want confidence intervals). Matplotlib also won't accept categorical variables as the variable for the x-axis, so you have to first make the bar chart with numbers as the x-axis, then change the tick-marks on the x-axis back to your original categories. Here's the code for doing it in matplotlib, which doesn't even include re-ordering the x-axis:

```
total_bill_by_day = tips.groupby("day").mean()
plt.bar([1, 2, 3, 4], total_bill_by_day["total_bill"], align = "center")
plt.xticks([1, 2, 3, 4], total_bill_by_day.index)
plt.xlabel("Day")
plt.ylabel("Average Total Bill")
plt.title("Total Bill by Day")
```

<p align="center">
<img src="https://github.com/robinsones/robinsones.github.io/blob/draft-post-3/images/ugly_bar_chart.png" alt="Sequential Color"/>
</p>

This is far from an unusual case. While seaborn certainly does not have it's own plots for everything, it has a lot of the ones you'd typically use for exploratory purposes. 

### Final Verdict

I think every python programmer can benefit from using seaborn for visualizations. The advantage of matplotlib is that you can do essentially anything you want with it by building a plot piece-by-piece. Seaborn doesn't take away any of that, but rather adds some nice default aesthetics and built-in plots that complement the complicated matplotlib code you may already be writing. 

As someone who started off using seaborn right away and has been using it for less than two months, I'm far from an expert on seaborn or matplotlib. But I hoped this post would be helpful for new Python users or reluctant seaborn adapters for the great advantages I see in Seaborn. 


