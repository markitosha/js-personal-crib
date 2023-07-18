# Browser rendering

### What is Browser Rendering

Browser rendering is the process by which a web browser translates code into a functional website. This process involves several steps that turn your code into what the user sees on their screen.

### Steps Involved in Browser Rendering

1. **Parsing**: The browser parses HTML markup into a Document Object Model (DOM) tree. This represents the hierarchical structure of the page's elements.

2. **CSSOM Tree**: The browser then parses CSS into a CSS Object Model (CSSOM) tree which represents the styles that will be applied to the DOM elements.

3. **Render Tree**: The browser combines the DOM and CSSOM into a render tree. This tree contains all visual elements in the order in which they will be displayed.

4. **Layout**: Next, the browser computes the layout, determining where each element goes on the screen. The position and size of each object are calculated relative to its siblings and parents.

5. **Painting**: The browser "paints" the render tree, filling in pixels for each node. This involves drawing out text, colors, images, borders, and more.

6. **Compositing**: Finally, the browser performs compositing where it layers all elements on the screen, especially those with certain CSS properties like `opacity` or `transform`.

## Reflow and Repaint Steps

**Reflow** refers to the process in which the browser recalculates the positions and geometries of elements in the document, for the purpose of re-rendering part or all of the document. When a reflow happens, the following steps take place:

1. **DOM Tree construction**: The document is parsed and a tree-like structure called the Document Object Model (DOM) is built.
2. **Render Tree construction**: The Render Tree, which is a tree of visual elements used in the painting process, is constructed. This involves figuring out the styles that apply to each visible element.
3. **Layout**: The browser calculates the geometry of the Render Tree to determine where each node should be on the page. This step is where the reflow is triggered.
4. **Paint**: After layout, the final painted information is filled in.

**Repaint** refers to the process where the browser needs to draw out elements, either because something was invalidated (layout recalculated, which may not cause a reflow), or because styles affecting the visibility changed (colors, outlines, etc.). A repaint involves the following steps:

1. **DOM Tree construction**
2. **Render Tree construction**
3. **Paint**: Here, the browser will "fill in" or "paint" the pixels for each visual element. This is what's referred to as a "repaint".

## JavaScript Functions that Trigger Reflow or Repaint

Here is a list of JavaScript operations and the browser rendering processes (reflow or repaint) they typically trigger:

- **Reflow**: Generally, any operation that changes the layout or geometry of elements will cause a reflow. For example:

    - Adding or removing elements from the DOM: Causes a reflow as the browser has to recalculate the layout.
    - Changing an element's size or position: Causes a reflow.
    - Resizing the window: Causes a reflow as the layout may have to change to accommodate the new window size.
    - Changing an element's content, particularly in a way that changes its layout (e.g., changing the text content in a way that will make the element wider or taller): Causes a reflow.
    - Querying or setting properties like `offsetHeight`, `offsetTop`, `offsetParent`, `scrollTop`, `scrollLeft`, `getComputedStyle`, `getBoundingClientRect`: These trigger a reflow because they require the browser to calculate layout information.

- **Repaint**: Any operation that changes visual styles but doesn't affect the layout will cause a repaint. For example:

    - Changing the color, background-color, visibility or outline of an element: Causes a repaint.
    - Animating an element with changes that do not affect layout (such as color changes, opacity changes, or transforms): Causes a repaint.
    - Querying or setting properties or styles that affect an element's appearance but not its layout: These can trigger a repaint.

### Improving Performance

1. **Minimize DOM Size**: A smaller DOM means less to parse, fewer render tree nodes, and less to lay out and paint.

2. **Avoid unnecessary reflows and repaints**: Batch your DOM changes and avoid layout thrashing where reflows are triggered multiple times.

3. **Use CSS wisely**: Some CSS properties can cause a page to slow down. For example, properties like `box-shadow` can require more of the browser and thus slow down the page.

4. **Use `will-change` property**: This CSS property allows you to inform the browser ahead of time of what kinds of changes you are likely to make to an element, allowing it to optimize early.

5. **Leverage GPU**: Transform and opacity changes can be handled by the GPU rather than the CPU, making them less expensive.

6. **Use layers wisely**: Promoting elements to their own layer can make compositing less expensive, but each layer consumes memory and more layers could cause more harm than good.
