Image Caching and Deletion
==========================

Effective management of image caching and deletion is essential to optimize storage and maintain compliance with data policies in WeAudit.

Caching Strategy
----------------

- **Temporary Storage**: Store images temporarily in AWS S3 with a defined expiry time.
- **Caching Mechanism**: Implement caching mechanisms to reuse frequently requested images, reducing the need to regenerate them.

Deletion Policy
---------------

- **Automated Deletion**: Set up automated rules in AWS S3 to delete images after their usefulness expires.
- **Manual Deletion**: Allow users to manually delete images when they are no longer needed.

Implementing Deletion Policies
------------------------------

Here's how to set up automated deletion in AWS S3:

.. code-block:: json

    {
        "Rules": [
            {
                "Prefix": "generated_images/",
                "Status": "Enabled",
                "Expiration": {
                    "Days": 30
                }
            }
        ]
    }

This JSON configuration automatically deletes images stored under the 'generated_images/' prefix after 30 days.
