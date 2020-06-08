# API references

::: tip
Props with an `*` are required.
:::

[[toc]]

## Props
### images*

An array containing the paths of the images you wan to use.
* **type** : Array
* **required** : *true*
* **default value** : `[]`

### displacement*

The path of the displacement image.
* **type** : String
* **required** : *true*
* **default value** : `none`

### intensity

The intensity of the displacement.
* **type** : Number
* **required** : *false*
* **default value** : `1`

### speedIn

The duration of the animation for the next image, in seconds.
* **type** : Number 
* **required** : *false*
* **default value** : `1`

### speedOut

The duration of the animation for the previous image, in seconds.
* **type** : Number
* **required** : *false*
* **default value** : `1`

### ease

The GSAP easing to use.
* **type** : String
* **required** : *false*
* **default value** : `expo.out`

### preserveAspectRatio

Whether the images keep their aspect ratio (act as ``background-size`` : ``cover`` (true) or ``contain`` (false).
* **type** : Boolean
* **required** : *false*
* **default value** : `true`

### isInteractive

Whether the canvas is interactive on mouse move.
* **type** : Boolean
* **required** : *false*
* **default value** : `false`

### interactionFactor

The factor of the interaction.
* **type** : Number
* **required** : *false*
* **default value** : `1`

### interactionDuration

The duration of the interaction.
* **type** : Number
* **required** : *false*
* **default value** : `1`

### startAsTransparent

Whether the canvas is initially transparent and the first transition goes to the first picture.
* **type** : Boolean
* **required** : *false*
* **default value** : `false`

### angle

The angle of the transition.
* **type** : Number 
* **required** : *false*
* **default value** : `Math.PI / 4`

## Methods

### next()

Transition to the second image.
* **Params** : ``none``
* **Returns** : ``void``

### previous()

Transition to the first image.
* **Params** : ``none``
* **Returns** : ``void``

### pause()

Pause the current transition.
* **Params** : ``none``
* **Returns** : ``void``

### play()

Play the current paused animation.
* **Params** : ``none``
* **Returns** : ``void``

### insertImage(path,index)

Insert an image at a given index.
* **Params** : 
    - ``path`` : the path of the image
    - ``index`` :  the index of the inserted image, if not provided, the image will be inserted at the end of the array. It has the same behavior as the ``splice`` method (negative number allowed).
* **Returns** : a Promise resolved when the image is loaded.

### insertTransparentTexture(index)

Insert a transparent texture at a given index.
* **Params** : 
    - ``index`` : the index of the inserted image, it has the same behavior as the ``insertImage`` ``index`` parameter.
* **Returns** : ``void``

### removeImage(index)

Remove an image at a given index.
* **Params** : 
    - ``index`` : the index of the image to remove (must be different from the current image index).
* **Returns** : ``void``

### goTo(index)

Transition to a given image by its index.
* **Params** : 
    - ``index`` : the index of the image to transition to.
* **Returns** : ``void``


## Events
### loaded

Fired when the component is ready.

### animationEnd

Fired when the transition is done.