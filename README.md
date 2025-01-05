# horizontal-scroll-gallery

A modern horizontal scroll gallery with reveal effects, built with Locomotive Scroll in React. This component allows you to showcase products, collections, or content in a visually dynamic way, enhancing user engagement through smooth scrolling and animations.

## Features

- **Horizontal Scrolling**: Smooth, natural horizontal scrolling for an interactive browsing experience.
- **Locomotive Scroll Integration**: Leverages Locomotive Scroll to provide smooth scrolling with scroll-based animations.
- **Reveal Effect**: Elements fade in or animate as they come into view during scroll, creating an engaging, interactive experience.
- **Customizable**: Easy to adapt to various content types such as product galleries, lookbooks, or portfolios.

## Installation

To get started, install the necessary dependencies:

```bash
npm install locomotive-scroll react
```

Then, include Locomotive Scroll and create the horizontal scroll gallery component in your React app.

## Usage

### 1. Create the Horizontal Scroll Gallery Component

```jsx
import React, { useEffect, useRef } from 'react';
import LocomotiveScroll from 'locomotive-scroll';
import 'locomotive-scroll/src/locomotive-scroll.scss';

const HorizontalScrollGallery = () => {
  const scrollContainerRef = useRef(null);

  useEffect(() => {
    const scroll = new LocomotiveScroll({
      el: scrollContainerRef.current,
      smooth: true,
      direction: 'horizontal', // Horizontal scroll
    });

    return () => {
      scroll.destroy();
    };
  }, []);

  return (
    <div className="scroll-container" ref={scrollContainerRef}>
      <div className="scroll-content">
        {/* Add gallery items here */}
        <div className="gallery-item" data-scroll data-scroll-speed="2">
          <img src="image1.jpg" alt="Product 1" />
        </div>
        <div className="gallery-item" data-scroll data-scroll-speed="2">
          <img src="image2.jpg" alt="Product 2" />
        </div>
        <div className="gallery-item" data-scroll data-scroll-speed="2">
          <img src="image3.jpg" alt="Product 3" />
        </div>
      </div>
    </div>
  );
};

export default HorizontalScrollGallery;
```

### 2. Add Custom Styles

You can add custom styles to the horizontal scroll gallery for layout, size, and animation:

```css
.scroll-container {
  width: 100%;
  height: 100vh;
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
}

.scroll-content {
  display: flex;
  flex-direction: row;
}

.gallery-item {
  margin-right: 20px;
  opacity: 0;
  transition: opacity 0.5s ease-out;
}

.gallery-item[data-scroll] {
  opacity: 1;
}
```

### 3. Implement Reveal Effects

For reveal effects, use Locomotive Scroll's data attributes to trigger animations on scroll:

```jsx
<div className="gallery-item" data-scroll data-scroll-speed="2" data-scroll-class="reveal">
  <img src="image1.jpg" alt="Product 1" />
</div>
```

Then define the animation in your CSS:

```css
.reveal {
  opacity: 1 !important;
  transform: translateY(0) !important;
}
```

## Customization

- **Scroll Direction**: You can set the scroll direction to horizontal by adding `direction: 'horizontal'` in the Locomotive Scroll configuration.
- **Scroll Speed**: Control the scroll speed of each item by adjusting the `data-scroll-speed` attribute.
- **Animations**: Use Locomotive Scroll's `data-scroll-class` or `data-scroll` attributes to trigger animations such as fade-ins or transforms.

## Example

Here’s how you can use the gallery component within your app:

```jsx
import React from 'react';
import HorizontalScrollGallery from './HorizontalScrollGallery';

const App = () => (
  <div>
    <HorizontalScrollGallery />
  </div>
);

export default App;
```

## Contributions

We welcome contributions! If you find a bug or want to enhance the functionality, feel free to fork the repository and create a pull request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
