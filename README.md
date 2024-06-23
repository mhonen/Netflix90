---
jupyter:
  colab:
    name: Welcome to DataCamp Workspaces.ipynb
  editor: DataLab
  kernelspec:
    display_name: Python 3 (ipykernel)
    language: python
    name: python3
  language_info:
    codemirror_mode:
      name: ipython
      version: 3
    file_extension: .py
    mimetype: text/x-python
    name: python
    nbconvert_exporter: python
    pygments_lexer: ipython3
    version: 3.11.7
  nbformat: 4
  nbformat_minor: 5
---

<div class="cell markdown">

<center><img src="redpopcorn.jpg"></center>

</div>

<div class="cell markdown">

# Description of Project:

This was a project that I had to complete in one of my courses with
Datacamp. It uses the netflix_data.csv data file that was supplied by
the course. The main questions for this project were the following:

<p style="color: blue">1. What was the most frequent length of movies of the 90's between the year 1990 - 1999.</p>
<p style="color: blue">2. There were a few "Action" films during this decade.  How many of these action films were below 90 minutes in length.</p>

## The data

### **netflix_data.csv**

Here is the breakdown of the columns (i.e. variables) that incompassed
the date set:

| Column         | Description                     |
|----------------|---------------------------------|
| `show_id`      | The ID of the show              |
| `type`         | Type of show                    |
| `title`        | Title of the show               |
| `director`     | Director of the show            |
| `cast`         | Cast of the show                |
| `country`      | Country of origin               |
| `date_added`   | Date added to Netflix           |
| `release_year` | Year of Netflix release         |
| `duration`     | Duration of the show in minutes |
| `description`  | Description of the show         |
| `genre`        | Show genre                      |

</div>

<div class="cell markdown">

# 1. Data Exploration

### Note: Data Discovery and data cleaning were not neccessary for this project, since the dataset was already cleaned prior to analyzing.

Import Pandas and Matplotlib and read in dataset (netflix_data.csv)

</div>

<div class="cell code" execution_count="1" executionCancelledAt="null"
executionTime="40" lastExecutedAt="1718980524026"
lastExecutedByKernel="df4007f5-183f-4cc0-871f-35ffe7adab40"
lastScheduledRunId="null"
lastSuccessfullyExecutedCode="# Importing pandas and matplotlib
import pandas as pd
import matplotlib.pyplot as plt

# Read in the Netflix CSV as a DataFrame
netflix_df = pd.read_csv(&quot;netflix_data.csv&quot;)">

``` python
# Importing pandas and matplotlib
import pandas as pd
import matplotlib.pyplot as plt

# Read in the Netflix CSV as a DataFrame
netflix_df = pd.read_csv("netflix_data.csv")
```

</div>

<div class="cell markdown">

## 1.1 Getting some visual and statistics on the data set.

</div>

<div class="cell code" execution_count="17" executionCancelledAt="null"
executionTime="58" lastExecutedAt="1718980524084"
lastExecutedByKernel="df4007f5-183f-4cc0-871f-35ffe7adab40"
lastScheduledRunId="null"
lastSuccessfullyExecutedCode="# Start coding here! Use as many cells as you like
netflix_df.head(100)"
outputsMetadata="{&quot;0&quot;:{&quot;height&quot;:324,&quot;type&quot;:&quot;dataFrame&quot;}}">

``` python
# Get a feel for the data and what it contains
netflix_df.head(10)
```

