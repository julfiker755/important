```js
 // Working With URL Params [ Request ]

//example---  http://localhost:3000/api/menu?id=1000
export const GET=async(req,res)=>{
    const {searchParams}=new URL(req.url)
    const idvalue=searchParams.get("id")
    return NextResponse.json({status:'success',message:idvalue})
}

//example---  http://localhost:3000/api/menu?id=1000](http://localhost:3000/api/menu?id=1000&roll=404428)
export const GET=async(req,res)=>{
    const {searchParams}=new URL(req.url)
    const idvalue=searchParams.get("id")
    const roll=searchParams.get("roll")
    return NextResponse.json({status:'success',roll:roll,id:idvalue})
}

```

```js
 // Working With Form Data [Request]

export const POST=async(req,res)=>{
    const fromdata=await req.formData()
    const gender=fromdata.get("gender")
    const phone=fromdata.get("phone")
    return NextResponse.json({status:'success',gender:gender,phonenum:phone})
}
```
```js
 // Working With Headers [Request]

export const GET=async(req,res)=>{
    const headerslist=headers()
    const api_key=headerslist.get('API_KEY')
    return NextResponse.json({status:'success',message:api_key})
}
```
```js
 // Working With Cookies [Request]

export const GET=async(req,res)=>{
     // const token=req.cookies.get('token')['name']
    // const token=req.cookies.get('token')['value']
    const token=req.cookies.get('token')
    return NextResponse.json({status:'success',message:token})
}

```
```js
 // Working With Status Code [Response]  -- 
export const GET=async(req,res)=>{
    return NextResponse.json(
        // {body}{status}
        {roll:'404420',name:'julfiker'},
        {
            status:203
        }
        )
}

```

```js
 // Working With Header [Response]  --

export const GET=async(req,res)=>{
    return NextResponse.json(
        {roll:'4044201',name:'julfiker'},
        {
            status:200,
            headers:{'token1':'xyz-123'}
        }
        )
}

// mutiple headers
export const GET=async(req,res)=>{
    return NextResponse.json(
        {roll:'4044201',name:'julfiker'},
        {
            status:200,
            headers:{
                'token1':'xyz-123',
                'token2':'xyz-1234',
                'token3':'xyz-1fd234'
            }
        }
        )
}

```

```js
 // Working With Cookies [Response]  --

export const GET=async(req,res)=>{
    return NextResponse.json(
        {roll:'4044201',name:'julfiker'},
        {
            status:200,
            headers:{
                'token1':'xyz-123',
                'token2':'xyz-1234',
                'Set-Cookie':'token=XYZ-123;Path=/'
            }
        }
        )
}

// multiple cookice
export const GET=async(req,res)=>{
    return NextResponse.json(
        {roll:'4044201',name:'julfiker'},
        {
            status:200,
            headers:{
                'token1':'xyz-123',
                'token2':'xyz-1234',
                'Set-Cookie':'token=XYZ-123;Path=/'
                'Set-Cookie':'token=XYjffj-123;Path=/'
            }
        }
        )
}
```
```js
// Introduce With Next.js [Middleware] -- middleware.js file use
 // setp-1
 export function middleware() {
     console.log('I am middleware')
  }

// setp-2
export function middleware() {
     console.log('I am middleware')
  }

  export const config = {
    matcher:['/api/:path*']
  }
// setp-3
export function middleware() {
     console.log('I am middleware')
  }

  export const config = {
    matcher:['/api/:path*','/dashboard/:path*']
  }
```
```js
 // Apply Specific Path On [Middleware]

export function middleware(req,res) {
     if(req.nextUrl.pathname.startsWith("/api/menu")){
     console.log("/api/menu pathname")
     return NextResponse.next()
     }else if(req.nextUrl.pathname.startsWith("/dashboard/help")){
       console.log('Dashboard layout')
       return NextResponse.next()
     }
  }
```
```js
 // Settings Header With Request [Middleware]
//example-1
export function middleware(req,res) {
     if(req.nextUrl.pathname.startsWith("/api/menu")){
      const reqheader=new Headers(req.headers)
      const token=reqheader.get('token')
      if(token === "xyz-123"){
        return NextResponse.next()
      }else{
        return NextResponse.json({message:'fail woring token'})
      }

     }
  }
// example-2
export function middleware(req, res) {
    if (req.nextUrl.pathname.startsWith("/api/menu")) {
      const reqHeaders = new Headers(req.headers);
      reqHeaders.set('phone', '01741703755');

      return NextResponse.next({
        request: {
          headers: reqHeaders,
        },
      });
    }
}
// server get example2
export const GET=async(req,res)=>{
    const headerslist=headers()
    const api_key=headerslist.get('phone')
    return NextResponse.json({phone:api_key})
}

````
```js
// Settings Header With Response [Middleware] --
export function middleware(req, res) {
    if (req.nextUrl.pathname.startsWith("/api/menu")) {
      const resnext=NextResponse.next();
      resnext.headers.set('jim','01741703755')
      resnext.headers.set('jim1','01741703755')
      return resnext
    }
}

```
