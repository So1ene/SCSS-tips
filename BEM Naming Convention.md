
title: SCSS Naming Convention
created at: Tue Sep 08 2020 23:55:16 GMT+0000 (Coordinated Universal Time)
updated at: Mon Dec 14 2020 00:37:27 GMT+0000 (Coordinated Universal Time)
---

# SCSS Naming Convention

As a Dev team we have decided that as our team grows, it would be a good idea to stick to one naming convention for SCSS, so that we can quickly look at each other's code and understand what is going on.

We use our own variation of BEM that we like to call 'CBEM' where we use BEM and then put separate sections in a **C**ontainer. There is usually only 1 container per web page body, it is used to avoid styles accidentally affecting other pages and to generally keep things organized and easier to read. You can learn more about BEM [<u>here</u>](https://css-tricks.com/bem-101/)<u>.</u>

# C**BEM**

**C** → .container

**B** → .block

**E** → \_\_element

**M** → --modifier

```css
.container .block__element--modifier {
}
```

!! **Note:** Depending on the case, you do not always have to use the container, especially if the block repeats itself over multiple pages.

## Below is how your **SCSS** should look:

```css
.container {
  color: pink;

  .block {
    // notice how the block does not use '&'
    color: yellow;

    &__element {
      color: green;

      &--modifier {
        color: blue;
      }
    }
  }
}
```

!! **Important: **Pay attention to the '**&**' symbol, read more about how it works [<u>here</u>](https://css-tricks.com/the-sass-ampersand/). There should be no space between the & and the underscores or dashes.

!! **Note: **The & symbol makes it so that the 2 lines are put together as one class. So this means that:
!! <sub>SCSS </sub> <sub>CSS</sub>
!! <mark>\*\* **</mark><mark> .</mark><mark>_block { _</mark><mark>**\_ _\*\*</mark>_ _will compile as: <mark> </mark><mark>_.block**element { _</mark>
!! <mark>_** &**_</mark>_<mark>**element { } </mark>_\*\*_ _\*\*<mark>_ } _</mark>
!! _<mark> } </mark>_\*\*_<mark> </mark>\_\*\*

## Based on the above example, this is how your compiled** CSS **should look:

```css
.container {
  color: pink;
}

.container .block {
  color: yellow;
}

.container .block__element {
  color: green;
}

.container .block__element--modifier {
  color: blue;
}
```

And your HTML can have something like this:

    <div class="container">
        <div class="block">
            <div class="block__element"></div>
            <div class="block__element--modifier"></div>
        </div>
    </div>

**This is just a starting point, a guideline. You do not have to follow this exactly. **

For example, you can put a block inside a block, and an element inside an element, there is no problem with that, I do that all the time, just use common sense to see what looks good to you. The whole point of the naming convention is so that we can easily read and understand what is going on in your code.

# Examples

**SCSS (how you would write it)**

![image.png](media_SCSS%20Naming%20Convention/image.png)

**Compiled CSS of the example above**

![image.png](media_SCSS%20Naming%20Convention/63887b9b-3abe-4056-9dba-2d25401ee9d0_image.png)

          
