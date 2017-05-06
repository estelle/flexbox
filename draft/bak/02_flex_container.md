
# Flex Container

In the previous chapter we learned how to use `display` property values `flex` and `inline-flex` to instantiate a flex container and turn the container's children into flex items. We now understand how `flex-direction` sets the direction of the flex items within the flex container, setting the _main-axis_, _main-axis_ direction and _cross-axis_ and how `flex-wrap` can be used to enable multi-line flex containers and to invert the _cross-axis_ direction. We also know how to use `flex-flow` to set both `flex-direction` and `flex-wrap`. 

We learned how to use `flex-flow` properties to handle multiline flex containers, but we haven't really discussed what happens to the extra space when the flex items don't fill a row or column, and what happens to the extra space when not all the flex items have the same cross dimension. 

Thus far in our examples, when the flex items did not fill the flex container, the flex items have been grouped towards the _main-start_ on the _main-axis_. We can control that. Flex items can be flush against the _main-end_ instead. They can be centered. We can even space the flex items out evenly across the _main-axis_. 

The flex layout specification provides us with flex container properties to control the distribution of space: in addition to `display` and `flex-flow`, the CSS Flexible Box Layout Module Level 1 properties applied to flex containers include the `justify-content`, `align-content` and `align-items` properties. 

The `justify-content` property controls how flex items in a flex line are distributed along the _main-axis_. The `align-content` defines how flex lines are distributed along the cross axis of the flex container. The `align-items` property defines how the flex items are distributed along the cross axis of each of those flex lines.

The properties applied to individual flex items are discussed in the next chapter.

### The `justify-content` property

The `justify-content` property enables us to define how flex items will be distributed along the _main-axis_ of the flex container. 

---

`justify-content`

 **Values:**

flex-start | flex-end | center | space-between | space-around

 **Initial value:**

flex-start 

 **Applies to:**

 flex containers

 **Inherited:**

No

 **Percentages:**

not applicable

 **Animatable:**

No

---


The distribution of elements along the main axis of the container is controlled with the `justify-content` property. If you remember from [figure ?](img/display_flex.png from last chapter), when an element is converted to a flex container, the flex items, by default, were grouped together at the _main-start_. 

The `justify-content` defines how space is distributed. There are five values for the `justify-content` property including `flex-start`, the default value, and `flex-end`, `center`, `space-between`, and `space-around`. 

