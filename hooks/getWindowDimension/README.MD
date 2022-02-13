# WHAT DOES IT DO? 
> This hook capture the dimensions of device, is util for SSR applications nextjs or react

##CAUTION:
>but it doesn't work with getServerSideRendering and getStaticProps
---
## THE CODE
~~~javascript
import { useState, useEffect } from 'react';

export default function useWindowDimensions() {

  const hasWindow = typeof window !== 'undefined';

  function getWindowDimensions() {
    const width = hasWindow ? window.innerWidth : null;
    const height = hasWindow ? window.innerHeight : null;
    return {
      width,
      height,
    };
  }

  const [windowDimensions, setWindowDimensions] = useState(getWindowDimensions());

  useEffect(() => {
    if (hasWindow) {
      function handleResize() {
        setWindowDimensions(getWindowDimensions());
      }

      window.addEventListener('resize', handleResize);
      return () => window.removeEventListener('resize', handleResize);
    }
  }, [hasWindow]);

  return windowDimensions;
}
~~~
---
## HOW TO USE IN YOUR COMPONENT
~~~javascript
import useWindowDimensions from './hooks/useWindowDimensions';

const Component = () => {
  const { height, width } = useWindowDimensions();
  /* you can also use default values or alias to use only one prop: */
  // const { height: windowHeight = 480 } useWindowDimensions();

  return (
    <div>
      width: {width} ~ height: {height}
    </div>
  );
}
~~~
