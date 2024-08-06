<p>
 <h1 style="color:red;" align="center">Accordion</h1>
</p>


```js
import Accordion from '@/components/reuseable/Accordion'


function Rootpage() {
  const advertisersQuestions= [
    {
      title: "Sign Up and Onboard",
      content:"Create your account and set up your first campaign with ease. Our user-friendly interface and guided setup process make it simple to get started.",
    },
    {
      title: "Recruit Affiliates",
      content:"Launch your advertising campaigns across various channels. Whether you're focusing on display ads, social media, or search, Affity supports all major advertising platforms.",
    },
    {
      title: "Track and Optimize",
      content:"Monitor your campaigns in real-time and use our advanced analytics to optimize performance. Make data-driven decisions to enhance your ROI.",
    },{
      title:"Scale Your Efforts",
      content:"As you refine your strategy, scale your campaigns to reach a larger audience. Affity provides the tools you need to grow your advertising efforts successfully.",
    }
  ];


  return (
    <div>
        <Accordion questions={advertisersQuestions}></Accordion>
    </div>
  );
}

export default Rootpage
```

```js
"use client"
import { useEffect, useRef, useState } from "react";
import { GoPlus } from "react-icons/go";
import { HiMinus } from "react-icons/hi";
import Container from '@/components/reuseable/container';
import './index.css';


function Accordion({ questions }) {
  const [activeAccordion, setActiveAccordion] = useState(null);
  const [contentHeight, setContentHeight] = useState(0);
  const contentRef = useRef(null);

  useEffect(() => {
    const otherSideRemover = ({ target }) => {
      if (!contentRef.current || !activeAccordion) return;
      if (!contentRef.current.contains(target)) {
        setActiveAccordion(null);
      }
    };
    document.addEventListener('click',otherSideRemover);
    return () => document.removeEventListener('click',otherSideRemover);
  }, [activeAccordion]);


  useEffect(() => {
    if (contentRef.current) {
      setContentHeight(activeAccordion === null ? 0 : contentRef.current.scrollHeight);
    }
  }, [activeAccordion]);

  const toggleAccordion = (index) => {
    setActiveAccordion(prev => (prev === index ? null : index));
  };



  return (
    <Container>
      <div className="py-5">
        <div className="flex flex-col lg:flex-row">
          <div className="w-full">
            {questions.map((item, index) => (
              <div key={index} className="py-[10px] px-5 mb-4 rounded-md custom-box-shadow cursor-pointer bg-inherit">
                <div className="flex items-center justify-between" onClick={() => toggleAccordion(index + 1)}>
                  <h4 className="text-base lg:text-lg font-[550] text-[#1B1B1B]">
                    {item.title}
                  </h4>
                  <span>
                    {activeAccordion === index + 1 ? (
                      <HiMinus size={20} className="text-[#282828]" />
                    ) : (
                      <GoPlus size={20} />
                    )}
                  </span>
                </div>
                <div
                  className={`overflow-hidden transition-all duration-300 ease-out ${activeAccordion === index + 1 ? 'max-h-full' : 'max-h-0'}`}
                  style={{ maxHeight: activeAccordion === index + 1 ? `${contentHeight}px` : '0px' }}
                  ref={contentRef}
                >
                  <p className="text-sm lg:text-base mt-1">{item.content}</p>
                </div>
              </div>
            ))}
          </div>
        </div>
      </div>
    </Container>
  );
}

export default Accordion
```
