# IMPORTANT
 const bodycontent=body.match(/<body[^>]*>([\s\S.]*)<\/body>/i)[1]

 https://www.npmjs.com/package/html-react-parser



  https://github.com/taylor-lindores-reeves/NextJS-SSR-offset-based-pagination/blob/main/components/pagination.tsx
  https://www.youtube.com/watch?v=cxxumABmLYA


import React from 'react'
import Pagination from './paginatio'

export default function Rootpage({ searchParams }) {
  console.log(searchParams.page)
  return (
    <div>
      <Pagination page={searchParams.page}></Pagination>
    </div>
  )
}

```js
// components/Tabs.js

import Link from 'next/link';

const Tabs = ({ activeTab }) => {
  const renderContent = () => {
    switch (activeTab) {
      case 'tab1':
        return <div>Content for Tab 1</div>;
      case 'tab2':
        return <div>Content for Tab 2</div>;
      case 'tab3':
        return <div>Content for Tab 3</div>;
      default:
        return <div>Select a tab to see content</div>;
    }
  };

  return (
    <div>
      <div className="tab-menu">
        <Link href="/?tab=tab1">
          <a className={activeTab === 'tab1' ? 'active' : ''}>Tab 1</a>
        </Link>
        <Link href="/?tab=tab2">
          <a className={activeTab === 'tab2' ? 'active' : ''}>Tab 2</a>
        </Link>
        <Link href="/?tab=tab3">
          <a className={activeTab === 'tab3' ? 'active' : ''}>Tab 3</a>
        </Link>
      </div>
      <div className="tab-content">
        {renderContent()}
      </div>
      <style jsx>{`
        .tab-menu a {
          margin-right: 10px;
          text-decoration: none;
          padding: 5px 10px;
          color: black;
        }
        .tab-menu a.active {
          font-weight: bold;
          color: blue;
        }
        .tab-content {
          margin-top: 20px;
        }
      `}</style>
    </div>
  );
};

export default Tabs;


```
```js
import { useRouter } from 'next/router';
import Link from 'next/link';

const Tabs = () => {
  const router = useRouter();
  const { tab } = router.query;

  // Set default tab to 'tab1' if no tab query parameter is present
  const activeTab = tab || 'tab1';

  const renderContent = () => {
    switch (activeTab) {
      case 'tab1':
        return <div>Content for Tab 1</div>;
      case 'tab2':
        return <div>Content for Tab 2</div>;
      case 'tab3':
        return <div>Content for Tab 3</div>;
      default:
        return <div>Select a tab to see content</div>;
    }
  };

  return (
    <div>
      <div className="tab-menu">
        <Link href="/?tab=tab1">
          <a className={activeTab === 'tab1' ? 'active' : ''}>Tab 1</a>
        </Link>
        <Link href="/?tab=tab2">
          <a className={activeTab === 'tab2' ? 'active' : ''}>Tab 2</a>
        </Link>
        <Link href="/?tab=tab3">
          <a className={activeTab === 'tab3' ? 'active' : ''}>Tab 3</a>
        </Link>
      </div>
      <div className="tab-content">
        {renderContent()}
      </div>
      <style jsx>{`
        .tab-menu a {
          margin-right: 10px;
          text-decoration: none;
          padding: 5px 10px;
          color: black;
        }
        .tab-menu a.active {
          font-weight: bold;
          color: blue;
        }
        .tab-content {
          margin-top: 20px;
        }
      `}</style>
    </div>
  );
};

export default Tabs;

```

```js
/* eslint-disable react/prop-types */
const CustomInput = ({
    id,
    label = '',
    name,
    defaultValue,
    type,
    disabled = false,
    placeholder,
    register,
    required,
    errors,
}) => {
    return (
        <div className="w-full">
            <label htmlFor={id} className="mb-1 block text-sm font-medium text-gray-500">
                {label}
            </label>
            <input
                type={type}
                name={name}
                disabled={disabled}
                defaultValue={defaultValue}
                placeholder={placeholder}
              className="block w-full appearance-none rounded-sm border border-gray-300 px-3 py-2 placeholder-gray-400 shadow-sm focus:border-[#A0DEFF] focus:outline-none focus:ring-[#FFD300] sm:text-sm"
                {...register(name, { required: required })}
            />
            <div className="error-text">
                {errors && errors[name] && <span>{label || 'this'} field is required</span>}
            </div>
        </div>
    );
};

export default CustomInput;
<CustomInput
                id="name"
                label="Name"
                type="text"
                name="name"
                placeholder="Enter your name"
                register={register}
                errors={errors}
            />



/* eslint-disable react/prop-types */
const CustomSelect = ({ label, name, options, register, errors, defaultTitle, setSelectValue }) => {

    return (
        <div className="mb-1 w-full">
            <label className="mb-1 block text-sm font-medium text-gray-500" htmlFor={name}>
                {label}
            </label>
            <select
                name={name}
                id={name}
                {...register(name)}
                onChange={()=>setSelectValue(event.target.value)}
                className={`className="block w-full appearance-none rounded-sm border border-gray-300 px-3 py-2 placeholder-gray-400 shadow-sm focus:border-[#A0DEFF] focus:outline-none focus:ring-[#FFD300] sm:text-sm" ${errors[name] ? 'border-red-500' : ''
                    }`}
            >
                <option selected disabled>{defaultTitle}</option>
                {options.map((option, index) => (
                    <option key={index} value={option.value}>
                        {option.label}
                    </option>
                ))}
            </select>
            {errors[name] && <p className="error-text">{errors[name].message}</p>}
        </div>
    );
};

export default CustomSelect;


 <CustomSelect
                    label="Select an Option"
                    name="mySelect"
                    options={category}
                    register={register}
                    errors={errors}
                    defaultTitle="Choose an option"
                    setSelectValue={setSelectValue}
                />
```
