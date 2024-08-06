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
