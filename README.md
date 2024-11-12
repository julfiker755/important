
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
```
