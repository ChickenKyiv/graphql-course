
<img data-src="img/flex-container.png" style="width:80%;" />

<img data-src="img/flex-children.png" style="width:80%;" />
 This defines a flex container; inline or block depending on the given value. It enables a flex context for all its direct children.




<img data-src="img/flex-direction-row.png" style="width:80%;" />
 This establishes the main-axis, thus defining the direction flex items are placed in the flex container. Flexbox is (aside from optional wrapping) a single-direction layout concept. Think of flex items as primarily laying out either in horizontal rows or vertical columns.



<img data-src="img/flex-wrap.png" style="width:80%;" />
 By default, flex items will all try to fit onto one line. You can change that and allow the items to wrap as needed with this property.



<img data-src="img/flex-justify.png" style="width:80%;" />
 This defines the alignment along the main axis. It helps distribute extra free space left over when either all the flex items on a line are inflexible, or are flexible but have reached their maximum size.



<img data-src="img/flex-align-items.png" style="width:80%;" />
 This defines the default behaviour for how flex items are laid out along the cross axis on the current line. Think of it as the justify-content version for the cross-axis (perpendicular to the main-axis).



img(src="images/flex-align-content.png")

 This aligns a flex container's lines within when there is extra space in the cross-axis, similar to how justify-content aligns individual items within the main-axis.



--------------
Order

<img data-src="img/flex-order.png" style="width:80%;" />
p By default, flex items are laid out in the source order. However, the order property controls the order in which they appear in the flex container.

Flex grow

<img data-src="img/flex-grow.png" style="width:80%;" />
 This defines the ability for a flex item to grow if necessary. It accepts a unitless value that serves as a proportion. It dictates what amount of the available space inside the flex container the item should take up.

Flex shrink

<img data-src="img/flex-grow.png" style="width:80%;" />
 This defines the ability for a flex item to shrink if necessary.

Flex basis

<img data-src="img/flex-grow.png" style="width:80%;" />
 This defines the default size of an element before the remaining space is distributed. It can be a length (e.g. 20%, 5rem, etc.) or a keyword.

Align self

<img data-src="img/flex-align-self.png" style="width:80%;" />
 This allows the default alignment (or the one specified by align-items) to be overridden for individual flex items.
