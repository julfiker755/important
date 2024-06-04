```js
/* Custom scrollbar */
/* Width */
::-webkit-scrollbar {
  width: 5px;
  border-radius: 6px;
}


/* Track */
::-webkit-scrollbar-track {
  background: #e0e9f4;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: #1890ff;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #1890ff;
}
```
```js
// fetch client
   useEffect(()=>{
    (async()=>{
         const blog=(await (await fetch(`${process.env.API_URL}/get-latest-blogs`)).json())["data"]
         setlatestblog(blog)
    })()
   },[])

// fetch server side
async function getdata(){
    let social=(await (await fetch(`${process.env.HOST}/api/social`,{ cache: 'no-cache' })).json())['data']
    let categories=(await (await fetch(`${process.env.HOST}/api/categories`,{ cache: 'no-cache' })).json())['data']
    return {social,categories}
}
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
### Fetching data on the Server with third-party libraries
```js
// No catch data 
async function getplecholder(){
   return axios.get("https://randomuser.me/api")
}

 const Rootpage = async() => {
  const getdata=await getplecholder()
  console.log(getdata)
  return (
    <div>
       <h1>{getdata?.data?.results[0].gender}</h1>
    </div>
  );
};
```
```js
const getplecholder=cache(()=>{
  return axios.get("https://randomuser.me/api")
})
```

### server action 

```js
import React from 'react';


 const Rootpage = async() => {

  const addUser=async(fromData)=>{
    'use server'
     const email=fromData.get("email")
     const password=fromData.get("password")
     console.log(email,password)

  }
  return (
    <div>
      <div className="bg-white py-6 sm:py-8 lg:py-12">
  <div className="mx-auto max-w-screen-2xl px-4 md:px-8">
    <h2 className="mb-4 text-center text-2xl font-bold text-gray-800 md:mb-8 lg:text-3xl">Login</h2>

    <form action={addUser} className="mx-auto max-w-lg rounded-lg border">
      <div className="flex flex-col gap-4 p-4 md:p-8">
        <div>
          <label for="email" className="mb-2 inline-block text-sm text-gray-800 sm:text-base">Email</label>
          <input name="email" type="email" className="w-full rounded border bg-gray-50 px-3 py-2 text-gray-800 outline-none ring-indigo-300 transition duration-100 focus:ring" />
        </div>

        <div>
          <label for="password" className="mb-2 inline-block text-sm text-gray-800 sm:text-base">Password</label>
          <input name="password" type="text" className="w-full rounded border bg-gray-50 px-3 py-2 text-gray-800 outline-none ring-indigo-300 transition duration-100 focus:ring" />
        </div>

        <button type="submit" className="block rounded-lg bg-gray-800 px-8 py-3 text-center text-sm font-semibold text-white outline-none ring-gray-300 transition duration-100 hover:bg- 
       gray-700 focus-visible:ring">Log in</button>
      </div>

    </form>
  </div>
</div>
    </div>
  );
};

export default Rootpage;
```

