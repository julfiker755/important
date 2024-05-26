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
