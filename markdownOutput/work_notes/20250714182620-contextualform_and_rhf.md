
# Table of Contents

1.  [Overview](#orga4a4465)
2.  [ContextualForm Component](#org149b758)
    1.  [Purpose](#orgf35c264)
    2.  [Key Behaviors](#orge4b72dd)
    3.  [Code Reference](#org14fa9f3)
3.  [useForm vs useFormContext](#org715f590)
    1.  [useForm](#org27bbe61)
    2.  [useFormContext](#orge2835a2)
4.  [Why not use useForm everywhere?](#orgf1eb17c)
5.  [Controlled Selects and useEffect](#orgb00aedf)
6.  [Example Pattern](#orgae1ab63)



<a id="orga4a4465"></a>

# Overview

This note describes how the app handles complex forms using \`react-hook-form\` (RHF) and a shared wrapper component called \`ContextualForm\`.

Instead of calling \`useForm()\` in each field component (which would create multiple isolated forms), the app wraps all form content in a shared \`ContextualForm\`, allowing nested components to access the same form state via \`useFormContext()\`.


<a id="org149b758"></a>

# ContextualForm Component


<a id="orgf35c264"></a>

## Purpose

Creates a single RHF form context and provides it to all nested components.


<a id="orge4b72dd"></a>

## Key Behaviors

-   Accepts `defaultValue` or `values` for form initialization.
-   Automatically resets form state when `defaultValue` changes (if `shouldReset` is true).
-   Can trigger `onSubmit` on `change` or `submit` depending on `type`.
-   Wraps children in `FormProvider`, allowing access to RHF context using `useFormContext()`.


<a id="org14fa9f3"></a>

## Code Reference

<file:///Users/chancenorris/your-path-to/contextualForm.js>


<a id="org715f590"></a>

# useForm vs useFormContext


<a id="org27bbe61"></a>

## useForm

-   Only used in the top-level `ContextualForm`.
-   Creates the main form instance.
-   Should NOT be used in nested components (would create disconnected state).


<a id="orge2835a2"></a>

## useFormContext

-   Used in all children under `ContextualForm`.
-   Accesses the shared form state.
-   Enables registering fields, watching values, and using validation.


<a id="orgf1eb17c"></a>

# Why not use useForm everywhere?

-   Would create multiple form contexts and break form state.
-   Only one form context should exist — provided via `FormProvider`.
-   Best practice is to call `useForm()` once and access it with `useFormContext()`.


<a id="orgb00aedf"></a>

# Controlled Selects and useEffect

-   If setting a default value in a dropdown, use `setValue(...) + watch(...) + value` binding.
-   Avoid setting state inline during render; use `useEffect` for that.


<a id="orgae1ab63"></a>

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

