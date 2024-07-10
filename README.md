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
