Mirage
======

Mirage is a tool within WeAudit designed to facilitate the real-time analysis and comparison of images generated through AI models to detect biases and anomalies.

Features and Capabilities
-------------------------

- **Image Comparison**: Provides functionalities to compare multiple images side by side to identify differences and anomalies.
- **Bias Detection**: Utilizes custom algorithms to detect and report potential biases in image generation.

Setting Up Mirage
-----------------

To incorporate Mirage effectively in WeAudit:

1. **Installation**: Deploy Mirage as a microservice within the AWS infrastructure, ensuring scalability and accessibility.
2. **Integration**: Link Mirage with the WeAudit's main system to fetch and send image data seamlessly.

Usage Example
-------------

Mirage is typically used in scenarios where rapid analysis of generated images is crucial. For example, auditors may use Mirage to quickly compare images generated from different demographic prompts to assess bias.

.. code-block:: javascript

    // Example Mirage function call
    async function imageGeneration(prompt, modelName, modelVersion, n) {

        // Construct the body in the format expected by your Lambda function
        const requestBody = JSON.stringify({
            model_name: modelName,
            model_version_id: modelVersion,
            prompt: prompt,
            num: n
        });

        const response = await axios.post("https://vtsuohpeo0.execute-api.us-east-1.amazonaws.com/Prod/mirage", {
            body: requestBody
        }, {
            headers: {
                'Content-Type': 'application/json'
            }
        });

        // Retuns an array of generated images from Replicate
        return JSON.parse(response.data.body);

    }

