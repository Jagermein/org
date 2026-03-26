
# Table of Contents

1.  [Data Picking (Left Side)](#org8c8ddc5)
    1.  [Data Picker will send the data via a form into the dataForm which will show all data in collapsable form where they can rearrange order](#orgda79dba)
    2.  [The data that will be shown in the Data Picker](#org9853b79)
        1.  [Category : String](#org057ffdb)
        2.  [Marker Type : Id](#orgfe13e28)
        3.  [Marker Feild : Id](#org3e20442)
        4.  [Marker Field Type | &rsquo;Total&rsquo; : String](#orgc04d476)
        5.  [labels : String](#org691ed13)
    3.  [The Data will have the format of the numerator/denominator type. Along with a label](#org9128dd0)
    4.  [We need the data to be sent over as a metric](#orgfa434fc)
        1.  [A Metric is just the numerator and denominator that the user chooses.](#org5e84da3)
    5.  [Once this is sent over the picker resets](#org81c24bf)
2.  [Data Form](#org96d8401)
    1.  [The data form is what the user will be able to choose the order of everything.](#org399726b)
    2.  [THIS WILL BE THE FINAL PUSH TO DB](#org123b21f)
    3.  [The categories and the metrics need to be able to be changed around. This requires drag and drop capabilities to occur.](#org8e5133e)
    4.  [The format is :](#orgc1b0b63)
        1.  [{ { Categories { Metric Id } } Metrics { MetricObj } }](#orgc7d1530)
        2.  [This is containing the orders and the MetricIds, it will then contain all the information of the metrics that the first portion will reference.](#org530127d)
    5.  [The Data Form Needs the ability to have the following Handles (@ First Glance)](#orge3d841f)
        1.  [Order States](#org7499098)
        2.  [Removing Metric](#org9ba46a7)
        3.  [Collapse States (Category and Metric?)](#orgc309140)
        4.  [Dragging? | dependent on the React DnD setup](#org8a408be)
        5.  [nrf](#org829f201)

:ID:       00daa17d-2335-4af7-9d13-1ad862f51b0e


<a id="org8c8ddc5"></a>

# Data Picking (Left Side)


<a id="orgda79dba"></a>

## Data Picker will send the data via a form into the dataForm which will show all data in collapsable form where they can rearrange order


<a id="org9853b79"></a>

## The data that will be shown in the Data Picker


<a id="org057ffdb"></a>

### Category : String


<a id="orgfe13e28"></a>

### Marker Type : Id


<a id="org3e20442"></a>

### Marker Feild : Id


<a id="orgc04d476"></a>

### Marker Field Type | &rsquo;Total&rsquo; : String


<a id="org691ed13"></a>

### labels : String


<a id="org9128dd0"></a>

## The Data will have the format of the numerator/denominator type. Along with a label


<a id="orgfa434fc"></a>

## We need the data to be sent over as a metric


<a id="org5e84da3"></a>

### A Metric is just the numerator and denominator that the user chooses.


<a id="org81c24bf"></a>

## Once this is sent over the picker resets


<a id="org96d8401"></a>

# Data Form


<a id="org399726b"></a>

## The data form is what the user will be able to choose the order of everything.


<a id="org123b21f"></a>

## THIS WILL BE THE FINAL PUSH TO DB


<a id="org8e5133e"></a>

## The categories and the metrics need to be able to be changed around. This requires drag and drop capabilities to occur.


<a id="orgc1b0b63"></a>

## The format is :


<a id="orgc7d1530"></a>

### { { Categories { Metric Id } } Metrics { MetricObj } }


<a id="org530127d"></a>

### This is containing the orders and the MetricIds, it will then contain all the information of the metrics that the first portion will reference.


<a id="orge3d841f"></a>

## The Data Form Needs the ability to have the following Handles (@ First Glance)


<a id="org7499098"></a>

### Order States


<a id="org9ba46a7"></a>

### Removing Metric


<a id="orgc309140"></a>

### Collapse States (Category and Metric?)

1.  QUESTION : Do we want category to collapse initially? I mean we don&rsquo;t really need it IMO. But we still might need some container to hold nested collapsible things


<a id="org8a408be"></a>

### Dragging? | dependent on the React DnD setup


<a id="org829f201"></a>

### nrf