<div class="output execute_result" execution_count="17">

      show_id     type  title           director  \
    0      s2    Movie   7:19  Jorge Michel Grau   
    1      s3    Movie  23:59       Gilbert Chan   
    2      s4    Movie      9        Shane Acker   
    3      s5    Movie     21     Robert Luketic   
    4      s6  TV Show     46        Serdar Akar   
    5      s7    Movie    122    Yasir Al Yasiri   
    6      s8    Movie    187     Kevin Reynolds   
    7      s9    Movie    706      Shravan Kumar   
    8     s10    Movie   1920       Vikram Bhatt   
    9     s11    Movie   1922       Zak Hilditch   

                                                    cast        country  \
    0  Demián Bichir, Héctor Bonilla, Oscar Serrano, ...         Mexico   
    1  Tedd Chan, Stella Chung, Henley Hii, Lawrence ...      Singapore   
    2  Elijah Wood, John C. Reilly, Jennifer Connelly...  United States   
    3  Jim Sturgess, Kevin Spacey, Kate Bosworth, Aar...  United States   
    4  Erdal Beşikçioğlu, Yasemin Allen, Melis Birkan...         Turkey   
    5  Amina Khalil, Ahmed Dawood, Tarek Lotfy, Ahmed...          Egypt   
    6  Samuel L. Jackson, John Heard, Kelly Rowan, Cl...  United States   
    7  Divya Dutta, Atul Kulkarni, Mohan Agashe, Anup...          India   
    8  Rajneesh Duggal, Adah Sharma, Indraneil Sengup...          India   
    9  Thomas Jane, Molly Parker, Dylan Schmid, Kaitl...  United States   

              date_added  release_year  duration  \
    0  December 23, 2016          2016        93   
    1  December 20, 2018          2011        78   
    2  November 16, 2017          2009        80   
    3    January 1, 2020          2008       123   
    4       July 1, 2017          2016         1   
    5       June 1, 2020          2019        95   
    6   November 1, 2019          1997       119   
    7      April 1, 2019          2019       118   
    8  December 15, 2017          2008       143   
    9   October 20, 2017          2017       103   

                                             description             genre  
    0  After a devastating earthquake hits Mexico Cit...            Dramas  
    1  When an army recruit is found dead, his fellow...     Horror Movies  
    2  In a postapocalyptic world, rag-doll robots hi...            Action  
    3  A brilliant group of students become card-coun...            Dramas  
    4  A genetics professor experiments with a treatm...  International TV  
    5  After an awful accident, a couple admitted to ...     Horror Movies  
    6  After one of his high school students attacks ...            Dramas  
    7  When a doctor goes missing, his psychiatrist w...     Horror Movies  
    8  An architect and his wife move into a castle t...     Horror Movies  
    9  A farmer pens a confession admitting to his wi...            Dramas  

</div>

</div>

<div class="cell code" execution_count="19" executionCancelledAt="null"
executionTime="62" lastExecutedAt="1718980524146"
lastExecutedByKernel="df4007f5-183f-4cc0-871f-35ffe7adab40"
lastScheduledRunId="null"
lastSuccessfullyExecutedCode="# First take a look to see if there are any NULLS
netflix_df.info()"
outputsMetadata="{&quot;0&quot;:{&quot;height&quot;:397,&quot;type&quot;:&quot;stream&quot;}}"
scrolled="true">

``` python
# First take a look to see if there are any NULLS
netflix_df.info()
```

<div class="output stream stdout">

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 4812 entries, 0 to 4811
    Data columns (total 11 columns):
     #   Column        Non-Null Count  Dtype 
    ---  ------        --------------  ----- 
     0   show_id       4812 non-null   object
     1   type          4812 non-null   object
     2   title         4812 non-null   object
     3   director      4812 non-null   object
     4   cast          4812 non-null   object
     5   country       4812 non-null   object
     6   date_added    4812 non-null   object
     7   release_year  4812 non-null   int64 
     8   duration      4812 non-null   int64 
     9   description   4812 non-null   object
     10  genre         4812 non-null   object
    dtypes: int64(2), object(9)
    memory usage: 413.7+ KB

</div>

</div>

<div class="cell markdown">

## 2. Data Manipulation to help answer Original Questions

### 2.1 Creating a new dataframe to hold the correct columns

Using the column/variable "release_year" to get data from the years
1990 - 1999.

