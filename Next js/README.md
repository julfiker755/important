```js
//css use https://github.com/vercel/next.js/tree/canary/examples
// post.module.css
```
```js
   //security
   // Webp
   // layout="responsive"
   // layout="fixed"
   // priority
   <Image 
   alt="cover photo"
   width={200}
   height={200}
   layout='responsive'
   priority
   src="https://img.freepik.com/free-photo/young-bearded-man-with-striped-shirt_273609-5677.jpg">
   </Image>
```

```js
//{cache:'no-store'}
//{ cache: 'force-cache' }
//{next:{revalidate:5}}
const res=await fetch("http://localhost:2000/data", { cache: 'no-cache'})
const postdaa=await res.json()
````
```js
//map.slice(0,10) use limit for use
export async function generateStaticParams() {
  const res=await fetch("http://localhost:2000/data")
  const postdaa=await res.json()
  const ids=postdaa.map(d=>{
    return {
      id:d.id+""
    }
  })
  return ids
  // return [{ id: '1' }, { id: '2' }]
}
```
```js
//****************NextConfig***************

// images --
const nextConfig = {
    images:{
        domains:["images.pexels.com"]
    }
}


// base path --
const nextConfig = {
    basePath:'/submenu'
};

// env file --
const nextConfig = {
    env:{
        API_KEY:'fjfjdlfjdl'
    }
};

// headers --
const nextConfig = {
   async headers(){
     return [
        // {source:'/product',headers:[{key:'my-value',value:'123434'}]}
        {source:'/:path*',headers:[{key:'my-value',value:'123434'}]}
     ]
   }
};

// iframe use website --
const nextConfig = {
   async headers(){
     return [
        // {source:'/:path*',headers:[{key:'X-Frame-Options',value:'SAMEORIGIN'}]} // how to iframe use my website but other not use
        {source:'/:path*',headers:[{key:'X-Frame-Options',value:'DENY'}]} // how to not use iframe ,my website,other
     ]
   }
};


// Powered By --
const nextConfig = {
    poweredByHeader: false,
};


```
```js
// server side
const Dynamicpage = ({params,searchParams}) => {
    console.log(params)
    return (
        <div>
            <h1>Hello dynamic page-{params.id}</h1>
            <h1>search parms {searchParams.email}</h1>
        </div>
    );
};
```
```js
// client side
const Dynamicpage = () => {
     // const params = useParams()
  const searchParams = useSearchParams()
  const search = searchParams.get('search')

    return (
        <div>
            <h1>Hello dynamic page</h1>
        </div>
    );
};

```

