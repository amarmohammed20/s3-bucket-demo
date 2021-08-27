## Application Aim

To create a demo react application that demonstrates the ability to upload and retrieve objects/files from a AWS s3 bucket.

## App Build

This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

## Reference

The source of information for this application has come from "Sam Meech-Ward" who is a youtuber.
Video - https://www.youtube.com/watch?v=yGYeYJpRWPM

## Steps of App

The application will work using the following steps in the order specified:

1. Make request to server to get a secure URL for the S3 bucket. Server will have credentials for the S3 bucket and in return a S3 bucket will be created.
2. The application will send the objects/files to the S3 bucket using the secure URL.
3. Once step 2 is successfully done the app will send extra bits of information/data to the server.

## AWS S3 Bucket

To interact with the amazon S3 bucket we will be using the npm package called aws-sdk - https://www.npmjs.com/package/aws-sdk
You will need to create a S3 bucket with the following setting:

- Un-tick block public access, allowing for public access to the s3 bucket.

Create the bucket with not other changes.

- In the permissions tab edit the bucket policy to allow anyone to get objects from the bucket. Use the policy generator to make it easier. See in the images folder "aws-policy-gen". On line 11 add /\* to the end of the resource name, see image "aws-policy-gen 2".

- The CORS policy will need to be configured, to determine exactly what this should be depends on the environment. In PROD we would only allow requests from an address with our domain but in this exactly we are going to say any address can make a request. See in images the "s3 CORS policy".

- IAM user and policy will need to be created to ensure only we can add to the bucket, policy simply stating what a user can do.
  See images "IAM Policy" setup
  The access type for the user should be programmatic access. This will give us a access key and secret key which our application will use to connect to the bucket. When setting permissions chose attach existing policies directly and chose the policy you made. Once all made store these values in the .env file.
