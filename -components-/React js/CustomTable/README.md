```js
import "./index.css";

export default function CustomTable({ headers, children }) {
    return (
      <div>
        <div className="overflow-x-auto">
          <table className="custom-table w-full min-h-full">
            <thead className="">
              <tr className="bg-[#052D57] !rounded-md">
                {headers?.map((header, index) => (
                  <th
                    key={index}
                    className={`py-3 text-lg text-white`}
                  >
                    {header}
                  </th>
                ))}
              </tr>
            </thead>
            <tbody>
              {children}
            </tbody>
          </table>
        </div>
      </div>
    );
  }
```
```js
.custom-table tr {
    @apply whitespace-nowrap;
}

.custom-table td {
    @apply px-6 py-2 text-sm text-gray-500 text-center;
}
```
```js
{
  customer?.map((item, index) => (
    <tr
      className={`transition-all duration-300 ${index % 2 === 0 ? "" : "bg-gray-200"
        }`}
      key={index}
    >
    </tr>
 }
```

```js
    <CustomTable headers={["Feature", "Affity", "Affise", "Offer18", "HasOffers"]}>
        <tr className="border-b-[1px]">
            <td className="!text-left !text-lg lg:w-[250px]">
              Affordable Pricing
            </td>
            <td className="table-shadow">
              <div className="flex gap-1 justify-center text-lg items-center">
                <IoCheckmarkCircleSharp   className="text-[#008000d7]" size={22}/>
              </div>
            </td>
            <td>
            <div className="flex gap-1 justify-center text-lg items-center">
              <IoCloseCircleSharp className="text-[#ff000098]" size={22}/>
              </div>
            </td>
            <td>
            <div className="flex gap-1 justify-center text-lg items-center">
                <IoCloseCircleSharp className="text-[#ff000098]" size={22}/>
              </div>
            </td>
            <td>
            <div className="flex gap-1 justify-center text-lg items-center">
                <IoCloseCircleSharp className="text-[#ff000098]" size={22}/>
              </div>
            </td>
          </tr>
          <tr className="border-b-[1px]">
            <td className="!text-left !text-lg lg:w-[250px]">
               Quick Onboarding
            </td>
            <td className="table-shadow">
              <div className="flex gap-1 justify-center text-lg items-center">
              <IoCheckmarkCircleSharp   className="text-[#008000d7]" size={22}/>
              </div>
            </td>
            <td>
            <div className="flex gap-1 justify-center text-lg items-center">
               <IoCloseCircleSharp className="text-[#ff000098]" size={22}/>
              </div>
            </td>
            <td>
            <div className="flex gap-1 justify-center text-lg items-center">
            <IoCheckmarkCircleSharp   className="text-[#008000d7]" size={22}/>
              </div>
            </td>
            <td>
            <div className="flex gap-1 justify-center text-lg items-center">
              <IoCloseCircleSharp className="text-[#ff000098]" size={22}/>
              </div>
            </td>
          </tr>
        </CustomTable>
```
