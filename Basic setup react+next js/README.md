
```js
  useEffect(()=>{
    window.scrollTo(0, 0);
},[])
/* Custom scrollbar */
/* Width */
::-webkit-scrollbar {
  width: 5px;
  border-radius: 6px;
}


/* Track */
::-webkit-scrollbar-track {
  background: #e0e9f4;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: #1890ff;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #1890ff;
}
```

```js
  background-image: radial-gradient(#fc8b0257 1px, transparent 0);
  background-size: 10px 10px;
```

```js
// close if the esc key is pressed
    useEffect(() => {
      const keyHandler = ({ keyCode }) => {
        if (!dropdownOpen || keyCode !== 27) return;
        setDropdownOpen(false);
      };
      document.addEventListener('keydown', keyHandler);
      return () => document.removeEventListener('keydown', keyHandler);
    });
```

### Container
```js
import React from 'react';

const Container = ({children }) => {
    return (
        <div className='w-11/12 lg:max-w-7xl m-auto'>
            {children}
        </div>
    );
};

export default Container;
```
### Button
```js
"use client"
const Button = ({handleclick="",children}) => {
    return (
        <button 
        onClick={()=>handleclick()} 
        className='w-full bg-[#3288e9] text-white py-2 px-3 rounded-sm' >
        {children}
        </button>
    );
};

export default Button;
```
```js
"use client";
import React, { useEffect, useState } from "react";

// Define the type for position state
interface Position {
  x: number;
  y: number;
}


// Main CustomCursor component
const CustomCursor: React.FC = () => {
  const [position, setPosition] = useState<Position>({ x: -100, y: -100 });
  const [woking,setWorking]=useState<number | null>(null);

  useEffect(() => {
    function handleMove(e: PointerEvent) {
      setPosition({ x: e.clientX, y: e.clientY });
    }

    function handleMouseOut() {
      setPosition({ x: -100, y: -100 });
    }

    window.addEventListener("pointermove", handleMove);
    window.addEventListener("mouseout", handleMouseOut);

    return () => {
      window.removeEventListener("pointermove", handleMove);
      window.removeEventListener("mouseout", handleMouseOut);
    };
  }, []);

   
  // extrea soluton use
  useEffect(() => {
    const handleMouseEnter = () => setWorking(Math.floor(Math.random()*6666))
    const handleMouseOut = () => setWorking(0);
    
    const elements = document.querySelectorAll('.custom-cursor');
    elements.forEach(element => {
      element.addEventListener('mouseenter', handleMouseEnter);
      element.addEventListener('mouseout', handleMouseOut);
    });
  
    return () => {
      elements.forEach(element => {
        element.removeEventListener('mouseenter', handleMouseEnter);
        element.removeEventListener('mouseout', handleMouseOut);
      });
    };
  }, [woking]);
 
 
{/* <div className="border-2 border-[#3B82F6] p-2 rounded-full">
        <div className="bg-blue-500 p-[6px] rounded-full"></div>
  </div> */}


  
   

  return (
    <div
      style={{
        transform: `translate(${position.x}px, ${position.y}px)`,
        position: "fixed",
        pointerEvents: "none",
        left: -16,
        top: -16,
        zIndex: 9999,
      }}
    >
     <div className={`${woking ? 'border-none':'border-2' } w-[34px] h-[34px] flex flex-col items-center justify-center border-[#3B82F6] p-2 rounded-full`}>
    <div className={`${woking ? 'bg-[#3b83f652] [transition:0.4s] w-full h-full ![transform:scale(2)] rounded-full':'[transform:scale(1)] w-[10px] h-[10px] bg-blue-500  rounded-full'}`}></div>
      </div>
    </div>
  );
};

export default CustomCursor;

```
