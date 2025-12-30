
# Table of Contents

1.  [Overview](#org24c6450)
2.  [ContextualForm Component](#org4e0b186)
    1.  [Purpose](#org98117f3)
    2.  [Key Behaviors](#org58fbab2)
    3.  [Code Reference](#org07d1021)
3.  [useForm vs useFormContext](#org47a94c1)
    1.  [useForm](#org97614a2)
    2.  [useFormContext](#orgeff2765)
4.  [Why not use useForm everywhere?](#org01cf775)
5.  [Controlled Selects and useEffect](#orgc3238d7)
6.  [Example Pattern](#org0c6b768)



<a id="org24c6450"></a>

# Overview

This note describes how the app handles complex forms using \`react-hook-form\` (RHF) and a shared wrapper component called \`ContextualForm\`.

Instead of calling \`useForm()\` in each field component (which would create multiple isolated forms), the app wraps all form content in a shared \`ContextualForm\`, allowing nested components to access the same form state via \`useFormContext()\`.


<a id="org4e0b186"></a>

# ContextualForm Component


<a id="org98117f3"></a>

## Purpose

Creates a single RHF form context and provides it to all nested components.


<a id="org58fbab2"></a>

## Key Behaviors

-   Accepts `defaultValue` or `values` for form initialization.
-   Automatically resets form state when `defaultValue` changes (if `shouldReset` is true).
-   Can trigger `onSubmit` on `change` or `submit` depending on `type`.
-   Wraps children in `FormProvider`, allowing access to RHF context using `useFormContext()`.


<a id="org07d1021"></a>

## Code Reference

<file:///Users/chancenorris/your-path-to/contextualForm.js>


<a id="org47a94c1"></a>

# useForm vs useFormContext


<a id="org97614a2"></a>

## useForm

-   Only used in the top-level `ContextualForm`.
-   Creates the main form instance.
-   Should NOT be used in nested components (would create disconnected state).


<a id="orgeff2765"></a>

## useFormContext

-   Used in all children under `ContextualForm`.
-   Accesses the shared form state.
-   Enables registering fields, watching values, and using validation.


<a id="org01cf775"></a>

# Why not use useForm everywhere?

-   Would create multiple form contexts and break form state.
-   Only one form context should exist — provided via `FormProvider`.
-   Best practice is to call `useForm()` once and access it with `useFormContext()`.


<a id="orgc3238d7"></a>

# Controlled Selects and useEffect

-   If setting a default value in a dropdown, use `setValue(...) + watch(...) + value` binding.
-   Avoid setting state inline during render; use `useEffect` for that.


<a id="org0c6b768"></a>

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

