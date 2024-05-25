```js
 // Email Sending
// example url = http://localhost:3000/api/email?email=julfiker755.bd@gmail.com
import { NextResponse } from "next/server"
import nodemailer from 'nodemailer'

export const GET=async(req,res)=>{
    const {searchParams}=new URL(req.url)
    const toemail=searchParams.get("email")

    //  transporter
    let transporter = nodemailer.createTransport({
        host: "mail.teamrabbil.com",
        port: 25,
        secure: false,
        auth: {
          user: "info@teamrabbil.com",
          pass: "~sR4[bhaC[Qs",
        },
        tls:{rejectUnauthorized:false}
      });

    //  sendMail
    let myemail = await transporter.sendMail({
        from: '"Send the emai provider " <info@teamrabbil.com>', 
        to:toemail,
        subject: "Text nex js Email", 
        text: "Hello world ??", 
      });
  try{
    await transporter.sendMail(myemail)
    return NextResponse.json({message:'success email'})
  }catch(err){
    return NextResponse.json({message:'fail email'})
  }
   
}
```

```js
// JWT TOKEN ENCODE ---
import {SignJWT,jwtVerify} from 'jose'
import { NextResponse } from 'next/server'

export const GET=async(req,res)=>{
    const key=new TextEncoder().encode(process.env.secert_key)
    const paylod={email:'Julfiker755.bd@gmail.com',user_id:'40840'}
    let token=await new SignJWT(paylod)
         .setProtectedHeader({alg:'HS256'})
         .setIssuedAt()
         .setIssuer("http://localhost:3000")
         .setExpirationTime('2h')
         .sign(key)

    return NextResponse.json({token:token})
}
```
```js
//JWT TOKEN DECODE

import {SignJWT,jwtVerify} from 'jose'
import { NextResponse } from 'next/server'

export const POST=async(req,res)=>{
  const jsonbody=await req.json()
  const Token=jsonbody['token']
  const key=new TextEncoder().encode(process.env.secert_key) 
  const decoded=await jwtVerify(Token,key)
  return NextResponse.json(decoded)
}
```
```js
// login --
import { NextResponse } from "next/server"
import {SignJWT,jwtVerify} from 'jose'

export const POST=async(req,res)=>{
    const jsonbody=await req.json()
    const username=jsonbody['user']
    const userpassword=jsonbody['password']
    // database check
    if(username === "ABC" && userpassword === "123"){
        const payload={username:username,userpassword:userpassword}
        const key=new TextEncoder().encode(process.env.secert_key)
        let token=await new SignJWT(payload)
         .setProtectedHeader({alg:'HS256'})
         .setIssuedAt()
         .setIssuer("http://localhost:3000")
         .setExpirationTime('2h')
         .sign(key)
         return NextResponse.json({status:'success',message:'Login success',token})
    }else{
        return NextResponse.json({status:'fail',message:'Not Login success'})
    }
    
    
  }
```

> next js/login/middleware/ [github source code](https://github.com/julfiker755/jwt-authentication-nextjs)
