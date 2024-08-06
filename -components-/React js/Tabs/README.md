<p>
 <h1 style="color:red;" align="center">Tabs</h1>
</p>

```js
import { useEffect, useState } from "react";

const TabBox = ({ tabItems, children }) => {
  const [activeTab, setActiveTab] = useState(localStorage.getItem("activeTab") || tabItems[0]?.key);

  useEffect(() => {
    localStorage.setItem("activeTab", activeTab);
  }, [activeTab]);

  const handleTabClick = (tabkey) => {
    setActiveTab(tabkey);
  };



  return (
    <>
      <ul className="flex flex-wrap gap-x-1 gap-y-2 pb-5 text-sm">
        {tabItems?.map((item) => (
          <li
            key={item.key}
            className={`bg-affity-color cursor-pointer text-white rounded-md py-1 px-3 ${activeTab.trim() === item.key.trim()
              ? "!bg-[#f350af] text-White"
              : ""
              }`}
            onClick={() => handleTabClick(item.key)}
          >
            {item.label}
          </li>
        ))}
      </ul>
      <div className="mt-1">
         {children.map((child) => (activeTab.trim() === child.key.trim() ? child : null))}
      </div>
    </>
  );
};

export default TabBox;
```

```js
import TabBox from "@/components/common/tabs";

function Rootpage() {
    const tabs = [
        { key: "tab1", label: "tab 1" },
        { key: "tab2", label: "tab 2" },
    ];

    return (
        <div className="w-11/12 lg:max-w-6xl m-auto pb-16">
            <TabBox tabItems={tabs}>
                <div key="tab1">
                    tab 1
                </div>
                <div key="tab2">
                    tab 2
                </div>
            </TabBox>
        </div>
    );
}

export default Rootpage;

```
