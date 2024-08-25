```js
"use client";
import * as yup from "yup";
import { yupResolver } from "@hookform/resolvers/yup";
import Button from "@/components/button";
import CountryData from "@/components/data/country-data";
import Input from "@/components/reuseable/Input";
import Select from "@/components/reuseable/Select";
import Link from "next/link";
import React, { useState } from "react";
import { Controller, useForm } from "react-hook-form";
import { IoEyeOffOutline, IoEyeOutline } from "react-icons/io5";

const schema = yup
  .object({
    name: yup.string().required("Name is required"),
    email: yup.string().email("Invalid email").required("Email is required"),
    mobile: yup.string().required("Mobile number is required"),
    skype: yup.string().required("Skype address is required"),
    password: yup.string().required("Password is required"),
    repeatPassword: yup
      .string()
      .oneOf([yup.ref("password"), null], "Passwords do not match")
      .required("Password confirmation is required"),
    country: yup
      .object({
        value: yup.string().required("Country is required"),
        label: yup.string().required(),
      })
      .required("Country is required"),
  })
  .required();

function FreeTrialFrom() {
  const [showPassword, setShowPassword] = useState(false);
  const [repeatPassword, setRepeatPassword] = useState(false);
  const {
    control,
    handleSubmit,
    formState: { errors: formErrors },
    reset,
  } = useForm({
    resolver: yupResolver(schema),
  });

  const onSubmit = async (data) => {
    const formData = {
      name: data.name,
      email: data.email,
      country: data.country.label,
      mobile: data.mobile,
      skype: data.skype,
      password: data.password,
    };

    console.log(formData);

    // try {
    //   const res = await useApi.post("/v1/admin/advertiser/store", formData);
    //   if (res?.data?.success) {
    //     toast.success("Advertiser Created Successfully", {
    //       duration: 4000,
    //       position: "top-right",
    //     });
    //     reset();
    //   }
    // } catch (error) {
    //   console.error(error);
    // }
  };

  return (
    <div>
      <h1 className="text-3xl font-bold pb-5">Create an Account</h1>
      <p className="text-gray-500 text-lg">
        Get started with your free account today. No credit card needed and no setup fees.
      </p>
      <form onSubmit={handleSubmit(onSubmit)}>
        <div className="py-10 space-y-4">
          <Controller
            name="name"
            control={control}
            render={({ field, fieldState: { error } }) => (
              <Input
                label="Name:"
                placeholder="Enter Your Name"
                errorMessage={error?.message}
                {...field}
              />
            )}
          />
          <Controller
            name="email"
            control={control}
            render={({ field, fieldState: { error } }) => (
              <Input
                label="Company Email:"
                placeholder="Enter Your Email"
                errorMessage={error?.message}
                {...field}
              />
            )}
          />
          <Controller
            name="country"
            control={control}
            render={({ field, fieldState: { error } }) => (
             <Select
                label="Country:"
                options={CountryData}
                placeholder="Select the Country"
                labelColor="text-gray-700"
                color="gray"
                search={true}
                errorMessage={error?.value?.message}
                {...field}
              />
            )}
          />
          <Controller
            name="mobile"
            control={control}
            render={({ field, fieldState: { error } }) => (
              <Input
                label="Mobile Number:"
                placeholder="Enter Your Mobile Number"
                errorMessage={error?.message}
                {...field}
              />
            )}
          />
          <Controller
            name="skype"
            control={control}
            render={({ field, fieldState: { error } }) => (
              <Input
                label="Skype Address:"
                placeholder="Enter Your Skype Address"
                errorMessage={error?.message}
                {...field}
              />
            )}
          />
          <div className="w-full relative">
            <Controller
              name="password"
              control={control}
              render={({ field, fieldState: { error } }) => (
                <Input
                  label="Password"
                  type={showPassword ? "text" : "password"}
                  placeholder="Password"
                  errorMessage={error?.message}
                  {...field}
                />
              )}
            />
            {showPassword ? (
              <IoEyeOutline
                className="absolute right-5 top-[34px] cursor-pointer text-lg text-gray-500"
                onClick={() => setShowPassword(!showPassword)}
              />
            ) : (
              <IoEyeOffOutline
                className="absolute right-5 top-[34px] cursor-pointer text-lg text-gray-500"
                onClick={() => setShowPassword(!showPassword)}
              />
            )}
          </div>
          <div className="w-full relative">
            <Controller
              name="repeatPassword"
              control={control}
              render={({ field, fieldState: { error } }) => (
                <Input
                  label="Repeat Password"
                  type={repeatPassword ? "text" : "password"}
                  placeholder="Repeat Password"
                  errorMessage={error?.message}
                  {...field}
                />
              )}
            />
            {repeatPassword ? (
              <IoEyeOutline
                className="absolute right-5 top-[34px] cursor-pointer text-lg text-gray-500"
                onClick={() => setRepeatPassword(!repeatPassword)}
              />
            ) : (
              <IoEyeOffOutline
                className="absolute right-5 top-[34px] cursor-pointer text-lg text-gray-500"
                onClick={() => setRepeatPassword(!repeatPassword)}
              />
            )}
          </div>
          <div className="flex gap-2 pt-2">
            <input
              className="w-5 h-4 text-blue-600 mt-[6px] border-gray-500 rounded"
              type="checkbox"
            />
            <p className="text-lg">
              By signing up you agree to the{" "}
              <Link
                className="text-link-color underline"
                href={"/terms-and-conditions"}
              >
                Terms & Conditions
              </Link>{" "}
              and{" "}
              <Link
                className="text-link-color underline"
                href={"/privacy-policies"}
              >
                Privacy Policy
              </Link>
            </p>
          </div>
          <Button className="!px-10 !mt-6">Submit</Button>
        </div>
      </form>
    </div>
  );
}

export default FreeTrialFrom;

```


