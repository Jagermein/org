
# Table of Contents

1.  [Overview](#org4a6a817)
2.  [ContextualForm Component](#org602604d)
    1.  [Purpose](#orgf20d920)
    2.  [Key Behaviors](#org50aa58b)
    3.  [Code Reference](#org7f4f31b)
3.  [useForm vs useFormContext](#orgc7e203e)
    1.  [useForm](#org86285ad)
    2.  [useFormContext](#orgfd59094)
4.  [Why not use useForm everywhere?](#org38f804a)
5.  [Controlled Selects and useEffect](#org2dd8c9d)
6.  [Example Pattern](#orgc9e87fb)



<a id="org4a6a817"></a>

# Overview

This note describes how the app handles complex forms using \`react-hook-form\` (RHF) and a shared wrapper component called \`ContextualForm\`.

Instead of calling \`useForm()\` in each field component (which would create multiple isolated forms), the app wraps all form content in a shared \`ContextualForm\`, allowing nested components to access the same form state via \`useFormContext()\`.


<a id="org602604d"></a>

# ContextualForm Component


<a id="orgf20d920"></a>

## Purpose

Creates a single RHF form context and provides it to all nested components.


<a id="org50aa58b"></a>

## Key Behaviors

-   Accepts `defaultValue` or `values` for form initialization.
-   Automatically resets form state when `defaultValue` changes (if `shouldReset` is true).
-   Can trigger `onSubmit` on `change` or `submit` depending on `type`.
-   Wraps children in `FormProvider`, allowing access to RHF context using `useFormContext()`.


<a id="org7f4f31b"></a>

## Code Reference

<file:///Users/chancenorris/your-path-to/contextualForm.js>


<a id="orgc7e203e"></a>

# useForm vs useFormContext


<a id="org86285ad"></a>

## useForm

-   Only used in the top-level `ContextualForm`.
-   Creates the main form instance.
-   Should NOT be used in nested components (would create disconnected state).


<a id="orgfd59094"></a>

## useFormContext

-   Used in all children under `ContextualForm`.
-   Accesses the shared form state.
-   Enables registering fields, watching values, and using validation.


<a id="org38f804a"></a>

# Why not use useForm everywhere?

-   Would create multiple form contexts and break form state.
-   Only one form context should exist — provided via `FormProvider`.
-   Best practice is to call `useForm()` once and access it with `useFormContext()`.


<a id="org2dd8c9d"></a>

# Controlled Selects and useEffect

-   If setting a default value in a dropdown, use `setValue(...) + watch(...) + value` binding.
-   Avoid setting state inline during render; use `useEffect` for that.


<a id="orgc9e87fb"></a>

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

