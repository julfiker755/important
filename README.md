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

```js
import { useEffect, useState } from "react";
import { useForm } from "react-hook-form";
import Input from "../../../../../components/input";
import MainCard from "../../../../../components/card";
import useApi from "./../../../../../hooks/use-api/index";
import { IoEyeOffOutline, IoEyeOutline } from "react-icons/io5";
import toast from "react-hot-toast";
import { useParams } from "react-router-dom";

const AffiliateUpdate= () => {
  const [sendEmail, setSendEmail] = useState(false);
  const [showPassword, setShowPassword] = useState(false);
  const [confirmShowPassword, setConfirmShowPassword] = useState(false);
  const [singleData,setSingledata]=useState([])
  const {id}=useParams()
  const {register,handleSubmit,setValue,formState: { errors },reset} = useForm();
  // Handle checkbox change
  const handleCheckboxChange = (event) => {
    const data = event.target.checked;
    console.log("first checkbox value is", data);
    setSendEmail(event.target.checked);
  };

  console.log(singleData)
  // setCountry
  useEffect(()=>{
    (async()=>{
      await useApi
      .get(`/v1/admin/affiliate/${id}`)
      .then((response) => {
        setSingledata(response.data.data)
        reset(response.data.data)
        console.log(response.data.data)
      })
      .catch((error) => {
        console.log(error);
      });
    })()
  },[id,reset])

  const onSubmit = async (data) => {
    if (data?.password !== data?.password_confirmation) {
      return toast.error("password doesn't match!");
    }
  


    const formData = {
      firstName:data.firstName,
      lastName: data?.lastName,
      email: data?.email,
      password: data?.password,
      phone: data?.phone_number,
      imHandler: data?.imHandler,
      imHandlerUsername: data?.imHandlerUsername,
      addressLineOne: data?.addressLineOne,
      city: data?.city,
      state: data?.state,
      country: data.country,
      zipCode: data?.zipCode,
      status: data.status,
    };
   
    // console.log(data)

    await useApi
      .put(`/v1/admin/affiliate/update/${id}`, formData)
      .then((res) => {
        if (res?.data?.success === true) {
          toast.success("Affiliate successfully updated", {
            duration: 4000,
            position: "top-right",
          });
        }
      })
      .catch((error) => {
        console.log(error);
      });

    // reset
     
  };
  const togglePasswordVisibility = () => {
    setShowPassword((prev) => !prev);
  };

  const toggleConfirmPasswordVisibility=()=>{
    setConfirmShowPassword((prev)=>!prev)
  }



  const data = [
    { id: 1, country_name: "United States" },
    { id: 2, country_name: "Canada" },
    { id: 3, country_name: "United Kingdom" },
    { id: 4, country_name: "Germany" },
    { id: 5, country_name: "France" },
    { id: 6, country_name: "Australia" },
    { id: 7, country_name: "Japan" },
    { id: 8, country_name: "China" },
    { id: 9, country_name: "Brazil" },
    { id: 10, country_name: "India" },
    { id: 11, country_name: "Mexico" },
    { id: 12, country_name: "Russia" },
    { id: 13, country_name: "South Korea" },
    { id: 14, country_name: "Italy" },
    { id: 15, country_name: "Spain" },
    { id: 16, country_name: "Netherlands" },
    { id: 17, country_name: "Switzerland" },
    { id: 18, country_name: "Sweden" },
    { id: 19, country_name: "Norway" },
    { id: 20, country_name: "Denmark" },
    { id: 21, country_name: "Finland" },
    { id: 22, country_name: "Belgium" },
    { id: 23, country_name: "Austria" },
    { id: 24, country_name: "Portugal" },
    { id: 25, country_name: "Greece" },
    { id: 26, country_name: "New Zealand" },
    { id: 27, country_name: "Ireland" },
    { id: 28, country_name: "Singapore" },
    { id: 29, country_name: "South Africa" },
    { id: 30, country_name: "Argentina" },
  ];


  return (
    <MainCard title="Edit Advertiser">
      <div>
        <form
          onSubmit={handleSubmit(onSubmit)}
          className="flex flex-col gap-2 w-full mt-8 space-y-3"
        >
          <div className="flex items-center justify-center gap-5 w-full ">
            <Input
              label="First Name"
              name="firstName"
              placeholder="firstName"
              errors={errors}
              register={register}
            />
            <Input
              label="Last Name"
              name="lastName"
              placeholder="lastName"
              errors={errors}
              register={register}
            />
          </div>
          <div className="flex items-center justify-center gap-5 w-full ">
            <Input
              label="Email"
              name="email"
              type="email"
              placeholder="Email Address"
              errors={errors}
              register={register}
            />
            <Input
              label="Phone"
              name="phone_number"
              placeholder="Phone Number"
              errors={errors}
              register={register}
            />
          </div>
          <div className="flex items-center justify-center flex-col md:flex-row lg:flex-row gap-5  mb-5">
            <div className="w-full relative">
              <Input
                label="Password"
                name="password"
                type={showPassword ? "text" : "password"}
                placeholder="Password"
                errors={errors}
                register={register}
              />
              {showPassword ? (
                <IoEyeOutline
                  className="absolute right-2 top-10 cursor-pointer text-lg text-gray-500"
                  onClick={togglePasswordVisibility}
                />
              ) : (
                <IoEyeOffOutline
                  className="absolute right-2 top-10 cursor-pointer text-lg text-gray-500"
                  onClick={togglePasswordVisibility}
                />
              )}
            </div>
            <div className="w-full relative">
              <Input
                label="Repeate Password"
                name="password_confirmation"
                defaultValue={singleData.password}
                type={confirmShowPassword ? "text" : "password"}
                placeholder="Repeate Password"
                errors={errors}
                register={register}
              />
              {confirmShowPassword ? (
                <IoEyeOutline
                  className="absolute right-2 top-10 cursor-pointer text-lg text-gray-500"
                  onClick={toggleConfirmPasswordVisibility}
                />
              ) : (
                <IoEyeOffOutline
                  className="absolute right-2 top-10 cursor-pointer text-lg text-gray-500"
                  onClick={toggleConfirmPasswordVisibility}
                />
              )}
            </div>
          </div>
          <div className=" flex items-center justify-center flex-col md:flex-row lg:flex-row gap-5 mb-5">
            <div className="w-full">
              <label className="label" htmlFor="imHandler">
                <span className="label-text font-serif">IM Handler</span>
              </label>
              <select
                {...register("imHandler",{ required: true })}
                onChange={(e) => setValue("imHandler", e.target.value)}
                className="input-select-field text-gray-400"
              >
                <option value="whatsApp">WhatsApp</option>
                <option value="telegram">Telegram</option>
                <option value="skype">Skype</option>
                
              </select>
              {errors && errors.imHandler && (
                <span className="text-red-500">IM Handler is required</span>
              )}
            </div>
            <Input
              label="IM Username"
              name="imHandlerUsername"
              type="text"
              placeholder="IM Username"
              errors={errors}
              register={register}
            />
          </div>

          <Input
            label="Address Line "
            name="addressLineOne"
            placeholder="Address Line One"
            errors={errors}
            register={register}
          />
          <div className="flex items-center justify-center gap-5 w-full ">
            <Input
              label="City"
              name="city"
              placeholder="City"
              errors={errors}
              register={register}
            />
            <Input
              label="State / Region"
              name="state"
              placeholder="State / Region"
              errors={errors}
              register={register}
            />
          </div>
          <div className="flex items-center justify-center flex-col md:flex-row lg:flex-row gap-5 w-full ">
            <div className="w-full space-y-1">
              <label htmlFor="country">Country</label>
              <select
                {...register("country", { required: true })}
                onChange={(e) => setValue("country", e.target.value)}
                className="input-select-field"
                // required
              >
                {data.map((country, index) => (
                  <option  key={index} value={country?.country_name}>
                    {country?.country_name}
                  </option>
                ))}
              </select>
            </div>
            <Input
              label="ZIP Code"
              name="zipCode"
              placeholder="ZIP Code"
              errors={errors}
              register={register}
            />
          </div>
          {/* status */}
          <div className="w-full space-y-1">
            <label htmlFor="status">Status</label>
            <select
              name="status"
              {...register("status", { required: true })}
              onChange={(e) => setValue("status", e.target.value)}
              className="input-select-field"
              required
            >
                 
              <option value="pending">Pending</option>
              <option value="active">Active</option>
            </select>
          </div>
          <div className="flex items-center justify-start gap-3">
            <input
              type="checkbox"
              name="send_email"
              id="send_email"
              checked={sendEmail}
              onChange={handleCheckboxChange}
            />
            <label htmlFor="send_email" className="text-gray-500">
              Send Welcome Email
            </label>
          </div>
          <button
            type="submit"
            className="w-[140px] inline px-3 py-1 bg-blue-500 text-white rounded-md hover:bg-blue-600 transition-all duration-200"
          >
            Edit Advertiser
          </button>
        </form>
      </div>
    </MainCard>
  );
};

export default AffiliateUpdate;

```
