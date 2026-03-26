---
title: #("Gradesheet Creator" 0 18 (fontified nil))
layout: post
date: 2026-03-26
description: #("#+created: <2026-03-26 Thu>" 0 27 (ws-butler-chg chg wrap-prefix "" line-prefix "" fontified nil))
categories: [Testing]
---


# Table of Contents

1.  [Data Picking (Left Side)](#orga05668e)
    1.  [Data Picker will send the data via a form into the dataForm which will show all data in collapsable form where they can rearrange order](#org567f8c0)
    2.  [The data that will be shown in the Data Picker](#orgc037aff)
        1.  [Category : String](#org96ac9ff)
        2.  [Marker Type : Id](#orgf921871)
        3.  [Marker Feild : Id](#org42324eb)
        4.  [Marker Field Type | &rsquo;Total&rsquo; : String](#org254e7fb)
        5.  [labels : String](#orgb88833d)
    3.  [The Data will have the format of the numerator/denominator type. Along with a label](#orgbc1f8b5)
    4.  [We need the data to be sent over as a metric](#orgcfb58cf)
        1.  [A Metric is just the numerator and denominator that the user chooses.](#orga08fe9f)
    5.  [Once this is sent over the picker resets](#org7d3deb3)
2.  [Data Form](#org8062820)
    1.  [The data form is what the user will be able to choose the order of everything.](#org79434d6)
    2.  [THIS WILL BE THE FINAL PUSH TO DB](#org6129c14)
    3.  [The categories and the metrics need to be able to be changed around. This requires drag and drop capabilities to occur.](#org7f43d1e)
    4.  [The format is :](#org87170fe)
        1.  [{ { Categories { Metric Id } } Metrics { MetricObj } }](#org5f33321)
        2.  [This is containing the orders and the MetricIds, it will then contain all the information of the metrics that the first portion will reference.](#org569a83a)
    5.  [The Data Form Needs the ability to have the following Handles (@ First Glance)](#orge929746)
        1.  [Order States](#org8b55112)
        2.  [Removing Metric](#orgfb32ba3)
        3.  [Collapse States (Category and Metric?)](#org46e271f)
        4.  [Dragging? | dependent on the React DnD setup](#org3905db5)
        5.  [nrf](#org972e135)

:ID:       00daa17d-2335-4af7-9d13-1ad862f51b0e


<a id="orga05668e"></a>

# Data Picking (Left Side)


<a id="org567f8c0"></a>

## Data Picker will send the data via a form into the dataForm which will show all data in collapsable form where they can rearrange order


<a id="orgc037aff"></a>

## The data that will be shown in the Data Picker


<a id="org96ac9ff"></a>

### Category : String


<a id="orgf921871"></a>

### Marker Type : Id


<a id="org42324eb"></a>

### Marker Feild : Id


<a id="org254e7fb"></a>

### Marker Field Type | &rsquo;Total&rsquo; : String


<a id="orgb88833d"></a>

### labels : String


<a id="orgbc1f8b5"></a>

## The Data will have the format of the numerator/denominator type. Along with a label


<a id="orgcfb58cf"></a>

## We need the data to be sent over as a metric


<a id="orga08fe9f"></a>

### A Metric is just the numerator and denominator that the user chooses.


<a id="org7d3deb3"></a>

## Once this is sent over the picker resets


<a id="org8062820"></a>

# Data Form


<a id="org79434d6"></a>

## The data form is what the user will be able to choose the order of everything.


<a id="org6129c14"></a>

## THIS WILL BE THE FINAL PUSH TO DB


<a id="org7f43d1e"></a>

## The categories and the metrics need to be able to be changed around. This requires drag and drop capabilities to occur.


<a id="org87170fe"></a>

## The format is :


<a id="org5f33321"></a>

### { { Categories { Metric Id } } Metrics { MetricObj } }


<a id="org569a83a"></a>

### This is containing the orders and the MetricIds, it will then contain all the information of the metrics that the first portion will reference.


<a id="orge929746"></a>

## The Data Form Needs the ability to have the following Handles (@ First Glance)


<a id="org8b55112"></a>

### Order States


<a id="orgfb32ba3"></a>

### Removing Metric


<a id="org46e271f"></a>

### Collapse States (Category and Metric?)

1.  QUESTION : Do we want category to collapse initially? I mean we don&rsquo;t really need it IMO. But we still might need some container to hold nested collapsible things


<a id="org3905db5"></a>

### Dragging? | dependent on the React DnD setup


<a id="org972e135"></a>

### nrf

