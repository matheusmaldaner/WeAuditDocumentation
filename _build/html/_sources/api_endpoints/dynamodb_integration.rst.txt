DynamoDB Integration
====================

DynamoDB serves as the primary database for WeAudit, storing metadata, user data, and operation logs. The integration ensures efficient data management and retrieval.

Endpoint Overview
-----------------

**/data/store**
   - **Method**: POST
   - **Description**: Stores or updates image metadata in the DynamoDB table.
   - **Request Body**:

     .. code-block:: json

        {
            "imageId": "123456",
            "metadata": {
                "prompt": "A serene lake at sunset",
                "generationDate": "2024-07-12"
            }
        }

   - **Response**:

     .. code-block:: json

        {
            "status": "success",
            "message": "Data stored successfully."
        }

Data Management
---------------

- **Schema Design**: Design tables to optimize for the most frequent access patterns.
- **Security**: Use AWS IAM roles to securely access DynamoDB from the WeAudit application.
- **Performance**: Monitor and adjust read/write capacity to handle load effectively.

Example Data Retrieval
----------------------

.. code-block:: python

    import boto3

    def retrieve_metadata(image_id):
        dynamodb = boto3.resource('dynamodb')
        table = dynamodb.Table('ImageMetadata')
        response = table.get_item(Key={'imageId': image_id})

        return response['Item']

This snippet shows how to retrieve image metadata from DynamoDB using the AWS SDK for Python (Boto3).
