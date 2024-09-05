```sh
npm i react-responsive-pagination
```

```js
import React, { useState } from 'react';
import ResponsivePagination from 'react-responsive-pagination';
import 'react-responsive-pagination/themes/classic.css';


function MyApp() {
  const [currentPage, setCurrentPage] = useState(8);
  const totalPages = 20;

  return (
    <ResponsivePagination
      current={currentPage}
      total={totalPages}
      onPageChange={setCurrentPage}
    />
  );

```

```js
// **********custom responsive pagination all custom design************
import ResponsivePagination from 'react-responsive-pagination';
import { ChevronLeft, ChevronRight } from "lucide-react"
import { cn } from "@/lib/utils"
function Pagination({ page, setPage, totalPage, per_page,className}) {
    const total = Math.ceil(totalPage / per_page)
    return (
        <div className={cn("w-full", className)}>
            <ResponsivePagination
            previousLabel={<ChevronLeft className="h-4 w-4" />} nextLabel={<ChevronRight className="h-4 w-4" />}
            className="flex flex-row items-center gap-1 w-full"
            pageItemClassName="h-10 border w-10 flex items-center justify-center whitespace-nowrap rounded-md text-sm font-medium hover:bg-accent hover:text-accent-foreground"
            pageLinkClassName="h-10 w-10 flex items-center justify-center"
            activeItemClassName="bg-accent border rounded-md"
            disabledItemClassName="hover:!bg-transparent"
            current={page}
            total={total}
            onPageChange={setPage}
        />
        </div>
    )
}
export default Pagination
```
