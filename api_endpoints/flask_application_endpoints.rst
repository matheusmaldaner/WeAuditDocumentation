Flask Application Endpoints
===========================

WeAudit's Flask application provides a series of RESTful API endpoints to facilitate the interaction between the front-end and the back-end services. These endpoints are crucial for the operational flow of the platform.

Endpoint Overview
-----------------

1. **/predict**: Generates images based on text prompts.
2. **/status/{prediction_id}**: Checks the status of an image generation request.
3. **/generate**: Generates a set of images based on the given prompt and parameters.

Detailed Descriptions
---------------------

**/predict Endpoint**
   - **Method**: POST
   - **Description**: Accepts a text prompt and optional parameters to generate images.
   - **Request Body**:

     .. code-block:: json

        {
            "prompt": "A sunset over a city skyline",
            "parameters": {
                "model": "stable-diffusion",
                "num_images": 5
            }
        }

   - **Response**:

     .. code-block:: json

        {
            "prediction_id": "abc123",
            "status_url": "/status/abc123"
        }

**/status/{prediction_id} Endpoint**
   - **Method**: GET
   - **Description**: Returns the status and result of an image generation request.
   - **Response**:

     .. code-block:: json

        {
            "status": "completed",
            "images": [
                "url1.jpg",
                "url2.jpg"
            ]
        }

**/generate Endpoint**
   - **Method**: POST
   - **Description**: Directly generates images based on the provided prompt and returns their URLs.
   - **Request Body**:

     .. code-block:: json

        {
            "prompt": "A snowy mountain landscape",
            "num_images": 3
        }

   - **Response**:

     .. code-block:: json

        {
            "images": [
                "url1.jpg",
                "url2.jpg",
                "url3.jpg"
            ]
        }

These endpoints are designed to be flexible and robust, allowing for detailed control over the image generation process and seamless integration with the user interface.