![Figure ?: The five values of the `justify-content` property](img/2/07_justify_content_abc.png) [::LINK::](http://localhost/flexfiles/_07justify_content.html)

As shown in [figure ?](07_justify_content_abc.png figure above), by default, or with `justify-content: flex-start` explicitly set, flex items are laid out flush against _main-start_.  With `flex-end`, flex items are justified toward _main-end_. `center` groups the items flush against each other centered in the middle of the _main-dimension_ along the _main axis_. The `space-between` value puts the first flex item on a flex line flush with _main-start_ and the last flex item in each flex line flush with _main-end_, and then puts an equal amount of space between every pair of adjacent flex items. `space-around` evenly distributes the flex items, as if there were non-collapsing margins of equal size around each item. Examples of the five `justify-content` values are demonstrated in Figure ?.

As the `justify-content` property is applied to the flex container, the flex items will be distributed in the same manner whether they're on a filled first flex line or on a partially filled subsequent flex line in a wrapping flex container.

Those are the basics of `justify-content` property. But, of course, there's more to the property and each of the values. What happens if there is only one flex item on a line? If the writing mode is right to left? If `flex-flow: nowrap` is set and the flex items overflow the flex container?


![Figure ?: The overflow direction in a single line flex container depends on the value of the `justify-content` property](img/2/08_justify_content_nowrap.png)[::LINK::](http://localhost/flexfiles/08_justify_content_6elem_column.html)<!--(img/2/08_justify_content_overflow_column_reverse.png)-->


If `nowrap` is set, and the items overflow the line, the `justify-content` property helps control the appearance of the line overflow. [Figure ?](img/2/08_justify_content_nowrap.png) illustrates what happens with the different `justify-content` when `flex-flow: column nowrap` is set, and the flex items heights is taller than the container's main dimension. Let's take a look at the five values.

![Figure ?: Impact of setting `justify-content: flex-start;`](img/2/09_justifyconent_flexstart.png)[::LINK::](http://localhost/flexfiles/09_justify_content.html)

Setting `justify-content: flex-start`  explicitly sets the default behavior of grouping the flex items toward _main-start_, placing the first flex item of each flex line flush against the _main-start_ side. Each subsequent flex item then gets placed flush with the preceding flex item's _main-end_ side, until the end of the flex line is reached if wrapping is set. The location of the _main-start_ side depends on the flex direction and writing mode, which is explained in [Understanding Axis](link to "Understanding Axis" in previous chapter).   If there isn't enough room for all the items, and `nowrap` is the default or expressly set, the items will overflow on the _main-end_ edge, as shown in the third examples of figure ? and the next four images.

![Figure ?: Impact of setting `justify-content: flex-end;`](img/2/09_justifyconent_flexend.png)

Setting `justify-content: flex-end` puts the last flex on a line flush against the _main-end_ with each preceding flex item being placed flush with the subsequent item. In this case, if the items aren't allowed to wrap, and if there isn't enough room for all the items, the items will overflow on the _main-start_ edge, as shown in the third example of Figure ?. Any extra space on a flex line will be on the _main-start_ side.

![Figure ?: Impact of setting `justify-content: center;`](img/2/09_justifyconent_center.png)

Setting `justify-content: center` will pack all the items together, with their _main-axis_ side placed flush against each other like they were with `flex-start` and `flex-end`, but the group of flex items will be packed flush against each other at the center of each flex line instead of at the _main-start_ or _main-end_. If there isn't enough room for all the items and they aren't allowed to wrap, the items will overflow evenly on both the _main-start_ and _main-end_ edges. If the flex items wrap onto multiple lines, each line will have centered flex items, with extra space being on the _main-start_ and _main-end_ edges. 

![Figure ?: Impact of setting `justify-content: space-between;`](img/2/09_justifyconent_spacebetween.png)

Setting `justify-content: space-between` puts the first flex item flush with _main-start_ and the last flex item on the line flush with _main-end_, and then puts an even amount of space around each flex item, until the flex line is filled. Then it repeats the process with any flex items that are wrapped onto additional flex lines.  If there are 3 flex items, there will be the same amount of space between item 1 and 2 and between 2 and 3, but there will be no extra empty space between the edges of the container and items 1 or 3, as shown in the second example in figure ?. With `space-between`, the first item is flush with _main-start_, which is important to remember when you only have one flex item or when your flex items overflow the flex container in a `nowrap` scenario. This means, if there is only one flex item, it will be flush with _main-start_, not centered, which seems counter-intuitive to many at first. 

> With `justify-content: space-between`, the first flex item is placed flush with _main-start_, so, if there is only one item, or if the flex items aren't allowed to wrap and overflow the flex container, the appearance will be the same as `flex-start` -- the comparison can be seen in [figure ?](img/2/08_justify_content_nowrap.png) -- which may be less than intuitive. 

With `justify-content: space-between` the space between any two items on a flex line will be the same, but won't necessarily be the same across flex lines. When set the allow wrapping, on the last flex line, the first flex item of that last line is flush against _main-start_, the last if there are two or more on that line will be against _main-end_, with equal space between adjacent pairs of flex items. As shown in the last example of figure ?, A and G, the first items on each flex line, are flush against _main-start_. F and I, the last items on each line, are flush against _main-end_. The flex items are evenly distributed with the spacing between any two adjacent items being the same on each of the lines, but the space between flex items on the first line is narrower than the space between flex items on the second line. 

![Figure ?: Impact of setting `justify-content: space-around;`](img/2/09_justifyconent_spacearound.png)

Setting `justify-content: space-around` evenly distributes the extra space on the line around each of the flex items, as if there were non-collapsing margins of equal size around each element on the _main-dimension_ sides. So there will be twice as much space between the first and second item as there is between _main-start_ and the first item and _main-end_ and the last item, as shown in figure ?.

If `nowrap` is set, and there isn't enough room on the flex container's _main-direction_ for all the flex items, the flex items will overflow equally on both sides, similar to setting `center`, as shown in the third example in figure [figure ?](img/2/08_justify_content_nowrap.png).

If the flex items wrap onto multiple lines, the space around each flex item is based on the available space on each flex line. While the space around each element on a flex line with be the same, it might differ between lines, as shown in the last examples in figure ?. The spaces between A and B and between G and H are twice the width of the spaces between the _main-start_ edge and A and the edge and G.

With the margin added to the flex items to make the examples less hideous, this may be hard to tell. Comparing margin free examples of `center`, `space-around` and `space-between` might be more helpful:

![Figure ?: Comparing `center`, `space-around` and `space-between`](img/2/10_compare_justifycontent.png)

Figure ? demonstrates the difference between the spacing concepts of `center`, `space-around` and `space-between`. When set to `center`, the flex items are grouped flush against each other in the center of the _main-dimension_. 

With `space-between`, you'll note that on the first and last flex items on both flex lines abut _main-start_ and _main-end_ respectively. The space between each of the flex items on the first flex line is 24px: the 120px of free space is divided into 5 equal gaps placed between the 6 flex items. The space between each flex item on the second flex line is 150px: the 300px of free space is divided into two and placed between the three flex items. 

With `space-around`, the flex items do not necessarily abut the edges: if there is any extra space, it is put around every flex item. Just like in the other two examples, there are 120px of free space and 6 items on the first line and  300px of free space and 3 flex items on the second flex line. On the first line, the 120px of free space are divided among the two sides of the six items, placing 10px on the left and right of each item. This way, there are 10px of space between _main-start_ and the first item and the last item and _main-end_, and twice that, or 20px, between each adjacent flex item. On the second flex line, the 300px of free space is divided between the two sides of the 3 flex items, putting 50px on the outer edges and twice that, or 100px, between adjacent items.  

![The five values of `justify-content` property when `flex-direction: column-reverse` is set and flex items overflow the flex container](img/2/08_justify_content_overflow_column_reverse.png) 

It may also help to compare the overflow edge and edges of the five `justify-content` properties with a different _main-axis_. In figure ?, all flex containers have the following CSS:

    container { 
      display: inline-flex; 
      flex-flow: nowrap column-reverse; 
      height: 200px;
    } 

The layout when there is negative free space should now be more intuitive: 

* `flex-start` and `space-between` overflow at _main-end_
* `flex-end` overflows at _main-start_
* `center` and `space-around` overflow on both ends

With `justify-content: space-between`,  the first flex item is placed flush with _main-start_. If the flex items don't fit on a line within the flex container, they will overflow on the _main-end_ side, as shown in figure ?. With `justify-content: space-around` is if there is only one flex item on a line, or more items than a non-wrapping flex line can hold, it will be centered. If there are multiple items, the outer spaces are half the size of the spaces between adjacent item. 

In our examples, we've also prevented the flex items from shrinking, a default feature we haven't yet covered. The `height: 200px` limited the height of the container ensuring the flex items could overflow their container. The `display: inline-flex` declaration provided for a flex container that was only as wide as its content. Had we included `wrap` instead of `nowrap`, the container would have doubled in width, allowing for 2 columns or flex lines.

#### `justify-content` examples 


We took advantage of the default value in [Figure ?](img/1/01_nav_tabbednavigation_flex.png), creating a left aligned navigation bar. By changing the default value to `justify-content: flex-end;` we can right align the navigation bar, as shown in figure ?.

![Figure ?: Right and left aligned navigation in LTR and RTL languages using `justify-content`](img/2/07_justify_content_nav.png)[::LINK::](http://localhost/flexfiles/07_nav_displayflex.html)

For right to left writing modes we don't have to alter the CSS. As shown in figure ?, and as discussed in the previous chapter, flex items are grouped toward _main-start_. In English, _main-start_ is on the left. In Hebrew, _main-start_ is on the right.

By simply adding a single line to our CSS, we altered the appearance of our navigation example, making the English version flush to the right and the Hebrew translation flush to the left:

    nav {
      display: flex;
      justify-content: flex-end;
      border-bottom: 1px solid #ccc;
    }

We could have centered that navigation:

    nav {
      display: flex;
      justify-content: center;
      border-bottom: 1px solid #ccc;
    }

![Changing the layout with one property value pair](img/2/07_justify_content_nav_center.png)[::LINK::](http://localhost/flexfiles/07_nav_displayflex_center.html)














































### The `align-items` property

Whereas the `justify-content` defines how flex items are aligned along the flex container's _main-axis_, the `align-items` property defines how flex items are aligned along its flex line's _cross-axis_.

---

`align-items`

 **Values:**

flex-start | flex-end | center | baseline | stretch

 **Initial value:**

stretch 

 **Applies to:**

 flex containers

 **Inherited:**

No

 ** Percentages:**

not applicable

 **Animatable:**

No

---

With the `align-items` property, you can align flex items to the start, end or center of the _cross-axis_ of their flex line.  Set on the container element, `align-items` is similar to `justify-content` but in the perpendicular direction, setting the _cross-axis_ alignment for all flex items, including anonymouse flex items, within the flex container (we'll learn how to override this value for individual flex items when we cover [`align-self`](link to align self in the next chapter)).  With `align-items` you can set all the items to have their _cross-axis_ flush against the _cross-start_ or _cross-end_ of their flex line, or stretched flush to both. Or you can center all the flex items in the middle of the flex line. Stretched across the entire _cross-axis_ is the default and is what we have seen in most of the examples thus far. There are five values, including `flex-start`, `flex-end`, `center`, `baseline`, and the default `stretch`, as shown in image ?.

![Figure ?: The five values of the `align-items` property when you have a single row of flex items and single column of flex items](img/2/11_alignitems_singleline.png) [::LINK::](http://localhost/flexfiles/11_alignitems_column.html) [::LINK::](http://localhost/flexfiles/11_alignitems.html)

> While `align-items` sets the alignment for all the flex items within a container, the [`align-self` property](link to align-self) enables overriding the alignment for individual flex items.

In figure ? you'll note how the flex items either hug the _cross-start_ or _cross-end_ side of the flex container, are centered, or stretch to hug both, with the possible exception of `baseline`. 

The general idea is `flex-start` places the flex items on the _cross-start_, `flex-end` puts them on the _cross-end_ edge, `center` centers them on the _cross-axis_, the default `stretch` stretches the flex item from _cross-start_ to _cross-end_, and `baseline` looks similar to `flex-start` but actually lines up the baselines of the flex items and then pushes the group of flex items toward _cross-start_. 

With `baseline`, the flex items baselines are aligned: the flex item that has the greatest distance between its baseline and its `cross-start` side will be flush against the cross-start edge of the line. That's the general idea -- and explains non-wrapping flex containtainers pretty well -- but there's more to it then that. 

In the multi-line `align-items` figures that follow, the following code has been included: 

    flex-container {
      display: inline-flex;
      flex-flow: row wrap;
      border: 1px dashed;
      padding: 10px;
    }
    flex-item {
      border: 1px solid;
      margin: 0 10px;
    }
    .C, .H {
      margin-top: 10px;
    }
    .D, .I {
      margin-top: 20px;
    }
    .J {
      font-size: 3rem;
    }

The red line is _cross-start_ and the blue is _cross-end_ for each flex line. The lines appear purple when a new flex line abuts the previous flex line. C, H, D and I have different values for top and bottom margins. We've added a bit of margin to the sides of all the flex items to make the figures more legible, which doesn't effect the impact of the `align-items` property. J has the font size increased, increasing the line height. This will come into play when we discuss the `baseline` value.

The default is `align-items: stretch`, as shown in figure ?.

### `align-items: stretch`

![Figure ?: `align-items: stretch`](img/2/13_alignitems_stretch.png)

The default and the explicitly set `align-items: stretch`, stretches all the stretchable flex items in a line to be as tall or wide as the tallest or widest flex item on the line. What does 'stretchable' mean? While by default all the flex items will stretch to take up 100% of the _cross-size_, if `min-height`, `min-width`, `max-height`, `max-width`, `width` or `height` are set, those properties will take precedence.

If set or defaulting to `stretch`, the flex items' _cross-start_ will be flush with the flex line's _cross-start_, and the flex items' _cross-end_ will be flush with the flex line's _cross-end_. The flex item with the largest _cross-size_ will remain it's default size, and the other flex items will stretch, growing to the size of that largest flex item. As demonstrated by items C, D, H and I, the _cross-size_ of the flex items include the margins. 

>![Figure ?: effect of cross-axis margins on `align-items` property](img/2/12_effect_of_margin_on_alignitems.png) [::LINK::](http://localhost/flexfiles/12_alignitems_margin.html)

>The margins in the _cross_ direction have an impact. In figure ?, we've added 30px of margin to the _cross-start_ edge of `C` of flex item and 40px to the the _cross-end_ edge of the `D`. You'll note `A`, `B`, and `E` are flush against both cross edges, but the `C` and `D` appear pushed in. This is due to the margins: their outer margins are flush against _cross-start_ and _cross-end_ .

The size of the stretched flex item includes the margins on the _cross-start_ and _cross-end_ sides: it is the outer edge of the flex items' margin that will be flush with _cross-start_ and _cross-end_. This is the reason C, D, H and I may appear smaller than the other flex items on their flex lines. They're not. The outer edge of the top and bottom margins are flush with the _cross-start_ and _cross-end_ of the flex lines they occupy. Those flex lines are, in turn, as tall as the tallest item on the line (or as wide as the widest item when the _cross-dimension_ is horizontal).

Flex lines are only as tall as they need to be to contain their flex containers. In the five `align-items` figures, the first line, which includes E, is much taller than the last line, which includes only K. K has only one line of text, and no margin, whereas E has 5 lines of text. The second line, which includes F with 6 lines of text, is even taller than the first line. The line height of the flex line containing only K is much smaller than the line containing E, which is smaller than the line containing F. 

### `align-items: flex-start`

![`align-items: flex-start`](img/2/13_alignitems_flexstart.png)

The `flex-start` value lines up each flex items' _cross-start_ edge flush against the _cross-start_ edge of their flex line. The flex item's _cross-start_ edge is on the outside of the margin: if a flex item has a margin that is greater than 0, flex item will not appear flush with the flex line's _cross-start_ edge, as seen in flex item C, D, H, and I, in figure ?. If there is only one line of flex items, this will generally be the _cross-start_ edge of the container, inside the padding, if any.

### `align-items: flex-end` 

![`align-items: flex-end`](img/2/13_alignitems_flexend.png)

Setting `align-items: flex-end` will align the _cross-end_ edge of all the flex items along the _cross-end_ edge of the line they are in as shown in figure ?. In these examples, none of the flex items have a bottom margin greater than 0px, so unlike our other examples, this example does not look jagged.

### `align-items: center`

![`align-items: flex-center`](img/2/13_alignitems_center.png)

Setting `align-items: center` will center the flex items' _cross-size_ along the middle point of the _cross-axis_ of the line. The center is the midpoint between the outer edges of the margin, remembering flex item margins do not collapse. Because the cross-edge margins for C, D, H and I are not symmetrical, the flex items do not appear centered along the _cross-axis_, even though they are. In LTR and RTL languages, in the case of `flex-direction: row` and `row-reverse`, the midpoint is the midpoint of the top margin, top border, and top-padding, content or height, and bottom padding, bottom border and bottom margin. For `flex-direction: column` and `column-reverse`, the midpoint is the midpoint of the left margin, left border, and left-padding, content or width, and right padding, right border and right margin.

> Flex items may overflow flex container along in the _main-axis_ if `nowrap` is set and the _main-size_ is constrained. Similarly, if the flex container’s _cross-size_ is constrained, the contents  may overflow the flex container's _cross-start_ and/or _cross-end_ edge. The direction of the overflow is not determined by the `align-items` property, but rather by the `align-content` property, discussed next. The `align-items` aligns the flex items within the flex line and does not directly impact the overflow direction of the flex items within in the container.

### `align-items: baseline`


![`align-items: baseline`](img/2/13_alignitems_baseline.png) [::LINK::](13_align_items.html)

The `baseline` value may be a little more confusing. With `baseline`, the flex items in each line are all aligned at their baselines, which is basically the bottom of the first line of text, if there is any. The flex item on each flex line with the biggest distance between its baseline and its _cross-start_ margin edge is placed flush against the _cross-start_ edge of the line, with all other flex items' baseline lined up with the baseline of that flex item.

In many implementations, `baseline` will look like `flex-start`, but will differ from the `flex-start` value if the flex items have different margins, padding or border on the _cross-start_ side or if the first lines of content of the flex items don't all have the same line heights. Instead of lining the _cross-start_ of each flex item flush against the _cross-start_ of each line, the flex items aligned so their baselines align.

You'll notice that A, B, C, D, and E all seem aligned at top. What you may have missed is that they are not flush to the top - they are not flush against the red line. D has a top margin of 20px. The outer edge of D's top margin is flush against the _cross-start_ of the flex line, which is flush with the top of the flex container. The distance between the _cross-start_ line and baseline is determined by the item on the line that has the biggest distance between its outer margin on its _cross-start_ side and its baseline. In the baseline example of figure ?, it's D, J and K. These items' outer margins on the cross start side are placed flush against the _cross-start_ edge of their respective lines, and the other items in the same flex lines have their baseline lined up with D, J and K's baseline. 

As A, B, C, D and E all have the same line height, and D has the tallest top margin, they are aligned with D's baseline, and D's top margin is flush against the _cross-start_ edge. When it comes to the first line, because they all have the same line height, border and padding, it looks like they're lined up like `flex-start`, but they are actually a little lower, accommodating for D's top margin. The green line denotes where the baseline is.  

In all the examples, we increased the font size for J to `3rem` to create a flex item that had a different baseline from all the other flex items. Only when `align-items: baseline` is set does this impact the flex item alignment within the flex line, as shown in figure ?. When `align-items: baseline` is set, the baselines of all the items in the second flex line are aligned with Js baseline, as J is the flex item with the greatest space between the outer top margin and the bottom of the first line of text. Again, the green line denotes the approximate location of the baseline. 

### additional notes

The `align-items` property is set on the flex container and impacts all of the flex items within that flex container. If you want to change the alignment of one or more flex items, but not all, you can include the `align-self` property on the flex items you would like to align differently. The `align-self` takes the same values as `align-items`, and is discussed in the next chapter. 

You can not override the alignment for anonymous flex items (non-empty text node children of flex containers): their `align-self` always matches the value of `align-items` of their parent flex container.

In the `align-items` examples, the flex container's _cross-size_ was as tall as it needed to be. No `height` was declared on the container, so it defaulted to `height: auto`. Because of this, the flex box grew to fit the content. Had the _cross-size_, in this case the height, been set to a specific size, there may have been been extra space, or not enough space, to fit the content. Flex box allows us to control the alignment of flex lines with the `align-content` property. The `align-content` property is the last property we need to focus on that applies to the flex container (versus the flex items). The `align-items` property only impacts flex line alignment in multi-line flex containers.
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
## The `align-content` property

The `align-content` property aligns a flex container’s lines within a flex container that has extra space in the _cross-axis_ direction.

---

`align-content`

 **Values:**

flex-start | flex-end | center | space-between | space-around | stretch

 **Initial value:**

stretch 

 **Applies to:**

 multi-line flex containers

 **Inherited:**

No

 ** Percentages:**

not applicable

 **Animatable:**

No

---

The `align-content` property allows us to dictate how any extra _cross-direction_ space in a flex container is distributed between and around flex lines. This is different from `align-items` above with dictates flex item positioning within each flex line. 
 
The `align-content` property determines how flex lines are aligned within a multi-line flex container. When there is extra space in the _cross-axis_ direction, you can dictate whether the lines are grouped at _cross-start_, _cross-end_, centered, or stretched to take up all the available space, or distributed across the flex container with the extra space distributed between or around the flex lines.

Think of `align-content` as similar to how `justify-content` aligns individual items along the _main-axis_ of the flex container, but for flex lines across the _cross-axis_ of the container. This property only applies to multi line flex containers, having no effect on non-wrapping and otherwise single line flex containers. 

![Values of flex container's `align-content` property](img/2/14_aligncontent_all.png) [::LINK::](/flexfiles/14_aligncontent.html)

Figure ? demonstrates the six possible values of the `align-content` property. We've used the following CSS as the base for the six examples above:

    flex-container {
      display: flex;
      flex-flow: row wrap;
      align-items: flex-start;
      border: 1px dashed;
      height: 480px;
    }

### Distribution of extra space

In figure ?, each flex container has three flex lines. With a height of 480px, the flex container is taller than the default combined heights of the three flex lines.  The tallest items in each line - E, F and K - are 150px, 180px and 30px respectively, for a combined total of 360px. Each flex container has an extra 120px of free space in the _cross-size_ direction. The _cross-start_ side of each flex line is denoted with a red line, the _cross-end_ side with a blue line, appearing purple when they overlap. With 5 of the `align-items` values, the free space is distributed outside of the flex lines, as is more apparent in [Figure ?](img/2/14_aligncontent_distribution_of_space.png). With `stretch`, the extra space is evenly distributed between all the flex lines, increasing their cross size. 

![Figure ?: The distribution of extra space for the different values of `align-content`](img/2/14_aligncontent_distribution_of_space.png) [::LINK::](flexfiles/14_aligncontent_stretch.html)

Figure ? reiterates the six possible values of the `align-content` property, with `align-items: stretch` and `flow: 1;` set to allow the flex items to grow to take up their entire lines to make the impact of the `align-content` values more apparent (and generally, to be less of an eyesore):

    flex-container {
      display: flex;
      flex-flow: row wrap;
      **align-items: stretch;**
      border: 1px dashed;
      height: 480px;
    }
    flex-items {
      flow: 1;
    }

Just like the previous example, with a height of 480px, and with flex lines 150px, 180px, and 30px tall, we have 120px of free space along the _cross-direction_ distributed differently depending on the value of the `align-content` property:

    480 - (150 + 180 + 30) = 120

As shown in the first examples in both Figure ? and Figure ?, with `flex-start` the 120px is on the _cross-end_ side. With `flex-end` the extra 120px of available space are at the _cross-start_ side. With `center`, the lines are centered, with 60px of extra space at both the _cross-start_ and _cross-end_ sides, as shown in the top right example of both figures. With `space-between`, there is 60px between adjacent pairs of flex lines, as shown in the bottom left examples. With `space-around`, the space is evenly distributed around each line: the 120px is distributed evenly putting 20px of non-collapsed space on the _cross-start_ and _cross-end_ sides of each flex line, so there are 20px of extra space at the _cross-start_ and _cross-end_ sides of the flex container, and 40px of space between adjacent flex lines.  

The `stretch` value is different: with `stretch` the lines stretch with the extra space evenly distributed among the flex lines rather than between them. In this case, 40px was added to each of the flex lines. You'll note in the sixth example in both figure ? and figure ?, there is no area within the container that is not occupied by a flex line. Stretch is the default value, as you likely want to fill all the available space.

If there isn't enough room for all the lines, they will overflow at _cross-start_, _cross-end_, or both, depending on the value of the `align-content` property, as shown in figure ?.

![Appearance of `align-content` property when lines are overflowing the container](img/2/14_aligncontent_overflowing.png)

Figure ? shows the size `align-content` values when the flex lines overflow their parent flex container. The only difference in the CSS between this and [figure ?](figure # img/2/14_aligncontent_all.png from /flexfiles/14_aligncontent.html) is the height of the flex container. We defined `height: 240px` to create flex containers not tall enough to encompass all their child flex items:

    flex-container {
      display: flex;
      flex-flow: row wrap;
      align-items: flex-start;
      border: 1px dashed;
      **height: 240px;**
    }

If the flex lines overflow the flex container, `flex-start`, `space-between` and `stretch` overflow the _cross-end_ side, `stretch` and `center` overflow evenly both the _cross-end_ and _cross-start_ sides, and only `flex-end` overflows the _cross-start_ side.

#### `align-content: flex-start`

With `align-content: flex-start`, the _cross-start_ edge of the first line of flex items will be flush against _cross-start_, with each subsequent line placed flush against the preceding line, as shown in figure ?. In other words, all the flex lines will be grouped together at the _cross-start_ edge of the flex container. Note all the extra space (the extra 120px in this case) is at _cross-end_. Remembering the _cross-direction_ is inverted with [`flex-direction wrap-reverse`](link to flex-direction in chapter 1), as shown in figure ?. If there isn't enough room for all the lines, they will overflow at _cross-end_.

![Figure ?: Remember, `wrap-reverse` inverts the cross-direction. With flex-start, the excess space or overflowing lines, if any, is always at _cross-end_](img/2/14_aligncontent_flexstart.png) [::LINK::](15_aligncontent_start.html)

#### `align-content: flex-end`

With `align-content: flex-end`, the _cross-end_ edge of the last line of flex items is placed flush with the _cross-end_ edge of the flex container, and each preceding line is placed flush with the subsequent line, leaving all the extra white space at _cross-start_. In other words, all the flex lines will be grouped flush against the _cross-end_ edge of the flex container. Should the content overflow the flex container, it will do so on _cross-start_ side.

#### `align-content: center`

Declaring `align-content: center` groups the flex lines together, so they are flush against each other, just like they are grouped together with `flex-start` and `flex-end`, but in the center of the flex container. 

`center`, `flex-start` and `flex-end` all have each line's _cross-end_ being flush against the subsequent line's _cross-start_. Instead of all the lines being grouped at the container _cross-start_ as in `flex-start` or at _cross-end_ as in `flex-end`, with `align-content: center` the group of lines is centered between the flex container's _cross-start_ and _cross-end_, with equal amounts of empty space -- 60px on each side in this case -- between the _cross-start_ edge of the flex container and the cross start edge of the first flex line, and between the _cross-end_ edge of the flex container and the _cross-end_ edge of the last flex line, as shown in the top right example in figure ?. If the flex items overflow the flex container, the lines will overflow equally in both directions past the _cross-start_ and _cross-end_ edges of the container, as shown in the center left example in [figure ?](figure # for img/2/14_aligncontent_overflowing.png) .


#### `align-content: space-between`  

When `align-content: space-between` is set, the flex lines are evenly distributed in the flex container. The 'even distribution' is based on the available space, not the size of the lines. 

If we remember back to `justify-content: space-between`, the first flex item is flush against _main-start_. The second flex item, if there is one, is flush against main end. The rest of the flex items, if there are any, are spread out with equal amounts of the free space distributed between the flex items. This is similar to how `align-content: space-between` works. If there is more than one flex line, the first line will be flush against the container's _cross-start_, the last line will be flush against the container's _cross-end_ and the available extra space is distributed evenly between the additional lines, if there are any. The extra space is distributed evenly, not proportionally.  The space between any two flex lines within the flex container is equal: even if the _cross-sizes_ of the multiple flex lines differ. 

> Only flex containers with multiple lines can have free space in the _cross-axis_ for lines to be aligned in.  If there is only one line, the `align-content` property will not impact the distribution of the content. In flex containers with a single line of flex items, the lone line stretches to fill the space. 

The middle line, if there are an odd number of lines, is not necessarily centered, as the lines don't necessarily all have equivalent cross dimensions. Rather, the spacing between any two adjacent lines is the same: there is the same amount of space between the first and second line as there is between any other adjacent flex line, as shown in figure ?. In this case, we have 120px total of free space, which gets divided equally, with half, or 60px, between the first and second flex lines, and 60px between the second and third flex lines. 

    120px / 2 = 60px

If there isn't enough space to encompass all the flex lines, the free-space is negative and `align-content: space-between` appearance is identical to `flex-start`, with the overflow on the _cross-end_ side.  

#### `align-content: space around`

The `space-around` value distributes the lines of a multi-line flex box evenly, as if all the flex lines had equal, non-collapsing margins on both the _cross-start_ and _cross-end_ sides. Because there is an equal distribution of the extra available space around each line, the space between the edges of the container and the first and last flex lines is half the size of the distance between any two flex lines.  The distribution of the extra space is shown in figure ?. 

![Distribution of free space when `align-content: space-around` is set](images/align_content_space_around.tif) 

In this case we have 120px of free space distributed to three flex lines, with half of each flex lines extra space being added to the _cross-start_ edge and half being added to the _cross-end_ edge.

		(120px / 3 lines) / 2 sides = 20px per side

In this example, there is 20px on the outer sides of the flex lines, with twice that between any two adjacent flex lines. There is 20px between the _cross-start_ edge and the first line, 20px between the _cross-end_ edge and the last line, and 40px (twice 20px) between the first and second flex lines and the second and third flex lines.

If there isn't enough room for the flex lines and they overflow the flex container, the free-space is negative and `align-content: space-around` value is identical to `center`, with the overflow evenly distributed between the _cross-start_ and _cross-end_ sides. 

#### `align-content: stretch`

Omitting the `align-content` property, or setting it explicitly to the `align-content: stretch` default value, will makes the lines stretch to take up all the extra available space. 

If you take a close look at figure ?, you'll note that `stretch` and `space-between` are actually quite different. In `space-between`, the extra space is distributed **between** the lines. In `stretch`, the extra space is divided into the number of lines and added **to** the lines. The original lines were 150px, 180px and 30px tall respectively. When set to stretch, the extra 120px is added to the lines in equal amounts. As we have three flex lines and 120px of extra space, each flex line grows by 40px, giving us flex lines that are 190px, 220px and 70px respectively. 

![When set to stretch, the extra space is distributed equally, not proportionally, to each line.](images/align_content_stretch.tif) 

That extra space, in this example, is at the _cross-end_ of each individual line since we included `align-items: flex-start;`.  Had we used `align-items: flex-end;` instead, the extra space in each line would have been at the individual lines' flex start.

If there isn't enough space to fit all the flex lines, the lines will behave as if set to `flex-start`, with the first flex line flush against the _cross-start_ edge of the flex container. 


We have been taking a look at properties of the flex container. It's time to take a look at properties directly applied to flex items.