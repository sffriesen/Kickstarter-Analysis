# Kickstarting with Excel

## Overview of Project

### Purpose
I am using available Kickstarter data to visualize whether theatre campaigns were successful or not based on their launch dates, and how successful they were depending on their fundraising goals. This project is meant to help playwright Louise see if launch date and funding goal have an effect on the level of success of other campaigns, after her own campaign came close to reaching it's goal.

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date
Using a pivot table to isolate theatre campaigns and organize the campaign outcomes (successful, failed, canceled) into the months that the campaigns were launched, I was able to create the following line graph that visualizes which launch months were more successful than others.

![image](Resources/Theater_Outcomes_vs_Launch.png.png)

Here we can see that the month of May has a sharp increase in successful campaigns, with that petering down to July, before it starts to be around the same as other months. Using this line graph, we can also visually see rough ratios for failed/successful campaigns. While there is a small increase in successful campaigns in October, there is also a sharp increase in failed campaigns. Here, it looks like roughly for every 4 successful campaigns, there were 3 that failed (this can be confirmed using the data in the pivot table, with a 76.9% fail to success ratio in October). Alternatively, while there is also a small spike in failed campaigns in May (where our substantial increase in successful campaigns were), it looks like roughly for every 2 successful campaigns, there was only 1 that failed (again, confirmed from our pivot table with a 46.8% fail to success ratio).

### Analysis of Outcomes Based on Goals
Here I created a table that counted the number of campaigns for plays, based on their funding goals and their outcomes (successful, failed, canceled). To do this, I used a `=countifs()` function with multiple parameters, to filter through the main Kickstarters sheet and just return the number of campaigns that matched the parameters entered. Below is an example of the function and parameters for the number of successful campaigns with a goal of $1,000 to $4,999.

`=COUNTIFS(Kickstarters!$F:$F,"successful", Kickstarters!$D:$D,">=1000", Kickstarters!$D:$D, "<=4999", Kickstarters!$R:$R,"plays")`

I then turned this information into percentages and created the following line graph that represents the percentage of campaigns that were successful, failed, or canceled, within each fundraising goal.

![image](Resources/Theater_Outcomes_vs_Launch.png.png)

Using this graph we can see that the most successful kickstarters had goals between the range of $0-$14,999, as well as $35,000-$44,999. All other fundraising goals had more failures than successes (with the goal between $15,000-$19,999 being split 50%-50%).

### Challenges and Difficulties Encountered
My largest challenge was getting my `=countifs()` formula correct to count the number of campaigns based on goal and outcome. This was especially difficult because it's not as easy to check if it's returning the correct number when you have a larger set of data, i.e. if my formula for the number of successful play campaigns with a goal of less than 1000 returned 135 (instead of 141), it's not as easy or time efficient to double check that by actually counting how many match those parameters in the Kickstarter sheet. Nor is that a realistic approach for much larger datasets. This meant that I had to make sure my formula was written correctly and that the correct parameters were used to ensure I got the correct results.

## Results

#### Outcomes Based on Launch date
Based on the pivot table and line graph I utilized to organize the theatre outcomes based on Launch Date, I would say it is clear that the best time to launch a campaign and have the highest chance of success is in May. Secondly, while there seem to be success spikes in February and October, these also come with increases in failures and increased failure to success ratios that make them not as optimal for success as May. Although February is more promising than October if someone is looking to start in Fall/Winter rather than Spring/Summer.

#### Outcomes Based on Goals
By counting the number of play campaigns based on fundraising goal and outcome, we can see that campaigns with a goals of less than $4,999 or between $35,000 and $44,999 have the highest chance of success. Secondly, we can see that campaigns with goals of $25,000 to $34,999 or higher than $49,999 have the highest chance of failure.

#### Limitations
The most prominent limitation I can see is that we have a small amount of data for campaigns with high fundraising goals. This can cause issues in the analysis as it can skew data. For example, we only have 1 campaign with a goal of $45,000 to $49,000. This campaign failed, so there is a 100% failure rate for campaigns within that range. This may not actually be representative of what would happen if someone else started a campaign with that goal, there may have been other factors that caused that campaign to fail other than it's lofty goal amount, but we just don't have any other campaigns to compare it to.

As mentioned above, another limitation could be that there are other factors that might cause the success or failure of campaigns that is unaccounted for. For example, if a kickstarter for a play is started in a town that has a strong theatre presence, it may be more successful than one in a town with a small community theatre. Or if one is started in a more affluent urban community versus a rural one. If this sort of data is collected, we could incorporate it into our analysis to include matching parameters for what our future playwright matches, but I do believe that there will always be some sort of parameter missed, as there are just too many factors that can affect things.

#### Other Options for Tables and Graphs
For the Outcomes by Launch Date, I think a Clustered Column Bar Graph could be helpful to visualize the failure to success ratios of different months. Similarly, a Stacked Bar Graph could be helpful to see percentages in the Outcomes Based on Goals.
