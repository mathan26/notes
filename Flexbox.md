    

## display: flex;

 - Adding display: flex to an element turns it into a flex container.
 - **Note:** Not the inner child, if we want select the child then select that and apply.

`

## flex-direction`

    row, column, row-reverse and column-reverse.

 - This makes it possible to align any children of that element into rows or columns.
 - **Note:** The default value for the flex-direction property is row.

## **`justify-content`**

**`center`** 

 - which aligns all the flex items to the center inside the flex
   container.

    

 **`flex-start`**
 - aligns items to the start of the flex container.

    
**`flex-end`**
 - aligns items to the end of the flex container.

    
**`space-between`** 
 - aligns items to the center of the main axis, with extra space
   placed between the items. The first and last items are pushed to the
   very edge of the flex container.

**`space-around`**
   

 - similar to space-between but the first and last items are not locked to the edges of the container, the space is distributed around all the items with a half space on either end of the flex container.

**`space-evenly`**

 - Distributes space evenly between the flex items with a full space at either end of the flex container

## `align-items`

 - **Note:** Push the content Opposite direction of flex direction.
 - Flex containers also have a cross axis which is the opposite of the main axis. For rows, the cross axis is vertical and for columns, the cross axis is horizontal.
 

**`flex-start`**

**`flex-end`**

  **`center`**
  
 **`stretch`**
 
 **`baseline`**


## flex-wrap

    

 1. This means extra items move into a new row or column. The break point of where the wrapping happens depends on the size of the items and the size of the container.
 2. **`nowrap:`** this is the default setting, and does not wrap items.
 3. **`wrap:`** wraps items from left-to-right if they are in a row, or top-to-bottom if they are in a column.
 4. **`wrap-reverse:`** wraps items from right-to-left if they are in a row, or bottom-to-top if they are in a column.

## flex-shrink

 - The flex-shrink property takes numbers as values. The higher the number, the more it will shrink compared to the other items in the container. 
 - For example, if one item has a flex-shrink value of 1 and the other has a flex-shrink value of 3, the one with the value of 3 will shrink three times as much as the other.

## flex-grow

 - The opposite of flex-shrink is the flex-grow property. Recall that flex-shrink controls the size of the items when the container shrinks. 
 - The flex-grow property controls the size of items when the parent container expands.
## flex-basis
 - The flex-basis property specifies the initial size of the item before
   CSS makes adjustments with flex-shrink or flex-grow.
## flex
 - There is a shortcut available to set several flex properties at once. The flex-grow, flex-shrink, and flex-basis properties can all be set together by using the flex property.
 - For example, flex: 1 0 10px; will set the item to flex-grow: 1;, flex-shrink: 0;, and flex-basis: 10px;
 - **NOTE:** The default property settings are flex: 0 1 auto;.
## order
 - The order property is used to tell CSS the order of how flex items appear in the flex container. 
 - By default, items will appear in the same order they come in the source HTML. 
 - The property takes numbers as values, and negative numbers can be used.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyMTU5NTkyNzldfQ==
-->