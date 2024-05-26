### Dashboard layout
```js
import React from 'react';
import { useState } from 'react';
import Header from './Header/Header';
import Sidebar from './Sideber/Sideber';

const DashboardLayout = () => {
  const [sidebarOpen, setSidebarOpen] = useState(false);
  return (
    <div className="bg-boxdark-2 text-bodydark">
      <div className="flex h-screen overflow-hidden">
        {/* <!-- ===== Sidebar Start ===== --> */}
        <Sidebar sidebarOpen={sidebarOpen} setSidebarOpen={setSidebarOpen} />
        {/* <!-- ===== Content Area Start ===== --> */}
        <div className="relative flex flex-1 flex-col overflow-y-auto overflow-x-hidden">
          <Header sidebarOpen={sidebarOpen} setSidebarOpen={setSidebarOpen} />
          <main>
            <div className="mx-auto max-w-screen-2xl p-4 md:p-6 2xl:p-10">
              {/* ----content--- */}
               <h1>content the layout hare </h1>
            </div>
          </main>
        </div>
      </div>
    </div>
  );
};

export default DashboardLayout;
```
### Sideber components
```js
import React, { useEffect, useRef} from 'react';
import { NavLink} from 'react-router-dom';
import { IoIosClose } from "react-icons/io";
import Menuitem from '../Menuitem/Menuitem';
import { MdDashboard } from "react-icons/md";
import { IoSettingsOutline } from "react-icons/io5";
import { CiViewTable } from "react-icons/ci";
import { MdProductionQuantityLimits } from "react-icons/md";



const Sidebar = ({ sidebarOpen, setSidebarOpen }) => {
  const trigger = useRef(null);
  const sidebar = useRef(null);
  // close on click outside
  useEffect(() => {
    const clickHandler = ({ target }) => {
      if (!sidebar.current || !trigger.current) return;
      if (
        !sidebarOpen ||
        sidebar.current.contains(target) ||
        trigger.current.contains(target)
      )
        return;
      setSidebarOpen(false);
    };
    document.addEventListener('click', clickHandler);
    return () => document.removeEventListener('click', clickHandler);
  });

  return (
    <aside
      ref={sidebar}
      className={`absolute left-0 top-0 z-[99999999] flex h-screen w-72.5 flex-col overflow-y-hidden bg-[#1C2434] duration-300 ease-linear text-white w-[240px] lg:static lg:translate-x-0 ${
        sidebarOpen ? 'translate-x-0' : '-translate-x-full'
      }`}
    >
     <div className='py-3'>
         {/* <!-- sideber header --> */}
      <div className="flex items-center justify-between gap-2 px-6 py-5.5 lg:py-6.5">
        <NavLink to="/">
          <img className='text-white w-[100px]' src="https://kutty.netlify.app/brand/kutty-logo-white.png" alt="" />
        </NavLink>
        <button
          ref={trigger}
          onClick={() => setSidebarOpen(!sidebarOpen)}
          aria-controls="sidebar"
          aria-expanded={sidebarOpen}
          className="block border rounded-full lg:hidden"
        >
           <IoIosClose  color="white" size={30}/>
        </button>
      </div>
      <div className="no-scrollbar  flex flex-col overflow-y-auto duration-300 ease-linear">
        <nav className="mt-5 py-4 px-4 lg:mt-9 lg:px-6">
          <div>
            <h3 className="mb-4 ml-4 text-sm font-semibold text-bodydark2">Menu</h3>
            <ul className="mb-6 flex flex-col gap-1.5">
              {/* menu item box */}
              <Menuitem path="/dashboard" activepath='dashboard'> < MdDashboard/>Dashboard</Menuitem>
              <Menuitem path="/settings" activepath='settings'><IoSettingsOutline size={20}/>Settings</Menuitem>
              <Menuitem path="/table" activepath='table'>< CiViewTable size={20}/>Table</Menuitem>
              <Menuitem path="/products" activepath='products'><MdProductionQuantityLimits/>Products</Menuitem>
            </ul>
          </div>
        </nav>
      </div>
     </div>
    </aside>
  );
};

export default Sidebar;

```

### Menuitem components
```js
import React from 'react';
import { NavLink, useLocation } from 'react-router-dom';

const Menuitem = ({children,path,activepath=""}) => {
    const location = useLocation();
    const { pathname } = location;
    return (
        <li>
            <NavLink
                  to={path}
                  className={`group relative flex items-center gap-2.5 rounded-sm py-2 px-4 font-medium duration-300 ease-in-out hover:bg-[#2f3a52] ${
                    pathname.includes(activepath) &&
                    'bg-[#2f3a52]'
                  }`}
                >
                 {children}
                </NavLink>
            </li>
    );
};

export default Menuitem;
```

