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
