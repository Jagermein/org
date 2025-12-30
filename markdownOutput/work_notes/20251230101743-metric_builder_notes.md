
# Table of Contents

1.  [Database Structure](#org841367e)
    1.  [airspace](#org86cff37)
    2.  [events](#orgf557d5c)
    3.  [aircraft](#org814ebd6)



<a id="org841367e"></a>

# Database Structure

The Database structure section will go over what our current DB structure looks like. This will go over the data types, as well as the tables. Within each table, there can be sections/columns/etc. that are called into another, which will will try to highlight here.


<a id="org86cff37"></a>

## airspace

Airspace is exactly what it sounds like. This is the airspace that users have alreayd specified, which can easily be referenced in other fields such as [events](#orgf557d5c). These can have spcifications such as floor, targets, boundaries, etc. Below are the fields we currently care about (subject to change).

-   id [uuid] : unique id for the airspace
-   name [string] : name for the airspace
-   actual<sub>environment</sub> [string] : this is specifying if the environment is actually over land or sea. we say actual because they can simulate something different.
-   targets[{{}}] : an object of objects that specify the name, location of targets that are in the airspace. this is usually specified for stationary targets that persist in the airspace/range.


<a id="orgf557d5c"></a>

## events

Events is where we are storing each event that has occured. An event is what is made in the event page, where users specify the syllabi, location, threat levels, and many other aspects. An event is unique, but it can repeat. This can happen say if an AWF has a refly, or a SQDN wants to practice the same exact event. This also occurs often within virtual and constructive scenarios. It is advised and highly recommended that each event is unique for analysis purposes.

-   id [uuid] : unique id for the event.
-   event [string] : the name the user gave the event
-   time [int] : time of the event, the units are timeSinceEpoch. So ms since 01-01-1970.
-   airspaceId [uuid] : reference id from airspace.
-   airspaceName [string] : reference to the airspace name


<a id="org814ebd6"></a>

## aircraft

here we are now going to test [airspace](#org86cff37) and [events](#orgf557d5c) references.