### Header components
```js
import React from 'react';
import { LuMenu } from "react-icons/lu";
import Search from './Search/Search';
import DropdownUser from './DropdownUser/DropdownUser';

const Header = ({sidebarOpen,setSidebarOpen}) => {
    return (
        <div className='sticky top-0 z-999 flex w-full bg-[#333A48] py-1 shadow-1'>
      <header className="w-full px-3">
      <div className="flex justify-between items-center">
          {/* left side*/}
          <div className='flex gap-4 items-center'>
          <button
            aria-controls="sidebar"
            onClick={(e) => {
              e.stopPropagation();
              setSidebarOpen(!sidebarOpen);
            }}
            className="z-99999 block  border rounded-md border-stroke  p-1.5 shadow-sm lg:hidden"
          >
            <LuMenu color='white'/>
          </button>
           <Search></Search>
          </div>
          {/* right side */}
         <div>
            <DropdownUser/>
         </div>
      </div>
    </header>
   </div>
    );
};

export default Header;
```

### Search components
```js
import { CiSearch } from "react-icons/ci";

const Search = () => {
    return (
        <div className="flex  items-center bg-[white] py-1 px-3 rounded-md">
                <div className="flex w-5 items-center justify-center">
                    <CiSearch />
                </div>
                <input
                    type="text"
                    className="pl-2 w-full outline-none"
                    placeholder="Search hare"
                />
            </div>
    );
};

export default Search;
```
### droupdown components
```js
import { useEffect, useRef, useState } from 'react';
import { Link } from 'react-router-dom';
import { BsPersonCircle } from "react-icons/bs";
import { BsPersonCheckFill } from "react-icons/bs";
import { BiSolidContact } from "react-icons/bi";
import { CiSettings } from "react-icons/ci";
import { CiLogout } from "react-icons/ci";


const DropdownUser = () => {
    const [dropdownOpen, setDropdownOpen] = useState(false);
    const trigger = useRef(null);
    const dropdown = useRef(null);
    // close on click outside
    useEffect(() => {
      const clickHandler = ({ target }) => {
        if (!dropdown.current) return;
        if (
          !dropdownOpen ||
          dropdown.current.contains(target) ||
          trigger.current.contains(target)
        )
          return;
        setDropdownOpen(false);
      };
      document.addEventListener('click', clickHandler);
      
      return () => document.removeEventListener('click', clickHandler);
    });
//    submenu array
  const profilesubdata=[
    {
      id:1,
      path:"/profile",
      pathname:" My Profile",
      icon: <BsPersonCheckFill size={20}/>
    },{
      id:2,
      path:"/Contacts",
      pathname:"My Contacts",
      icon:<BiSolidContact size={20}/>
    },{       
      id:3,
      path:"/Settings",
      pathname:"Account Settings",
      icon: <CiSettings size={20}/>
    }
  ]
    return (
        <div className="relative">
      <Link
        ref={trigger}
        onClick={() => setDropdownOpen(!dropdownOpen)}
        className="flex items-center gap-4"
        to="#"
      >
        <span className="hidden text-right lg:block">
          <span className="block text-sm font-medium text-white">
            Thomas Anree
          </span>
          <span className="block text-xs text-white">UX Designer</span>
        </span>

        <span className="h-10 w-10 flex items-center rounded-full">
          <BsPersonCircle color='white' size={35}/>
        </span>
      </Link>

      {/* <!-- Dropdown Start --> */}
      <div
        ref={dropdown}
        onFocus={() => setDropdownOpen(true)}
        onBlur={() => setDropdownOpen(false)}
        className={`absolute right-0 mt-4 flex w-62.5 flex-col rounded-sm border border-stroke bg-white shadow-default ${
          dropdownOpen === true ? 'block' : 'hidden'
        }`}
      >
        <ul className="flex flex-col w-[220px]  gap-5 border-b  border-stroke px-6 py-5">
          {profilesubdata?.map(d =><li key={d.id}>
            <Link
              to={d?.path}
              className="flex items-center gap-3.5 text-sm font-medium duration-300 ease-in-out hover:text-primary lg:text-base"
            >
               {d?.icon}
               {d?.pathname}
            </Link>
          </li>)}
        </ul>
        <button className="flex items-center gap-3.5 px-6 py-4 text-sm font-medium duration-300 ease-in-out hover:text-primary lg:text-base">
          <CiLogout size={20}/>
          Log Out
        </button>
      </div>
    </div>
    );
};

export default DropdownUser;

```
