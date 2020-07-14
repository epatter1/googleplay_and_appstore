# Profitable App Profiles for the App Store and Google Play Markets
[View here!](https://nbviewer.jupyter.org/github/epatter1/googleplay_and_appstore/blob/master/Profitable%20App%20Profiles%20for%20the%20App%20Store%20and%20Google%20Play%20Markets.ipynb)

In this project, I act as if I'm a data analyst for a company that builds Android and iOS mobile apps on Google Play and the App Store.

> ### Goal: To analyze data to help our developers understand what type of apps are likely to attract more users.

For the purposes of this analysis, I decided that I only wanted to build apps that are free to download and install, and my main source of revenue consists of in-app ads. This means my company's revenue for any given app is mostly influenced by the number of users who use our app — the more users that see and engage with the ads, the better.

* Performed a brief exploration of the data
* Detect inaccurate data: corrected or removed it.
* Detect duplicate data, and remove the duplicates for Google Play. 
  * No need to do this for the App Store as there are no duplicates at the time of my analysis.
* Remove non-English apps like 爱奇艺PPS -《欢乐颂2》电视剧热播.
  * To minimize data loss, I only remove an app if its name has more than three characters with corresponding numbers falling outside the ASCII range. This isn't the most ideal way, but effective enough for my purposes here.
* Remove apps that aren't free.
* Being that in-app ads are the main source of revenue and my data sets contain both free and non-free apps, I isolated only the free apps for this analysis.

Again, my company's revenue is highly influenced by the number of people using our apps so I need to determine the kinds of apps that are likely to attract more users. 
And because the goal is to add the app on both Google Play and the App Store, I needed to find app profiles that are successful on *both* markets.
### Here is my validation strategy:
* Build a minimal Android version of the app and add it to Google Play.
* If the app has a good response from users, I develop it further.
* If the app is profitable after six months, I build an iOS version of the app and add it to the App Store

I start by building frequency tables to find the most common genres for each market and go from there. Chose the ***prime_genre*** column from the App Store data set, and for the ***Genres*** and ***Category*** columns from the Google Play data set.

Decided to build two functions, ***freq_table*** and ***display_table*** I can use to analyze the frequency tables
* One function to generate frequency tables that show percentages.
* Another function I can use to display the percentages in a descending order.

  ### Pitstop!
  *Things I had to consider*:
  * Dictionaries don't have order, and it will be very difficult to analyze the frequency tables. Hence I decided to build the second function which can help display the entries in the frequency table in a descending order.
  * I made use of the built-in ***sorted()*** function. This function takes in an iterable data type (like a list, dictionary, tuple, etc.), and returns a list of the elements of that iterable sorted in ascending or descending order.

  * But the ***sorted()*** function doesn't work too well with dictionaries because it only considers and returns the dictionary keys.
  [image1]

  * However, the ***sorted()*** function does work well if I transform the dictionary into a list of tuples, where each tuple contains a dictionary key along with its corresponding dictionary value. To ensure the sorting works right, the dictionary value comes first, and the dictionary key comes second:
  [image2]

The data set only contains free English apps, I  you should be careful not to extend your conclusions beyond that scope So if I found that gaming apps are the most numerous among the free English apps on Google Play, it doesn't mean I should expect to see the same pattern on Google Play as a whole. 
The frequency tables made it clear that the App Store is dominated by apps designed for ***fun***, while Google Play shows a more balanced landscape of both ***practical*** and ***fun*** apps.

At this point, I wanted to get an idea about the kind of apps with the most users. Decided to calculate the average number of user ratings per app genre on the App Store. 
To do that, I:
* Isolated the apps of each genre.
* Summed up the user ratings for the apps of that genre.
* Divided the sum by the number of apps belonging to that genre (not by the total number of apps).

Now that I have data about the number of installs for the Google Play market, you'd think I'd be able to get a clearer picture about genre popularity. However, the install numbers don't seem precise enough. For instance, I don't know whether an app with 100,000+ installs has 100,000 installs, 200,000, 350,000, and so on. However, I don't need very precise data for my purposes here — only which app genres attract the most users without the need for perfect precision with respect to the number of users.

So I left the numbers as they are, which means that I'll consider that an app with 100,000+ installs actually has 100,000 installs, an app with 1,000,000+ installs has 1,000,000 installs, and so on. To perform computations, however, I needed to convert each install number from string to float. This means I needed to remove the commas (,) and the plus (+) characters, otherwise the conversion won't raise an error.

## Conclusion
I finished this portion of my analysis by recommending that taking a popular book (perhaps a more recent book) and turning it into an app could be profitable for both the Google Play and the App Store markets. The markets are already full of libraries, so I need to add some special features besides the raw version of the book which could include:

* Daily quotes from the book
* An audio version of the book
* Quizzes on the book
* A forum where people can discuss the book, etc.
