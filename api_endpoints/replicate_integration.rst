Replicate Integration
=====================

WeAudit utilizes the Replicate API to access a variety of pre-trained models for image generation. This integration is critical for enabling dynamic and scalable image creation based on user prompts.

Endpoint Overview
-----------------

**/replicate/predict**
   - **Method**: POST
   - **Description**: Sends a request to Replicate to generate images based on a specific model and input parameters.
   - **Request Body**:

     .. code-block:: json

        {
            "model": "stability-ai/stable-diffusion",
            "input": {
                "prompt": "A serene lake at sunset"
            }
        }

   - **Response**:

     .. code-block:: json

        {
            "id": "prediction_id",
            "status": "processing"
        }

Integration Details
-------------------

- **Authentication**: API requests must include an authentication token provided by Replicate during the setup process.
- **API Calls**: Utilize HTTPS for secure communication. Handle rate limits and possible errors gracefully to ensure robustness.
- **Data Handling**: Ensure that the responses from Replicate are parsed correctly and that any image URLs or data are securely stored and handled within WeAudit.

Example Usage
-------------

An example function to call the Replicate API might look like this:

.. code-block:: python

    import requests

    def call_replicate_api(prompt):
        url = "https://api.replicate.com/v1/predictions"
        headers = {'Authorization': 'Bearer <Your-Replicate-Token>'}
        payload = {
            "model": "stability-ai/stable-diffusion",
            "input": {"prompt": prompt}
        }

        response = requests.post(url, headers=headers, json=payload)
        return response.json()

This function demonstrates how to interact with the Replicate API, including handling the necessary headers and JSON body for image generation.
