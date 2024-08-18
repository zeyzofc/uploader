# s3-uploader

This is a simple example application that uploads to an S3 bucket using Express.js and the AWS SDK.

The aim of this project is to provide a easy way for users to get a direct link to a file with less than 30MB.

Be warned that this is a one-way trip, there is no way to delete files and there are no spam restrictions in place. This means that if this is served as a public application, **anyone will be able to upload to your S3 bucket**. Consider using an [OAuth proxy](https://oauth2-proxy.github.io/oauth2-proxy/) to ensure authentication.

If you don't have a S3 Bucket, remember you can always host a [MinIO](https://min.io/) instance as those are fully compatible with AWS S3 API.

## Prerequisites

- Node.js (v12 or higher)
- AWS S3 credentials (S3 Bucket, Access Key ID and Secret Access Key)

## Getting Started

1. Clone the repository change to its directory.

2. Install dependencies with `yarn install`.

3. Set up environment variables that identify your S3 bucket

```
S3_REGION
S3_ACCESS_KEY
S3_SECRET_ACCESS_KEY
S3_BUCKET_NAME
```

You can achieve this by simply adding a `.env` file with your AWS credentials to the directory.

4. Start the server with `yarn start`.

5. Open your web browser and navigate to http://localhost:8080.

6. Select a file using the file input and click the "Upload" button. The file will be uploaded to the configured S3 bucket, and the public URL of the file will be displayed below.

## Run with Docker

This repository includes a Dockerfile to run the application in a containerized environment.

Just run it like every other Docker container:

```
docker build . -t s3-file-uploader
docker run -p 8080:8080 \
-e S3_REGION=your_region \
-e S3_ACCESS_KEY_ID=your_access_key \
-e S3_SECRET_ACCESS_KEY=your_secret_key \
-e S3_BUCKET_NAME=your_bucket_name \
-d s3-file-uploader 
```

## License

This project is licensed under the MIT License.
