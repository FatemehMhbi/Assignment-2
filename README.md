# Amyris_take_home_assignment
How to pick strains with improvement over the parent strains for the next round of screening (HTS)?
The dataset for this assignment includes the screening values from three different robots (explained in README.pdf file). The goal is to pick a specified number (20, 60, and 120) of strains for the next round of screening based on their improvement over the parent strain.

Jupyter notebook file "Take_home_assignemnt.ipynb" includes the calculations, plots and the strains I picked. 

Each step is explaind in the following: 

1- Looking into the relationship between each feature and the screening values (only parent strains) to find out if there is any significant differences between the values different robots are returning. I was thinking maybe the outliers need to be removed from data. But I did not do it since they did not seem to be that important in my final approache in picking the strains. I got three plots in this step: //
- Percentiles boxplot for parent strain values for each robot. In this plot, we can see the robots are returning slightly different values for the same parent strains. I came to the conclusion that the strains' screening values for each robot should be compared to the parent strains' values measured using the same robot. 
- Stacker position vs parent strain mean values for each robot. Based on this plot it is clear that stacker position is an important feature and each position need to be compared to to itself. Based on this plot I came with idea of fitting a linear curve to the datapoint (parent strains' values) for each robot in the last step.
- Parent strian mean values vs plates. This plot shows the same trend as stacker position plot, which makes sense looking at the dataset and the relationship between the stacker positions and the plate number. 
2- Choosing the potential candidates for the next round of screening: 
- Fitting a linear curve to the datapoint (parent strains' values) for each robot. f(x) = a*x + b where x is the stacker position and f(x) is the parent strain's mean value (mean over 4 different parent strains values in the dataset for each plate). 
- Estimate the mean value for each stacker position.
- Calculate the distance between the stains' values and the estimated value. The distance here is defined as the "estimated value at position T - a strain's value at stacker position T".
- Sorting (descending order) the stains based on their distnace value. Then I picked the top 20 strains, top 60 strains and top 120 strains in the list as the strains for the next round of screening. 

