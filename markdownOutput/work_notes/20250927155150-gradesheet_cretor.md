
# Table of Contents

1.  [Data Picking (Left Side)](#org3641468)
    1.  [Data Picker will send the data via a form into the dataForm which will show all data in collapsable form where they can rearrange order](#org4b83e10)
    2.  [The data that will be shown in the Data Picker](#orgc31fb44)
        1.  [Category : String](#org3817d1b)
        2.  [Marker Type : Id](#org452e6bb)
        3.  [Marker Feild : Id](#orgd15cb41)
        4.  [Marker Field Type | &rsquo;Total&rsquo; : String](#org04760a8)
        5.  [labels : String](#org17e954d)
    3.  [The Data will have the format of the numerator/denominator type. Along with a label](#org59623d7)
    4.  [We need the data to be sent over as a metric](#orgd745aaf)
        1.  [A Metric is just the numerator and denominator that the user chooses.](#org3a7624a)
    5.  [Once this is sent over the picker resets](#org325b254)
2.  [Data Form](#orgad316c2)
    1.  [The data form is what the user will be able to choose the order of everything.](#org7ee9cbe)
    2.  [THIS WILL BE THE FINAL PUSH TO DB](#org59231c4)
    3.  [The categories and the metrics need to be able to be changed around. This requires drag and drop capabilities to occur.](#org671a86e)
    4.  [The format is :](#org7595276)
        1.  [{ { Categories { Metric Id } } Metrics { MetricObj } }](#org62075eb)
        2.  [This is containing the orders and the MetricIds, it will then contain all the information of the metrics that the first portion will reference.](#org4feb2e4)
    5.  [The Data Form Needs the ability to have the following Handles (@ First Glance)](#org6a2a2e7)
        1.  [Order States](#org4eb52d7)
        2.  [Removing Metric](#orga77e251)
        3.  [Collapse States (Category and Metric?)](#org4be8c7b)
        4.  [Dragging? | dependent on the React DnD setup](#org46d2d7c)
        5.  [nrf](#org37a675f)



<a id="org3641468"></a>

# Data Picking (Left Side)


<a id="org4b83e10"></a>

## Data Picker will send the data via a form into the dataForm which will show all data in collapsable form where they can rearrange order


<a id="orgc31fb44"></a>

## The data that will be shown in the Data Picker


<a id="org3817d1b"></a>

### Category : String


<a id="org452e6bb"></a>

### Marker Type : Id


<a id="orgd15cb41"></a>

### Marker Feild : Id


<a id="org04760a8"></a>

### Marker Field Type | &rsquo;Total&rsquo; : String


<a id="org17e954d"></a>

### labels : String


<a id="org59623d7"></a>

## The Data will have the format of the numerator/denominator type. Along with a label


<a id="orgd745aaf"></a>

## We need the data to be sent over as a metric


<a id="org3a7624a"></a>

### A Metric is just the numerator and denominator that the user chooses.


<a id="org325b254"></a>

## Once this is sent over the picker resets


<a id="orgad316c2"></a>

# Data Form


<a id="org7ee9cbe"></a>

## The data form is what the user will be able to choose the order of everything.


<a id="org59231c4"></a>

## THIS WILL BE THE FINAL PUSH TO DB


<a id="org671a86e"></a>

## The categories and the metrics need to be able to be changed around. This requires drag and drop capabilities to occur.


<a id="org7595276"></a>

## The format is :


<a id="org62075eb"></a>

### { { Categories { Metric Id } } Metrics { MetricObj } }


<a id="org4feb2e4"></a>

### This is containing the orders and the MetricIds, it will then contain all the information of the metrics that the first portion will reference.


<a id="org6a2a2e7"></a>

## The Data Form Needs the ability to have the following Handles (@ First Glance)


<a id="org4eb52d7"></a>

### Order States


<a id="orga77e251"></a>

### Removing Metric


<a id="org4be8c7b"></a>

### Collapse States (Category and Metric?)

1.  QUESTION : Do we want category to collapse initially? I mean we don&rsquo;t really need it IMO. But we still might need some container to hold nested collapsible things


<a id="org46d2d7c"></a>

### Dragging? | dependent on the React DnD setup


<a id="org37a675f"></a>

### nrf

