
# Table of Contents

1.  [Data Picking (Left Side)](#orgebfaf99)
    1.  [Data Picker will send the data via a form into the dataForm which will show all data in collapsable form where they can rearrange order](#orgdf29f8d)
    2.  [The data that will be shown in the Data Picker](#org7de13f8)
        1.  [Category : String](#org6d44232)
        2.  [Marker Type : Id](#org32adcd3)
        3.  [Marker Feild : Id](#org918169d)
        4.  [Marker Field Type | &rsquo;Total&rsquo; : String](#org84f0bef)
        5.  [labels : String](#orgc07e8f3)
    3.  [The Data will have the format of the numerator/denominator type. Along with a label](#org1ea0d6a)
    4.  [We need the data to be sent over as a metric](#org5369e4d)
        1.  [A Metric is just the numerator and denominator that the user chooses.](#org92a77c7)
    5.  [Once this is sent over the picker resets](#org283418e)
2.  [Data Form](#orgc422bb1)
    1.  [The data form is what the user will be able to choose the order of everything.](#org966c188)
    2.  [THIS WILL BE THE FINAL PUSH TO DB](#org5f1619a)
    3.  [The categories and the metrics need to be able to be changed around. This requires drag and drop capabilities to occur.](#orge51eca1)
    4.  [The format is :](#orgc73614c)
        1.  [{ { Categories { Metric Id } } Metrics { MetricObj } }](#org34c514f)
        2.  [This is containing the orders and the MetricIds, it will then contain all the information of the metrics that the first portion will reference.](#org1386f49)
    5.  [The Data Form Needs the ability to have the following Handles (@ First Glance)](#org5ee0d65)
        1.  [Order States](#org5f6657e)
        2.  [Removing Metric](#org0ac164c)
        3.  [Collapse States (Category and Metric?)](#orge66bec8)
        4.  [Dragging? | dependent on the React DnD setup](#orga173584)
        5.  [nrf](#org2527627)

:ID:       00daa17d-2335-4af7-9d13-1ad862f51b0e


<a id="orgebfaf99"></a>

# Data Picking (Left Side)


<a id="orgdf29f8d"></a>

## Data Picker will send the data via a form into the dataForm which will show all data in collapsable form where they can rearrange order


<a id="org7de13f8"></a>

## The data that will be shown in the Data Picker


<a id="org6d44232"></a>

### Category : String


<a id="org32adcd3"></a>

### Marker Type : Id


<a id="org918169d"></a>

### Marker Feild : Id


<a id="org84f0bef"></a>

### Marker Field Type | &rsquo;Total&rsquo; : String


<a id="orgc07e8f3"></a>

### labels : String


<a id="org1ea0d6a"></a>

## The Data will have the format of the numerator/denominator type. Along with a label


<a id="org5369e4d"></a>

## We need the data to be sent over as a metric


<a id="org92a77c7"></a>

### A Metric is just the numerator and denominator that the user chooses.


<a id="org283418e"></a>

## Once this is sent over the picker resets


<a id="orgc422bb1"></a>

# Data Form


<a id="org966c188"></a>

## The data form is what the user will be able to choose the order of everything.


<a id="org5f1619a"></a>

## THIS WILL BE THE FINAL PUSH TO DB


<a id="orge51eca1"></a>

## The categories and the metrics need to be able to be changed around. This requires drag and drop capabilities to occur.


<a id="orgc73614c"></a>

## The format is :


<a id="org34c514f"></a>

### { { Categories { Metric Id } } Metrics { MetricObj } }


<a id="org1386f49"></a>

### This is containing the orders and the MetricIds, it will then contain all the information of the metrics that the first portion will reference.


<a id="org5ee0d65"></a>

## The Data Form Needs the ability to have the following Handles (@ First Glance)


<a id="org5f6657e"></a>

### Order States


<a id="org0ac164c"></a>

### Removing Metric


<a id="orge66bec8"></a>

### Collapse States (Category and Metric?)

1.  QUESTION : Do we want category to collapse initially? I mean we don&rsquo;t really need it IMO. But we still might need some container to hold nested collapsible things


<a id="orga173584"></a>

### Dragging? | dependent on the React DnD setup


<a id="org2527627"></a>

### nrf

