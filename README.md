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