</div>

<div class="cell code" execution_count="8" executionCancelledAt="null"
executionTime="82" lastExecutedAt="1718980524228"
lastExecutedByKernel="df4007f5-183f-4cc0-871f-35ffe7adab40"
lastScheduledRunId="null"
lastSuccessfullyExecutedCode="# Create a new df that is a sub-set of the original only with data from 1990 - 1999
new_net_df = netflix_df[(netflix_df.release_year &gt;= 1990) &amp; (netflix_df.release_year &lt;= 1999)]
new_net_df"
outputsMetadata="{&quot;0&quot;:{&quot;height&quot;:324,&quot;type&quot;:&quot;dataFrame&quot;}}">

``` python
# Create a new df that is a sub-set of the original only with data from 1990 - 1999
new_net_df = netflix_df[(netflix_df.release_year >= 1990) & (netflix_df.release_year <= 1999)]
new_net_df
```

<div class="output execute_result" execution_count="8">

         show_id   type                            title            director  \
    6         s8  Movie                              187      Kevin Reynolds   
    118     s167  Movie                A Dangerous Woman  Stephen Gyllenhaal   
    145     s211  Movie           A Night at the Roxbury    John Fortenberry   
    167     s239  Movie  A Thin Line Between Love & Hate     Martin Lawrence   
    194     s274  Movie                     Aashik Awara         Umesh Mehra   
    ...      ...    ...                              ...                 ...   
    4672   s7536  Movie                      West Beirut        Ziad Doueiri   
    4689   s7571  Movie      What's Eating Gilbert Grape     Lasse Hallström   
    4718   s7624  Movie                   Wild Wild West    Barry Sonnenfeld   
    4746   s7682  Movie                       Wyatt Earp     Lawrence Kasdan   
    4756   s7695  Movie                      Yaar Gaddar         Umesh Mehra   

                                                       cast        country  \
    6     Samuel L. Jackson, John Heard, Kelly Rowan, Cl...  United States   
    118   Debra Winger, Barbara Hershey, Gabriel Byrne, ...  United States   
    145   Will Ferrell, Chris Kattan, Dan Hedaya, Molly ...  United States   
    167   Martin Lawrence, Lynn Whitfield, Regina King, ...  United States   
    194   Saif Ali Khan, Mamta Kulkarni, Mohnish Bahl, S...          India   
    ...                                                 ...            ...   
    4672  Rami Doueiri, Mohamad Chamas, Rola Al Amin, Ca...         France   
    4689  Johnny Depp, Leonardo DiCaprio, Juliette Lewis...  United States   
    4718  Will Smith, Kevin Kline, Kenneth Branagh, Salm...  United States   
    4746  Kevin Costner, Dennis Quaid, Gene Hackman, Dav...  United States   
    4756  Mithun Chakraborty, Saif Ali Khan, Somy Ali, P...          India   

                date_added  release_year  duration  \
    6     November 1, 2019          1997       119   
    118      April 1, 2018          1993       101   
    145   December 1, 2019          1998        82   
    167   December 1, 2020          1996       108   
    194       June 1, 2017          1993       154   
    ...                ...           ...       ...   
    4672  October 19, 2020          1999       106   
    4689   January 1, 2021          1993       118   
    4718   January 1, 2020          1999       106   
    4746   January 1, 2020          1994       191   
    4756      July 1, 2017          1994       148   

                                                description           genre  
    6     After one of his high school students attacks ...          Dramas  
    118   At the center of this engrossing melodrama is ...          Dramas  
    145   After a run-in with Richard Grieco, dimwits Do...        Comedies  
    167   When a philandering club promoter sets out to ...        Comedies  
    194   Raised by a kindly thief, orphaned Jimmy goes ...          Dramas  
    ...                                                 ...             ...  
    4672  Three intrepid teens roam the streets of Beiru...          Dramas  
    4689  In a backwater Iowa town, young Gilbert is tor...  Classic Movies  
    4718  Armed with an ingenious arsenal, two top-notch...          Action  
    4746  Legendary lawman Wyatt Earp is continually at ...          Action  
    4756  When his brother becomes involved in a deadly ...          Dramas  

    [184 rows x 11 columns]

