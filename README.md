🚀 Customer Churn Prediction App Deployment on Google Cloud This guide
provides step-by-step instructions to build, deploy, and manage your
Customer Churn Prediction application using Google Cloud Run and Google
Container Registry (GCR).

📚 Prerequisites Before proceeding, ensure the following are set up:

Google Cloud account with billing enabled.

Google Cloud SDK installed and configured.

Docker installed on your machine.

Project configured with gcloud CLI:

bash Copy Edit gcloud config set project \[PROJECT_ID\] 🔥 Step 1: Build
and Submit Docker Image To build and submit the Docker image to Google
Container Registry (GCR), run the following command:

bash Copy Edit gcloud builds submit \--no-cache \--tag
gcr.io/\[PROJECT_ID\]/\[APP_NAME\] 🗑️ Step 2: Delete Existing Container
Image (Optional) If you need to delete the existing Docker image from
GCR before redeploying:

bash Copy Edit gcloud container images delete
gcr.io/\[PROJECT_ID\]/\[APP_NAME\] 📦 Step 3: Build and Tag Docker Image
Again (Optional) If you want to rebuild and tag the Docker image:

bash Copy Edit gcloud builds submit \--tag
gcr.io/\[PROJECT_ID\]/\[APP_NAME\] 🚀 Step 4: Deploy Application to
Google Cloud Run To deploy the application using Google Cloud Run:

bash Copy Edit gcloud run deploy \[APP_NAME\] \\ \--image
gcr.io/\[PROJECT_ID\]/\[APP_NAME\] \\ \--platform managed \\ \--region
\[REGION\] \\ \--allow-unauthenticated Deployment Parameters:
\[APP_NAME\] -- Name of your application.

\[PROJECT_ID\] -- Your Google Cloud project ID.

\[REGION\] -- Desired region (e.g., asia-south1).

✅ Step 5: Verify Deployment After successful deployment, a URL will be
generated. You can access your application using this URL.

To list all running services:

bash Copy Edit gcloud run services list To get the URL of your deployed
service:

bash Copy Edit gcloud run services describe \[APP_NAME\] \--format
\'value(status.url)\' 🛑 Optional: Stop or Delete Service To stop or
delete a service:

bash Copy Edit gcloud run services delete \[APP_NAME\] 🎯 Notes Make
sure to replace placeholders like \[PROJECT_ID\], \[APP_NAME\], and
\[REGION\] with actual values.

The \--allow-unauthenticated flag allows public access. Remove it for
restricted access.

Happy Deploying! 🎉
