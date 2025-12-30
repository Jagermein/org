
# Table of Contents

1.  [Overview](#org1c4afb0)
2.  [ContextualForm Component](#org4dfa814)
    1.  [Purpose](#org2b3de8f)
    2.  [Key Behaviors](#org898cc79)
    3.  [Code Reference](#orge6b9776)
3.  [useForm vs useFormContext](#orgaf6964d)
    1.  [useForm](#org32aed68)
    2.  [useFormContext](#org57d8bfa)
4.  [Why not use useForm everywhere?](#orge034769)
5.  [Controlled Selects and useEffect](#org0d36b8c)
6.  [Example Pattern](#orga70d27a)



<a id="org1c4afb0"></a>

# Overview

This note describes how the app handles complex forms using \`react-hook-form\` (RHF) and a shared wrapper component called \`ContextualForm\`.

Instead of calling \`useForm()\` in each field component (which would create multiple isolated forms), the app wraps all form content in a shared \`ContextualForm\`, allowing nested components to access the same form state via \`useFormContext()\`.


<a id="org4dfa814"></a>

# ContextualForm Component


<a id="org2b3de8f"></a>

## Purpose

Creates a single RHF form context and provides it to all nested components.


<a id="org898cc79"></a>

## Key Behaviors

-   Accepts `defaultValue` or `values` for form initialization.
-   Automatically resets form state when `defaultValue` changes (if `shouldReset` is true).
-   Can trigger `onSubmit` on `change` or `submit` depending on `type`.
-   Wraps children in `FormProvider`, allowing access to RHF context using `useFormContext()`.


<a id="orge6b9776"></a>

## Code Reference

<file:///Users/chancenorris/your-path-to/contextualForm.js>


<a id="orgaf6964d"></a>

# useForm vs useFormContext


<a id="org32aed68"></a>

## useForm

-   Only used in the top-level `ContextualForm`.
-   Creates the main form instance.
-   Should NOT be used in nested components (would create disconnected state).


<a id="org57d8bfa"></a>

## useFormContext

-   Used in all children under `ContextualForm`.
-   Accesses the shared form state.
-   Enables registering fields, watching values, and using validation.


<a id="orge034769"></a>

# Why not use useForm everywhere?

-   Would create multiple form contexts and break form state.
-   Only one form context should exist — provided via `FormProvider`.
-   Best practice is to call `useForm()` once and access it with `useFormContext()`.


<a id="org0d36b8c"></a>

# Controlled Selects and useEffect

-   If setting a default value in a dropdown, use `setValue(...) + watch(...) + value` binding.
-   Avoid setting state inline during render; use `useEffect` for that.


<a id="orga70d27a"></a>

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

