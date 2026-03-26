
# Table of Contents

1.  [Overview](#orgebb17b4)
2.  [ContextualForm Component](#org436e3fd)
    1.  [Purpose](#orgc6c8fc1)
    2.  [Key Behaviors](#org3250028)
    3.  [Code Reference](#orgd0cfbd4)
3.  [useForm vs useFormContext](#org99aab80)
    1.  [useForm](#org51eb0bc)
    2.  [useFormContext](#org7bad400)
4.  [Why not use useForm everywhere?](#orgb71179f)
5.  [Controlled Selects and useEffect](#orgfb852c2)
6.  [Example Pattern](#orga380220)

:ID:       2ca1e0f6-bf1f-4a61-a680-b263dea95426


<a id="orgebb17b4"></a>

# Overview

This note describes how the app handles complex forms using \`react-hook-form\` (RHF) and a shared wrapper component called \`ContextualForm\`.

Instead of calling \`useForm()\` in each field component (which would create multiple isolated forms), the app wraps all form content in a shared \`ContextualForm\`, allowing nested components to access the same form state via \`useFormContext()\`.


<a id="org436e3fd"></a>

# ContextualForm Component


<a id="orgc6c8fc1"></a>

## Purpose

Creates a single RHF form context and provides it to all nested components.


<a id="org3250028"></a>

## Key Behaviors

-   Accepts `defaultValue` or `values` for form initialization.
-   Automatically resets form state when `defaultValue` changes (if `shouldReset` is true).
-   Can trigger `onSubmit` on `change` or `submit` depending on `type`.
-   Wraps children in `FormProvider`, allowing access to RHF context using `useFormContext()`.


<a id="orgd0cfbd4"></a>

## Code Reference

<file:///Users/chancenorris/your-path-to/contextualForm.js>


<a id="org99aab80"></a>

# useForm vs useFormContext


<a id="org51eb0bc"></a>

## useForm

-   Only used in the top-level `ContextualForm`.
-   Creates the main form instance.
-   Should NOT be used in nested components (would create disconnected state).


<a id="org7bad400"></a>

## useFormContext

-   Used in all children under `ContextualForm`.
-   Accesses the shared form state.
-   Enables registering fields, watching values, and using validation.


<a id="orgb71179f"></a>

# Why not use useForm everywhere?

-   Would create multiple form contexts and break form state.
-   Only one form context should exist — provided via `FormProvider`.
-   Best practice is to call `useForm()` once and access it with `useFormContext()`.


<a id="orgfb852c2"></a>

# Controlled Selects and useEffect

-   If setting a default value in a dropdown, use `setValue(...) + watch(...) + value` binding.
-   Avoid setting state inline during render; use `useEffect` for that.


<a id="orga380220"></a>

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

