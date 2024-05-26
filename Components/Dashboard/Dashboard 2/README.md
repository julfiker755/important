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
