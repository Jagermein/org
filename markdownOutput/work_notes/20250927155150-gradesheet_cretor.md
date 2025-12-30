
# Table of Contents

1.  [Data Picking (Left Side)](#org5d8b5a0)
    1.  [Data Picker will send the data via a form into the dataForm which will show all data in collapsable form where they can rearrange order](#org53ab6d0)
    2.  [The data that will be shown in the Data Picker](#org819c07f)
        1.  [Category : String](#org621278c)
        2.  [Marker Type : Id](#orgd80d4f2)
        3.  [Marker Feild : Id](#orgd4f223d)
        4.  [Marker Field Type | &rsquo;Total&rsquo; : String](#org5c2b962)
        5.  [labels : String](#org835f2d2)
    3.  [The Data will have the format of the numerator/denominator type. Along with a label](#org8737e45)
    4.  [We need the data to be sent over as a metric](#orga92635e)
        1.  [A Metric is just the numerator and denominator that the user chooses.](#org3ec9a2f)
    5.  [Once this is sent over the picker resets](#org1da652b)
2.  [Data Form](#org5e494e9)
    1.  [The data form is what the user will be able to choose the order of everything.](#org84190f0)
    2.  [THIS WILL BE THE FINAL PUSH TO DB](#org40aa874)
    3.  [The categories and the metrics need to be able to be changed around. This requires drag and drop capabilities to occur.](#orgc6e68ee)
    4.  [The format is :](#orgead8ac3)
        1.  [{ { Categories { Metric Id } } Metrics { MetricObj } }](#org05a91cf)
        2.  [This is containing the orders and the MetricIds, it will then contain all the information of the metrics that the first portion will reference.](#orgadf0fa1)
    5.  [The Data Form Needs the ability to have the following Handles (@ First Glance)](#org698bc28)
        1.  [Order States](#orgdb792a6)
        2.  [Removing Metric](#org22d1104)
        3.  [Collapse States (Category and Metric?)](#orgf58cdd0)
        4.  [Dragging? | dependent on the React DnD setup](#orgf633276)
        5.  [nrf](#org0001b17)



<a id="org5d8b5a0"></a>

# Data Picking (Left Side)


<a id="org53ab6d0"></a>

## Data Picker will send the data via a form into the dataForm which will show all data in collapsable form where they can rearrange order


<a id="org819c07f"></a>

## The data that will be shown in the Data Picker


<a id="org621278c"></a>

### Category : String


<a id="orgd80d4f2"></a>

### Marker Type : Id


<a id="orgd4f223d"></a>

### Marker Feild : Id


<a id="org5c2b962"></a>

### Marker Field Type | &rsquo;Total&rsquo; : String


<a id="org835f2d2"></a>

### labels : String


<a id="org8737e45"></a>

## The Data will have the format of the numerator/denominator type. Along with a label


<a id="orga92635e"></a>

## We need the data to be sent over as a metric


<a id="org3ec9a2f"></a>

### A Metric is just the numerator and denominator that the user chooses.


<a id="org1da652b"></a>

## Once this is sent over the picker resets


<a id="org5e494e9"></a>

# Data Form


<a id="org84190f0"></a>

## The data form is what the user will be able to choose the order of everything.


<a id="org40aa874"></a>

## THIS WILL BE THE FINAL PUSH TO DB


<a id="orgc6e68ee"></a>

## The categories and the metrics need to be able to be changed around. This requires drag and drop capabilities to occur.


<a id="orgead8ac3"></a>

## The format is :


<a id="org05a91cf"></a>

### { { Categories { Metric Id } } Metrics { MetricObj } }


<a id="orgadf0fa1"></a>

### This is containing the orders and the MetricIds, it will then contain all the information of the metrics that the first portion will reference.


<a id="org698bc28"></a>

## The Data Form Needs the ability to have the following Handles (@ First Glance)


<a id="orgdb792a6"></a>

### Order States


<a id="org22d1104"></a>

### Removing Metric


<a id="orgf58cdd0"></a>

### Collapse States (Category and Metric?)

1.  QUESTION : Do we want category to collapse initially? I mean we don&rsquo;t really need it IMO. But we still might need some container to hold nested collapsible things


<a id="orgf633276"></a>

### Dragging? | dependent on the React DnD setup


<a id="org0001b17"></a>

### nrf

