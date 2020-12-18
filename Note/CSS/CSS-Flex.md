

1. 块级格式上下文中margin-top和margin-bottom的值如果是auto,则它们的值都为0
2. flex格式上下文中,通过justify-content和align-self进行对其之前,任何处于空闲的空间都会分配到该方向的自动margin中去
3. 使用了自动margin的flex子项目,它们的父元素设置的justify-content以及它们本身的align-self将不再生效

4. 设置flex布局以后,子元素的float、clear和vertical-align属性将失效

   容器属性：flex-direction, flex-warp, flex-flow, justify-content, align-items, align-content(多根轴线对齐方式)
   项目属性：order, flex-grow, flex-shrink, flex-basis, flex, align-self 
   