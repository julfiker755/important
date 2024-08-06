```js
import { Pagination } from "@/components/reuseable/pagination";


function Blogs({ searchParams: { page } }) {
 const {data,total,per_page}=await getBlogs(page)

  const paginationCalculation = {
    page: page,
    hasNextPage: (page * per_page) < total,
    totalPages: Math.ceil(total / per_page)
  };


  return (
      <div className="w-full lg:w-[400px] m-auto pt-5 pb-10">
          <Pagination {...paginationCalculation} />
     </div>
  );
}

export default Blogs;

```

```js
import Link from "next/link";
import { HiChevronDoubleLeft } from "react-icons/hi";
import { HiChevronDoubleRight } from "react-icons/hi";

export function Pagination({ page=1, totalPages, hasNextPage }) {
  const currentPage = Math.min(Math.max(Number(page), 1), totalPages);

  function getPagesToShow() {
    let startPage = currentPage - 2;
    let endPage = currentPage + 2;
  
    startPage = Math.max(1, startPage); 
    endPage = Math.min(totalPages, endPage); 
 

    if (startPage === 1) {
      endPage = Math.min(totalPages, 5); 
    } else if (endPage === totalPages) {
      startPage = Math.max(1, totalPages - 4); 
    }
  
    return Array.from(
      { length: endPage - startPage + 1 },
      (_, index) => startPage + index
    );
  }
  
  const pages = getPagesToShow();

  return (
    <div className="flex items-center justify-center space-x-6 text-black">
      {/* Previous Page Link */}
      <Link
        className={`rounded-md border border-gray-300 px-3 py-[9px] text-sm font-medium hover:bg-gray-50 
          ${currentPage === 1 ? 'pointer-events-none bg-gray-100' : ''}`}
        href={`?page=${currentPage - 1}`}
      >
       <HiChevronDoubleLeft/>
      </Link>

      {/* Page Number Links */}
      <nav
        aria-label="Pagination"
        className="relative z-0 inline-flex -space-x-px rounded-md"
      >
        {pages.map((pageItem, index) => (
          <Link
            key={pageItem}
            className={`
              relative inline-flex items-center border border-gray-300 px-4 py-2 text-sm font-medium hover:bg-gray-50'
              ${pageItem === currentPage ? 'pointer-events-none bg-affity-color !text-white' : ''}
              ${index === 0 ? 'rounded-l-md' : ''}
              ${index === pages.length - 1 ? 'rounded-r-md' : ''}
            `}
            href={`?page=${pageItem}`}
          >
            {pageItem}
          </Link>
        ))}
      </nav>

      {/* Next Page Link */}
      <Link
        className={`rounded-md border border-gray-300 px-3 py-[9px] text-sm font-medium hover:bg-gray-50'
         ${!hasNextPage ? 'pointer-events-none bg-gray-100' : ''}`}
        href={`?page=${currentPage + 1}`}
      >
        <HiChevronDoubleRight/>
      </Link>
    </div>
  );
}
```
