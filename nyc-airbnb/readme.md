# NYC Airbnb - Data Analysis Practice

## Question
What affects listing "price" in NYC Airbnb data? This question tested upon: neighbourhood group, room type, number of reviews, minimum nights, availability, and whether these factors combine or work independently.

## Method

* Comparison of categories using groupby() and mean() methods.
* Checking relationships between numeric columns with .corr().
* Checking distribution shape with .describe(), comparing mean vs median to catch outliers.
* Using pivot_table() to compare two categorical factors (neighbourhood group and room type) at the same time, to rule out one factor hiding behind the other.

## Results

1- Manhattan has the highest average price (196.9), followed by Brooklyn (124.4), Staten Island (114.8), Queens (99.5) and Bronx (87.5).

2- Room type has a strong effect on price. Entire home/apt is the most expensive (211.8), then Private room (89.8), then Shared room (70.1).

3- Number of reviews and price are not meaningfully related. Correlation is -0.05, which is close enough to 0 to say there's practically no relationship, even though the direction (cheaper listings get slightly more reviews) matched my initial guess.

4- Minimum nights is right-skewed. Even after capping unrealistic values (minimum nights higher than availability_365 adjusted down to match), mean (5.0) is still much higher than median (1.0), meaning most listings ask for very short minimum stays, but a handful of long-term listings pull the average up.

5- Availability and price are not meaningfully related either. Correlation is 0.08 - again close to 0.

6- Manhattan and Brooklyn have by far the most listings (21661 and 20104), while Bronx and Staten Island barely register (1091 and 373). Manhattan leads but Brooklyn is close behind in listing count, despite the large price gap between them.

7- Both neighbourhood group and room type affect price independently, not just one hiding behind the other. Using pivot_table() to hold room type fixed and compare across regions (and vice versa) showed the same pattern holds every time - e.g. Entire home/apt is more expensive than Shared room in every single region, and Manhattan is more expensive than Bronx for every single room type. So both factors are real, not one explained away by the other.

## Limitations
No cost/host-side data is available, so this only describes pricing patterns from the guest side, not what drives a host's profitability.

## Tools
Python, pandas