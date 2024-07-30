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

 ```
"use client"
import React, { useState } from 'react'
import { IoCheckmark } from 'react-icons/io5'
import './index.css'

function PricingCard() {
    const [isChecked, setIsChecked] = useState(false);
    const handleToggle = () => {
        setIsChecked(!isChecked);
      };
      const pricingItems = {
        monthly: [
          {
            title: "Start",
            price: "$15.99",
            monthy:"mo",
            itemsList: [
              "Online store",
              "Unlimited products",
              "5 staff accounts",
              "Free SSL certificate",
              "Gift cards creation",
              "Professional reports",
              "Gift cards creation",
              "Gift cards creation",
            ],
          },
          {
            title: "Business",
            price: "$29.99",
            monthy:"mo",
            itemsList: [
              "Online store",
              "Unlimited products",
              "5 staff accounts",
              "Free SSL certificate",
              "Gift cards creation",
              "Professional reports",
              "Gift cards creation",
              "Gift cards creation",
            ],
            color: "#574FEC",
          },
          {
            title: "Enterprise",
            price: "$99.99",
            monthy:"mo",
            itemsList: [
              "Online store",
              "Unlimited products",
              "5 staff accounts",
              "Free SSL certificate",
              "Gift cards creation",
              "Professional reports",
              "Gift cards creation",
              "Gift cards creation",
            ],
          },
        ],
        yearly: [
          {
            title: "Start",
            price: "$1200.99",
            itemsList: [
              "Online store",
              "Unlimited products",
              "5 staff accounts",
              "Free SSL certificate",
              "Gift cards creation",
              "Professional reports",
              "Gift cards creation",
              "Gift cards creation",
            ],
          },
          {
            title: "Business",
            price: "$6900.99",
            itemsList: [
              "Online store",
              "Unlimited products",
              "5 staff accounts",
              "Free SSL certificate",
              "Gift cards creation",
              "Professional reports",
              "Gift cards creation",
              "Gift cards creation",
            ],
            color: "#574FEC",
          },
          {
            title: "Enterprise",
            price: "$2006.90",
            itemsList: [
              "Online store",
              "Unlimited products",
              "5 staff accounts",
              "Free SSL certificate",
              "Gift cards creation",
              "Professional reports",
              "Gift cards creation",
              "Gift cards creation",
            ],
          },
        ]
      };

  const currentPricingItems = isChecked ? pricingItems.yearly : pricingItems.monthly;
  
  return (
    <div className="w-11/12 lg:max-w-6xl m-auto relative py-10 lg:py-0 lg:top-[-115px]">
    <div className="pb-14">
      <ul className="flex justify-center gap-3 text-xl">
        <li>Monthly</li>
        <li>
        <label className="relative inline-flex items-center cursor-pointer">
        <input
          type="checkbox"
          checked={isChecked}
          onChange={handleToggle}
          className="sr-only"
        />
        <div
          className={`w-[55px] h-[28px] bg-gray-300 rounded-full ${isChecked ? '!bg-blue-500' : ''} 
          transition-colors duration-300 ease-in-out`}
        >
          <span
            className={`absolute left-[2px] top-[2px] w-6 h-6 bg-white rounded-full transition-transform duration-300 ease-in-out 
            ${isChecked ? 'translate-x-[27px]' : ''}`}
          ></span>
        </div>
      </label>
        </li>
        <li>Yearly</li>
      </ul>
    </div>
    <div className="grid gap-y-10 lg:gap-y-0 lg:gap-x-8 grid-cols-1 lg:grid-cols-3">
      {currentPricingItems?.map((item, index) =>(     
        <div
          key={index}
          className="pricing-card-shadow lg:even:[transform:translateY(-25px)] bg-white lg:hover:!shadow-pricing-hover border lg:border-none rounded-lg lg:rounded-2xl p-5 translate-y-4"
        >
          <div className="flex justify-between items-center pb-12">
            <h1
              style={{ color: item.color }}
              className="text-2xl text-color font-medium"
            >
              {item.title}
            </h1>
            <ul className="text-gray-400 text-xl text-right">
              <li className="">/mo</li>
              <li className="text-2xl">{item.price}</li>
            </ul>
          </div>
          <ul className="space-y-3">
            {item?.itemsList?.map((items, index) => (
              <li
                key={index}
                className="flex gap-2 items-center text-base text-[#384C74]"
              >
                <h1 className="bg-custom-gray w-fit h-fit p-1 rounded-full">
                  <IoCheckmark size={16} color="#6DBB30" />
                </h1>
                {items}
              </li>
            ))}
          </ul>
          <div>
            <button
              style={{ color: item.color }}
              className={"text-[#384C74] text-lg pt-14"}
            >
              Get Started
            </button>
          </div>
        </div>
      ))}
      
    </div>
  </div>
  )
}

export default PricingCard
js```
