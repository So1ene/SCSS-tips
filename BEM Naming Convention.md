# BEM Naming Convention in SCSS

It's good idea to stick to one naming convention for SCSS, so that we can quickly look at the code and understand what is going on and exactly where to find things.

This variation of BEM that I like to call 'CBEM' where we use BEM and then put separate sections in a **C**ontainer. There is usually only 1 container per web page body or large section, it is used to avoid styles accidentally affecting other pages/sections and to generally keep things organized and easier to read. You can learn more about BEM [<u>here</u>](https://css-tricks.com/bem-101/)<u>.</u>

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

The & symbol makes it so that the 2 lines are put together as one class. So this means that:
```css
   SCSS:                                                     CSS:
   
  .block  {                            will compile as:      .block__element {
       &__element  {  }                                        }
  }
```

## Based on the above example, this is how the above SCSS compiles:

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

### This is just a starting point, a guideline. You do not have to follow this exactly.

For example, you can put a block inside a block, and an element inside an element, there is no problem with that, I do that all the time, just use common sense to see what looks good to you. The whole point of the naming convention is so that we can easily read and understand what is going on in your code.

# Examples

**SCSS (how you would write it)**

![image (1).png](<./assets/image (1).png>)

**Compiled CSS of the example above**

![image.png](<./assets/image.png>)

**Example usage in html**

![image.png](<./assets/Screenshot_3.jpg>)


<br />

<br />

- Also checkout my guide on [Breakpoints Mixins](<./Breakpoint Mixins.md>)

          
