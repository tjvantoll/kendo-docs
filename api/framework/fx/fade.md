---
title: FX Fade
slug: api-fx-fade
publish: true
---

# Fade

Fades the element in or out.
Supported directions are `in` and `out`.

## Fading an element out
    <div id="foo">
        I will fade out
    </div>

    <script>
        kendo.fx($("#foo")).fade("out").play();
        // an alternative syntax would be
        // kendo.fx($("#foo")).fadeOut.play();
    </script>

## Fading an element in

    <div id="foo">
        I will fade in
    </div>

    <script>
        kendo.fx($("#foo")).fade("in").play();
        // an alternative syntax would be
        // kendo.fx($("#foo")).fadeIn.play();
    </script>

## Constructor Parameters

### direction

The direction of the effect.

## Methods

### startValue

Sets the fade value for the element when it is faded in. By default the element fades in to opacity value of 1.

#### Parameters

##### value `Number`

the fade in value.

#### Returns

`Effect` The effect instance

### endValue

Sets the fade value for the element when it is faded out. By default the element fades in to opacity value of 0.

#### Parameters

##### value `Number`

the fade out value.

#### Returns

`Effect` The effect instance