</div>

</div>

<div class="cell markdown">

### 2.2 Drawing a Histogram on the Distribution of Film Length.

This gives a good view of the distribution of film length over a ten
year period. However, we don't really get a perfect idea on what is
exactly the frequency. So, to get the frequency or mode of which film
length was the most dominant. I decided to use the Pandas mode() method
on the extracted data set.

</div>

<div class="cell code" execution_count="16" executionCancelledAt="null"
executionTime="192" lastExecutedAt="1718980524420"
lastExecutedByKernel="df4007f5-183f-4cc0-871f-35ffe7adab40"
lastScheduledRunId="null"
lastSuccessfullyExecutedCode="# Create a histogram to get an idea of the most common movie duration in the 90's.  From graph it looks aroin 104 - 110.  However, this is could be more of a mean than actual median for frequency.

plt.hist(new_net_df['duration'])
plt.show()">

``` python
# Create a histogram to get an idea of the most common movie duration in the 90's.  
# However, It seems that the mode or median could be between 90 - 100 but hard to tell with just this graph.

plt.hist(new_net_df['duration'])
plt.xlabel("Run Time")
plt.ylabel("Number of Films")
plt.title ("Duration Histogram")
plt.show()
```

<div class="output display_data">

![](87b81cf0cc8355ac2f133cf2637e08484fc7f9c7.png)

</div>

</div>

<div class="cell code" execution_count="6" executionCancelledAt="null"
executionTime="52" lastExecutedAt="1718980524472"
lastExecutedByKernel="df4007f5-183f-4cc0-871f-35ffe7adab40"
lastScheduledRunId="null"
lastSuccessfullyExecutedCode="# Used the mode function to see which duration time was more frequent in the data.
duration = new_net_df['duration'].mode()[0]
duration">

``` python
# Used the mode() function to see which duration time was more frequent in the data.
duration = new_net_df['duration'].mode()[0]
duration
```

<div class="output execute_result" execution_count="6">

    94

</div>

</div>

<div class="cell markdown">

## 3. Getting a Count for Action Movies Under 90 Minutes

This final for loop counts how many "Action" movies in the 90's where
under 90 minutes in length.

</div>

<div class="cell code" execution_count="15" executionCancelledAt="null"
executionTime="60" lastExecutedAt="1718980524532"
lastExecutedByKernel="df4007f5-183f-4cc0-871f-35ffe7adab40"
lastScheduledRunId="null"
lastSuccessfullyExecutedCode="# Get the final count of movies that were under the 90 miniute duration time.
short_movie_count = 0
for index, rows in new_net_df.iterrows():
    if rows.genre == 'Action' and rows.duration &lt; 90:
        short_movie_count += 1
        
short_movie_count">

``` python
# Get the final count of movies that were under the 90 miniute duration time.
short_movie_count = 0
for index, rows in new_net_df.iterrows():
    if rows.genre == 'Action' and rows.duration < 90:
        short_movie_count += 1
        
short_movie_count
```

<div class="output execute_result" execution_count="15">

    7

</div>

</div>

<div class="cell markdown">

## 4. Final Answers

<b>1st Question:</b> What was the most dominant length for films in the
90's?

<p style="color: blue"><b>Answer:</b> The most frequent length of films within this decade was 94 minutes.</p>

<b>2nd Question:</b> Among the genre of "Action" films, how many of
those films length was under 90 minutes?

<p style="color:blue"><b>Answer:</b> There were a total of seven (7) films that were under 90 minutes during the 90's.</p>

</div>

<div class="cell code">

``` python
```

</div>
