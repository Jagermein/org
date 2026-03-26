---
title: #("contextual forms" 0 16 (fontified nil))
layout: post
date: 2026-03-26
description: #("#+created: <2026-03-26 Thu>" 0 27 (ws-butler-chg chg wrap-prefix "" line-prefix "" fontified nil))
tags: [react-hook-form context forms blueprintjs]
categories: [Testing]
---


# Table of Contents

1.  [Overview](#org9f6660b)
2.  [ContextualForm Component](#org929b9c7)
    1.  [Purpose](#org8467d83)
    2.  [Key Behaviors](#orgc88e510)
    3.  [Code Reference](#orgdb83f29)
3.  [useForm vs useFormContext](#org6102882)
    1.  [useForm](#org53cfe63)
    2.  [useFormContext](#org182e774)
4.  [Why not use useForm everywhere?](#org96ba058)
5.  [Controlled Selects and useEffect](#orgbd6e451)
6.  [Example Pattern](#org6d77fdb)

:ID:       2ca1e0f6-bf1f-4a61-a680-b263dea95426


<a id="org9f6660b"></a>

# Overview

This note describes how the app handles complex forms using \`react-hook-form\` (RHF) and a shared wrapper component called \`ContextualForm\`.

Instead of calling \`useForm()\` in each field component (which would create multiple isolated forms), the app wraps all form content in a shared \`ContextualForm\`, allowing nested components to access the same form state via \`useFormContext()\`.


<a id="org929b9c7"></a>

# ContextualForm Component


<a id="org8467d83"></a>

## Purpose

Creates a single RHF form context and provides it to all nested components.


<a id="orgc88e510"></a>

## Key Behaviors

-   Accepts `defaultValue` or `values` for form initialization.
-   Automatically resets form state when `defaultValue` changes (if `shouldReset` is true).
-   Can trigger `onSubmit` on `change` or `submit` depending on `type`.
-   Wraps children in `FormProvider`, allowing access to RHF context using `useFormContext()`.


<a id="orgdb83f29"></a>

## Code Reference

<file:///Users/chancenorris/your-path-to/contextualForm.js>


<a id="org6102882"></a>

# useForm vs useFormContext


<a id="org53cfe63"></a>

## useForm

-   Only used in the top-level `ContextualForm`.
-   Creates the main form instance.
-   Should NOT be used in nested components (would create disconnected state).


<a id="org182e774"></a>

## useFormContext

-   Used in all children under `ContextualForm`.
-   Accesses the shared form state.
-   Enables registering fields, watching values, and using validation.


<a id="org96ba058"></a>

# Why not use useForm everywhere?

-   Would create multiple form contexts and break form state.
-   Only one form context should exist — provided via `FormProvider`.
-   Best practice is to call `useForm()` once and access it with `useFormContext()`.


<a id="orgbd6e451"></a>

# Controlled Selects and useEffect

-   If setting a default value in a dropdown, use `setValue(...) + watch(...) + value` binding.
-   Avoid setting state inline during render; use `useEffect` for that.


<a id="org6d77fdb"></a>

# Example Pattern

    const { register, setValue, watch } = useFormContext();
    const selected = watch('service');
    
    useEffect(() => {
      if (initialService) {
        setValue('service', initialService);
      }
    }, [initialService, setValue]);
    
    <HTMLSelect {...register('service')} value={selected}>
      {!initialService && <option value=''>Select service...</option>}
      <option value='USN'>USN</option>
      ...
    </HTMLSelect>

