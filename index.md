---
title: Guide
lang: en-US
---

# Guide

[[toc]]

## Introduction

``vue-displacement-slideshow`` is a Vue.js 2.0 slideshow component working with [Three.js](https://threejs.org/) and [GSAP](https://greensock.com/gsap/). This component made simple Webgl image displacement transitions.

::: tip
You can find a demo of the component [here](https://vue-displacement-slideshow.now.sh/).
:::

![demo](./demo.gif) 

## Getting Started

### Installation 

You can install ``vue-displacement-slideshow`` using NPM or a CDN.

#### NPM
```
npm i --save vue-displacement-slideshow
```

#### CDN

```html
<script src="https://cdn.jsdelivr.net/npm/vue-displacement-slideshow"></script>
```

::: tip
You can also get the lib directly with downloading the [dist](https://github.com/AlbanCrepel/vue-displacement-slideshow/tree/master/dist) from the github repository.
:::

### Usage

You can import the ``vue-displacement-slideshow`` directly into a component like this : 

```vue
<script>
    import VueDisplacementSlideshow from "vue-displacement-slideshow";

    export default {
        components: {
            VueDisplacementSlideshow,
        },
    };
</script>
```

You can also import it globaly like this :

```js
import Vue from 'vue';
import VueDisplacementSlideshow from 'vue-displacement-slideshow';

Vue.component('vue-displacement-slideshow', VueDisplacementSlideshow);
```

To use the component two props are required, `images` and `displacement`.

* **images** : An array containing the paths of the images you wan to use
* **displacement** : The path of the displacement image

::: tip
You can also the [API reference](./api) to see all props and methods.
:::

### Example

**VueJs 2.0**

This is a complete example of the ``vue-displacement-slideshow`` component.

```vue
<template>
    <vue-displacement-slideshow
            :images="images"
            displacement="require('../assets/displacement.png')"
            :intensity="0.2"
            :speedIn="1.4"
            :speedOut="1.4"
            ease="expo.out"
            ref="slideshow"></vue-displacement-slideshow>
</template>

<script>
    import VueDisplacementSlideshow from "vue-displacement-slideshow";

    export default {
        components: {
            VueDisplacementSlideshow,
        },
        computed: {
            images() {
                return [
                    require("../assets/images/1.jpg"),
                    require("../assets/images/2.jpg"),
                    require("../assets/images/3.jpg")
                ];
            }
        },
        methods: {
            init() {
                //We loop through all our images by calling the 'next' method of our component every 2 seconds
                setInterval(() => {
                    this.$refs.slideshow.next();
                }, 2000);
            }
        },
        mounted() {
            this.init();
        }
    };
</script>
```

**Nuxt**

Just wrap the component between a ``no-ssr`` tag like so :

```vue
<no-ssr>
    <vue-displacement-slideshow />
</no-ssr>
```

## Behavior

The first image of the array is displayed at first.
When we call the `next` method while currently showing the last image, it will go to the first image.
When we call the `previous` method while currently showing the first image, it will go to the last image.

The images are displayed as we would use `background-size:cover` in CSS.

If you set the prop `startAsTransparent` to `true`, then it **adds a texture to your `images` array**. If you want to 
remove it after, you can just call the `removeImage` method with `0` as the index parameter value.