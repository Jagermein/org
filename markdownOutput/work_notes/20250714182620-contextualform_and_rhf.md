
# Table of Contents

1.  [Overview](#org5698956)
2.  [ContextualForm Component](#org16b8876)
    1.  [Purpose](#org2ae345b)
    2.  [Key Behaviors](#orge46ae82)
    3.  [Code Reference](#org34a4a7d)
3.  [useForm vs useFormContext](#org078c9c2)
    1.  [useForm](#org7c50f83)
    2.  [useFormContext](#org2f8d22c)
4.  [Why not use useForm everywhere?](#org85a9fe6)
5.  [Controlled Selects and useEffect](#org378beae)
6.  [Example Pattern](#orgecde077)



<a id="org5698956"></a>

# Overview

This note describes how the app handles complex forms using \`react-hook-form\` (RHF) and a shared wrapper component called \`ContextualForm\`.

Instead of calling \`useForm()\` in each field component (which would create multiple isolated forms), the app wraps all form content in a shared \`ContextualForm\`, allowing nested components to access the same form state via \`useFormContext()\`.


<a id="org16b8876"></a>

# ContextualForm Component


<a id="org2ae345b"></a>

## Purpose

Creates a single RHF form context and provides it to all nested components.


<a id="orge46ae82"></a>

## Key Behaviors

-   Accepts `defaultValue` or `values` for form initialization.
-   Automatically resets form state when `defaultValue` changes (if `shouldReset` is true).
-   Can trigger `onSubmit` on `change` or `submit` depending on `type`.
-   Wraps children in `FormProvider`, allowing access to RHF context using `useFormContext()`.


<a id="org34a4a7d"></a>

## Code Reference

<file:///Users/chancenorris/your-path-to/contextualForm.js>


<a id="org078c9c2"></a>

# useForm vs useFormContext


<a id="org7c50f83"></a>

## useForm

-   Only used in the top-level `ContextualForm`.
-   Creates the main form instance.
-   Should NOT be used in nested components (would create disconnected state).


<a id="org2f8d22c"></a>

## useFormContext

-   Used in all children under `ContextualForm`.
-   Accesses the shared form state.
-   Enables registering fields, watching values, and using validation.


<a id="org85a9fe6"></a>

# Why not use useForm everywhere?

-   Would create multiple form contexts and break form state.
-   Only one form context should exist — provided via `FormProvider`.
-   Best practice is to call `useForm()` once and access it with `useFormContext()`.


<a id="org378beae"></a>

# Controlled Selects and useEffect

-   If setting a default value in a dropdown, use `setValue(...) + watch(...) + value` binding.
-   Avoid setting state inline during render; use `useEffect` for that.


<a id="orgecde077"></a>

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

