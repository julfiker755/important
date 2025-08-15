
## not found

```js
import { useCallback } from 'react';
import { jsPDF } from 'jspdf';
import html2canvas from 'html2canvas';

const useConverter = () => {
  const handleDownload = useCallback((type: 'pdf' | 'image', downloadText: string, content: HTMLElement, width = 210, height = 297) => {
    if (!content) return;

    html2canvas(content, { scale: 2 }).then((canvas) => {
      const imgData = canvas.toDataURL(type === 'pdf' ? 'image/png' : 'image/jpeg');

      if (type === 'pdf') {
        const pdf = new jsPDF({ orientation: 'portrait', unit: 'mm', format: [width, height] });
        const imgHeight = canvas.height * (width / canvas.width);
        pdf.addImage(imgData, 'PNG', 0, 0, width, imgHeight);
        pdf.save(`${downloadText}.pdf`);
      } else {
        const link = document.createElement('a');
        link.href = imgData;
        link.download = `${downloadText}.jpg`;
        link.click();
      }
    });
  }, []);

  return { handleDownload };
};

export default useConverter

```
```js
//tailwind css
<ul class="hover:[&>li]:bg-[red]">
  <li>Julfiker</li>
  <li>Jim</li>
  <li>Rahaman</li>
  <li>Julfiker Rahaman</li>
</ul>
// shor and topic
*:text-[green]
[&_img]:size-20
-------------------------------------
<table id="t1" class="[&_td]:px-2 [&_td]:text-lg">
  <tr>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>
default: "h-9 px-4 py-2 has-[>svg]:px-3",
```

```js
// custom404
// app>[...not-found]>page.js
"use client"
import { redirect } from 'next/navigation';
import { useEffect } from 'react'

export default function Custom404() {
  useEffect(() => {
    redirect("/")
  }, []);
  return null;
}

```
```js
import React from "react";

interface IconProps {
  name: "home" | "user" | "settings"; // add more names as needed
  className?: string;
}

const icons: Record<string, JSX.Element> = {
  home: (
    <svg
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 24 24"
      fill="currentColor"
      className="w-6 h-6"
    >
      <path d="M12 3l9 8h-3v9H6v-9H3l9-8z" />
    </svg>
  ),
  user: (
    <svg
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 24 24"
      fill="currentColor"
      className="w-6 h-6"
    >
      <path d="M12 12c2.7 0 5-2.3 5-5s-2.3-5-5-5-5 2.3-5 5 2.3 5 5 5z" />
      <path d="M4 20c0-3.3 2.7-6 6-6h4c3.3 0 6 2.7 6 6v1H4v-1z" />
    </svg>
  ),
  settings: (
    <svg
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 24 24"
      fill="currentColor"
      className="w-6 h-6"
    >
      <path d="M12 8a4 4 0 100 8 4 4 0 000-8zm9.4 4a7.4 7.4 0 01-.3 2l2.1 1.7-2 3.5-2.5-1a7.4 7.4 0 01-1.7 1l-.4 2.7H9.4l-.4-2.7a7.4 7.4 0 01-1.7-1l-2.5 1-2-3.5 2.1-1.7a7.4 7.4 0 01-.3-2c0-.7.1-1.3.3-2L2.5 8.3l2-3.5 2.5 1a7.4 7.4 0 011.7-1l.4-2.7h4.8l.4 2.7a7.4 7.4 0 011.7 1l2.5-1 2 3.5-2.1 1.7c.2.6.3 1.3.3 2z" />
    </svg>
  ),
};

export default function Icon({ name, className = "" }: IconProps) {
  return React.cloneElement(icons[name], {
    className: `${icons[name].props.className} ${className}`,
  });
}

https://apidog.com/blog/free-cursor-ai/

```
