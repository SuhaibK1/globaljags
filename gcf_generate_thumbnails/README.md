# GlobalJags generate_thumbnails Google Cloud Function
This is a Google Cloud Function that will process images that were uploaded through the GlobalJags website. It will be developed in three parts.

1. Create a Node.js cloud function triggered by an upload to a Google Cloud Storage bucket
2. Examine the uploaded file to ensure it is a photo file that contains EXIF GPS data
3. Create a thumbnail image of the uploaded file and store it in Google Cloud Storage

## Deploy the Cloud Function
Deploy the Cloud Function with the following command. Ensure you replace the `trigger-resource` with YOUR uploads bucket.

```
gcloud functions deploy generate_thumbnails \
--runtime nodejs18 \
--trigger-event google.storage.object.finalize \
--entry-point generateThumbnail \
--trigger-resource sp24-41200-skankodi-gj-uploads
```

## Trigger the Cloud Function
Trigger the Cloud Function by uploading a sample image to your bucket. **Ensure you replace YOUR BUCKET NAME in the command below.**

```
gsutil cp gs://sp23-globaljags-dev-sample-images/china/china1.jpeg gs://sp24-41200-skankodi-gj-uploads
```