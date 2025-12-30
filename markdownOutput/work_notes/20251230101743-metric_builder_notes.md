
# Table of Contents

1.  [Database Structure](#orga12d705)
    1.  [events](#org05b09d5)



<a id="orga12d705"></a>

# Database Structure

The Database structure section will go over what our current DB structure looks like. This will go over the data types, as well as the tables. Within each table, there can be sections/columns/etc. that are called into another, which will will try to highlight here.


<a id="org05b09d5"></a>

## events

Events is where we are storing each event that has occured. An event is what is made in the event page, where users specify the syllabi, location, threat levels, and many other aspects. An event is unique, but it can repeat. This can happen say if an AWF has a refly, or a SQDN wants to practice the same exact event. This also occurs often within virtual and constructive scenarios. It is advised and highly recommended that each event is unique for analysis purposes.

-   id : uuid | unique id for the event.

