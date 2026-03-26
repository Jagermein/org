
# Table of Contents

1.  [Overview](#org420cc18)
2.  [ContextualForm Component](#org454b63d)
    1.  [Purpose](#org12021eb)
    2.  [Key Behaviors](#org6490655)
    3.  [Code Reference](#org0c5bffa)
3.  [useForm vs useFormContext](#org7dd4b63)
    1.  [useForm](#orgfe53d4a)
    2.  [useFormContext](#orgd3a3aec)
4.  [Why not use useForm everywhere?](#org10ac5dc)
5.  [Controlled Selects and useEffect](#orgfd0fa92)
6.  [Example Pattern](#org1b561d8)

:ID:       2ca1e0f6-bf1f-4a61-a680-b263dea95426


<a id="org420cc18"></a>

# Overview

This note describes how the app handles complex forms using \`react-hook-form\` (RHF) and a shared wrapper component called \`ContextualForm\`.

Instead of calling \`useForm()\` in each field component (which would create multiple isolated forms), the app wraps all form content in a shared \`ContextualForm\`, allowing nested components to access the same form state via \`useFormContext()\`.


<a id="org454b63d"></a>

# ContextualForm Component


<a id="org12021eb"></a>

## Purpose

Creates a single RHF form context and provides it to all nested components.


<a id="org6490655"></a>

## Key Behaviors

-   Accepts `defaultValue` or `values` for form initialization.
-   Automatically resets form state when `defaultValue` changes (if `shouldReset` is true).
-   Can trigger `onSubmit` on `change` or `submit` depending on `type`.
-   Wraps children in `FormProvider`, allowing access to RHF context using `useFormContext()`.


<a id="org0c5bffa"></a>

## Code Reference

<file:///Users/chancenorris/your-path-to/contextualForm.js>


<a id="org7dd4b63"></a>

# useForm vs useFormContext


<a id="orgfe53d4a"></a>

## useForm

-   Only used in the top-level `ContextualForm`.
-   Creates the main form instance.
-   Should NOT be used in nested components (would create disconnected state).


<a id="orgd3a3aec"></a>

## useFormContext

-   Used in all children under `ContextualForm`.
-   Accesses the shared form state.
-   Enables registering fields, watching values, and using validation.


<a id="org10ac5dc"></a>

# Why not use useForm everywhere?

-   Would create multiple form contexts and break form state.
-   Only one form context should exist — provided via `FormProvider`.
-   Best practice is to call `useForm()` once and access it with `useFormContext()`.


<a id="orgfd0fa92"></a>

# Controlled Selects and useEffect

-   If setting a default value in a dropdown, use `setValue(...) + watch(...) + value` binding.
-   Avoid setting state inline during render; use `useEffect` for that.


<a id="org1b561d8"></a>

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

