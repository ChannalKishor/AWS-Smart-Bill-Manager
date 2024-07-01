# SmartBill Manager

SmartBill Manager is a Node.js application that serves as a robust backend service for managing bill and file information. It allows authenticated users to upload and manage bills, each linked to an image file. Authentication is handled via basic auth to ensure secure access.

## Features

- **User Authentication**: Secure creation and authentication of users using basic auth.
- **Bill Management**: Create, update, and delete bill information.
- **File Attachment**: Attach image files to bills. Files are uploaded as `multipart/form-data` and saved to an S3 bucket when deployed on AWS, or to the `uploads/` directory when running locally.

## API Endpoints

### User

- **GET** `/v1/user/self`: Retrieve information about the current user.
- **PUT** `/v1/user/self`: Update information for the current user.
- **POST** `/v1/user`: Create a new user.

### Bill

- **GET** `/v1/bill`: List all bills created by the current user.
- **GET** `/v1/bills/due/:days`: List all bills due in the next `:days` days.
- **POST** `/v1/bill`: Create a new bill.
- **GET** `/v1/bill/:billId`: Retrieve a specific bill by its ID.
- **PUT** `/v1/bill/:billId`: Update a specific bill by its ID.
- **DELETE** `/v1/bill/:billId`: Delete a specific bill by its ID.

### File

- **POST** `/v1/bill/:billId/file`: Attach a file to a specific bill by its ID.
- **GET** `/v1/bill/:billId/file/:fileId`: Retrieve a specific file linked to a bill.
- **DELETE** `/v1/bill/:billId/file/:fileId`: Delete a specific file linked to a bill.

## Getting Started

To start the application, follow these steps:

1.  **Install npm packages**

    bash

    Copy code

    `npm install`

2.  **Run the application server**

    bash

    Copy code

    `npm start`

3.  **Test the application**

    bash

    Copy code

    `npm test`

The application will run on the port specified by the environment variable `EXPRESS_PORT` or default to port 3000.

You can access the app at [http://localhost:3000/](http://localhost:3000/).
