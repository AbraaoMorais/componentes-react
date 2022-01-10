# WHAT DOES IT DO? 
> This hook capture the dimensions of device, is util for SSR applications nextjs or react

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
