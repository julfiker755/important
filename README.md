```js
npx shadcn@latest button add input label  textarea table sonner skeleton dialog
 npm i js-cookie date-fns dayjs tailwind-scrollbar-hide use-debounce zod

```
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
export const DashboardIcon = (props: React.SVGProps<SVGSVGElement>) => (
    <svg width="22" height="23" viewBox="0 0 22 23" fill="currentColor" xmlns="http://www.w3.org/2000/svg" {...props}>
        <path d="M7.27784 13.1216H3.08865C2.53361 13.1248 2.00238 13.3475 1.61102 13.741C1.21967 14.1346 0.999992 14.6671 1 15.2222V19.4114C0.999717 19.6857 1.05355 19.9574 1.15841 20.211C1.26327 20.4645 1.41711 20.6949 1.61112 20.8889C1.80512 21.0829 2.03549 21.2367 2.28902 21.3416C2.54256 21.4465 2.81428 21.5003 3.08865 21.5H7.27784C7.83296 21.5006 8.36566 21.2811 8.7592 20.8895C9.15274 20.498 9.37501 19.9665 9.3773 19.4114V15.2222C9.37758 14.9464 9.32347 14.6732 9.21806 14.4184C9.11266 14.1635 8.95802 13.932 8.76301 13.737C8.568 13.542 8.33645 13.3873 8.0816 13.2819C7.82676 13.1765 7.55362 13.1224 7.27784 13.1227M7.27784 1.5H3.08865C2.81428 1.49972 2.54256 1.55355 2.28902 1.65841C2.03549 1.76327 1.80512 1.91711 1.61112 2.11112C1.41711 2.30512 1.26327 2.53549 1.15841 2.78902C1.05355 3.04256 0.999717 3.31428 1 3.58865V7.77784C0.999424 8.33296 1.21895 8.86566 1.61046 9.2592C2.00197 9.65274 2.53354 9.87501 3.08865 9.8773H7.27784C7.55362 9.87758 7.82676 9.82347 8.0816 9.71806C8.33645 9.61266 8.568 9.45802 8.76301 9.26301C8.95802 9.068 9.11266 8.83645 9.21806 8.5816C9.32347 8.32676 9.37758 8.05362 9.3773 7.77784V3.58865C9.37501 3.03354 9.15274 2.50197 8.7592 2.11046C8.36566 1.71895 7.83296 1.49942 7.27784 1.5ZM18.9114 1.5H14.7222C14.167 1.49942 13.6343 1.71895 13.2408 2.11046C12.8473 2.50197 12.625 3.03354 12.6227 3.58865V7.77784C12.623 8.33456 12.8443 8.8684 13.2379 9.26206C13.6316 9.65573 14.1654 9.87701 14.7222 9.8773H18.9114C19.4665 9.87501 19.998 9.65274 20.3895 9.2592C20.7811 8.86566 21.0006 8.33296 21 7.77784V3.58865C21.0003 3.31428 20.9465 3.04256 20.8416 2.78902C20.7367 2.53549 20.5829 2.30512 20.3889 2.11112C20.1949 1.91711 19.9645 1.76327 19.711 1.65841C19.4574 1.55355 19.1857 1.49972 18.9114 1.5ZM16.8108 13.1216C15.6998 13.1216 14.6342 13.563 13.8486 14.3486C13.063 15.1342 12.6216 16.1998 12.6216 17.3108C12.6216 18.4219 13.063 19.4874 13.8486 20.273C14.6342 21.0586 15.6998 21.5 16.8108 21.5C17.9219 21.5 18.9874 21.0586 19.773 20.273C20.5586 19.4874 21 18.4219 21 17.3108C21 16.1998 20.5586 15.1342 19.773 14.3486C18.9874 13.563 17.9219 13.1216 16.8108 13.1216Z" stroke="white" strokeWidth="1.5" strokeLinecap="round" strokeLinejoin="round" />
    </svg>
 
 
 
);

https://apidog.com/blog/free-cursor-ai/

```


``js
 {
        path: 'chats',
        lazy: async () => ({
          Component: (await import('@/components/coming-soon')).default,
        }),
      },
      {
        path: 'users',
        lazy: async () => ({
          Component: (await import('@/components/coming-soon')).default,
        }),
      },
      {
        path: 'analysis',
        lazy: async () => ({
          Component: (await import('@/components/coming-soon')).default,
        }),
      },
```
