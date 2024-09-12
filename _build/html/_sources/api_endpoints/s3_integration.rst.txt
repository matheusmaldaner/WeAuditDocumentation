S3 Integration
==============

Amazon S3 provides robust and secure storage for WeAudit, storing generated images and other digital assets. This section outlines how WeAudit integrates S3 to manage and retrieve these resources efficiently.

Endpoint Overview
-----------------

**/images/upload**
   - **Method**: POST
   - **Description**: Uploads generated images to an S3 bucket.
   - **Request Body**:

     .. code-block:: json

        {
            "image_data": "<base64_encoded_data>",
            "content_type": "image/jpeg",
            "image_id": "unique_image_identifier"
        }

   - **Response**:

     .. code-block:: json

        {
            "status": "success",
            "message": "Image uploaded successfully.",
            "url": "https://s3.amazonaws.com/yourbucket/unique_image_identifier.jpg"
        }

Integration Details
-------------------

- **Bucket Configuration**: Set up and configure an S3 bucket with appropriate permissions and policies to ensure secure storage and access.
- **Data Transfer**: Use AWS SDKs to handle data uploads and retrievals, ensuring data is encrypted in transit and at rest.

Example Usage
-------------

.. code-block:: python

    import boto3

    def upload_image_to_s3(image_data, content_type, image_id):
        s3 = boto3.client('s3')
        s3.put_object(
            Bucket='your-s3-bucket',
            Key=image_id,
            Body=image_data,
            ContentType=content_type
        )

This function demonstrates how to upload an image to an S3 bucket using the AWS SDK for Python (Boto3).
