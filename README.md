# react-multi-carousel

Lightweight React carousel component supports multiple items and SSR(Server-side rendering) with typescript.

The technical details of this carousel can be found at [www.w3js.com -> react-multi-carousel](https://w3js.com/index.php/2019/03/06/react-carousel-with-server-side-rendering-support-part-1z/).

## NPM

[NPM](https://www.npmjs.com/package/react-multi-carousel).

## Bundle size

[Bundle-size](https://bundlephobia.com/result?p=react-multi-carousel@1.0.33).
2.5kB

## Demo.

Demo and documentation can be found at [here](https://w3js.com/react-multi-carousel/).

Demo for the SSR are at [here](https://react-multi-carousel.now.sh/)
Try to disable JavaScript to test if it renders on the server-side.

Codes for SSR at [github](https://github.com/YIZHUANG/react-multi-carousel/blob/master/examples/ssr/pages/index.js).

Codes for the documentation at [github](https://github.com/YIZHUANG/react-multi-carousel/blob/master/stories/index.stories.js).

## Install

```
$ npm install react-multi-carousel --save

import Carousel from 'react-multi-carousel';
import 'react-multi-carousel/lib/styles.css';
```

### Technical approach.

Detailed Can be found in this blog post at [w3js](https://w3js.com/index.php/2019/03/06/react-carousel-with-server-side-rendering-support-part-1z/).

### How the SSR mode works?

The current most common solution is to detect the device type of the user based on the user agent. (server-side or client-side).

Based based on the device type, we decided how many items we are showing in the Carousel.

More detailed can be found in this blog post [here](https://w3js.com/index.php/2019/03/06/react-carousel-with-server-side-rendering-support-part-1z/).

Codes for SSR at [github](https://github.com/YIZHUANG/react-multi-carousel/blob/master/examples/ssr/pages/index.js).

Demo for the SSR are at [here](https://react-multi-carousel.now.sh/) Try to disable JavaScript to test if it renders on the server-side.

## Features.

* Server-side rendering
* Infinite mode
* Custom animation
* AutoPlay mode
* Responsive
* Swipe to slide
* Mouse drag to slide
* Keyboard control to slide
* Multiple items
* Show / hide arrows
* Custom arrows / control buttons
* Custom styling

## Examples

```
const responsive = {
  desktop: {
    breakpoint: { max: 3000, min: 1024 },
    items: 3
  },
  tablet: {
    breakpoint: { max: 1024, min: 464 },
    items: 2
  },
  mobile: {
    breakpoint: { max: 464, min: 0 },
    items: 1
  }
};
<Carousel
  disableSwipeOnMobile
  disableDrag
  shouldShowDots={true}
  responsive={responsive}
  forSSR
  slidesToSlide={2}
  infinite={true}
  autoPlay={this.props.deviceType !== 'mobile' ? true : false}
  autoPlaySpeed={1000}
  keyBoardControl={true}
  customTransition='all .5'
  transitionDuration={500}
  containerClassName='container-border-green'
  removeArrowOnDeviceType={['tablet', 'mobile']}
  deviceType={this.props.deviceType}
>
  {fakerData.map(card => {
    return <Card {...card} />;
  })}
</Carousel>
```

## Custom Arrows.
You can pass your own custom arrows to make it the way you want, the same for the position. For example, add media query for the arrows to go under when on smaller screens.

```
const CustomRightArrow = ({ onClick }) => <button onClick={() => onClick()} />
<Carousel customRightArrow={<CustomRightArrow />} />
```

## General Props
```
  responsive: responsiveType;
  deviceType?: string;
  forSSR?: boolean;
  slidesToSlide: number;
  disableDrag?: boolean;
  removeArrow?: boolean;
  disableSwipeOnMobile?: boolean;
  removeArrowOnDeviceType?: string | Array<string>;
  children: React.ReactNode | null;
  customLeftArrow?: React.ReactElement<any> | null;
  customRightArrow?: React.ReactElement<any> | null;
  infinite?: boolean;
  contentClassName?: string;
  itemClassName?:string;
  containerClassName?: string;
  keyBoardControl?: boolean;
  autoPlay?: boolean; // make sure you put infinite={true} if autoPlay is enabled.
  autoPlaySpeed?: number; // default 3000ms
  customTransition?:string;
  transitionDuration?: number;
  // if you are using customTransition, make sure to put the duration here.
  // for example, customTransition="all .5"  then put transitionDuration as 500.
  // this is needed for the resizing to work.
```

## Specific Props

| Name                 | Type              | Default               | Description                                                              |
| :------------------- | :---------------- | :-------------------- | :----------------------------------------------------------------------- |
| `responsive`              | `Object`         | `{}`               | How many items to show on each breakpoint.                                                                   |
| `deviceType`            | `string` | `none`                 | Only pass this when use for server-side rendering, what to pass can be found in the example folder.                                                                    |
| `forSSR`           | `bool`            | `false`               | For SSR |
| `slidesToSlide`   | `number`          | `1` | How many slides to slide.                                                       |

## Contribute

Submit an issue for feature request or submit a pr.
