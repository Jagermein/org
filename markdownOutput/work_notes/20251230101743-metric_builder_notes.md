
# Table of Contents

1.  [Database Structure](#org43dbb74)
    1.  [airspace](#org01f629c)
    2.  [events](#org56831a4)
    3.  [aircraft](#orgf6d9bc0)
    4.  [MarkerType](#orgb71a0cf)

:ID:       8c46f3d3-2b5b-448b-8c1e-9513bdf8f159


<a id="org43dbb74"></a>

# Database Structure

The Database structure section will go over what our current DB structure looks like. This will go over the data types, as well as the tables. Within each table, there can be sections/columns/etc. that are called into another, which will will try to highlight here.


<a id="org01f629c"></a>

## airspace

Airspace is exactly what it sounds like. This is the airspace that users have alreayd specified, which can easily be referenced in other fields such as [events](#org56831a4). These can have spcifications such as floor, targets, boundaries, etc. Below are the fields we currently care about (subject to change).

-   id [uuid] : unique id for the airspace
-   name [string] : name for the airspace
-   actual<sub>environment</sub> [string] : this is specifying if the environment is actually over land or sea. we say actual because they can simulate something different.
-   targets[{{}}] : an object of objects that specify the name, location of targets that are in the airspace. this is usually specified for stationary targets that persist in the airspace/range.


<a id="org56831a4"></a>

## events

Events is where we are storing each event that has occured. An event is what is made in the event page, where users specify the syllabi, location, threat levels, and many other aspects. An event is unique, but it can repeat. This can happen say if an AWF has a refly, or a SQDN wants to practice the same exact event. This also occurs often within virtual and constructive scenarios. It is advised and highly recommended that each event is unique for analysis purposes.

-   id [uuid] : unique id for the event.
-   event [string] : the name the user gave the event
-   time [int] : time of the event, the units are timeSinceEpoch. So ms since 01-01-1970.
-   airspaceId [uuid] : reference id from airspace.
-   airspaceName [string] : reference to the airspace name


<a id="orgf6d9bc0"></a>

## aircraft

Aircraft is self explainatory. This is where users created aircraft are stored. They create aircraft based on what they are flying, which is specified (via USN) with BUNO. Side numbers can be replicated and are not useful for complete identification.

-   id [uuid] : unique id for the aircraft.
-   buno [string] : again a unique identifier, though this is one that aircrew and maintenence personelle are familiar with.
-   side [string] : side number, unique for SQDN&rsquo;s but differing SQDN&rsquo;s can have the same side numbers.
-   squadron [string] : the squadron that the plane currently belongs too at the time. This can change.
-   service [string] : which service the plane belongs too.
-   tms [string] : the type of aircraft (tms is navy specific, airforce uses MDS).
-   software [string] : the software the tms/mds is using.


<a id="orgb71a0cf"></a>

## MarkerType

Marker Types are the bread and butter of RAPID. Types are made up of fields, which we will go over in depth later. MarkerTypes are what is \`placed\` during an event, and is what TAP/aircrew use to evaluate performance for a given skill. Though markerTypes should not be thought of directly as skills, but mainly markers mark a specific point in time. Meaning we can mark a death/kill/skill/learning stamp/etc.

-   id [uuid] : unique id for the markerType.

