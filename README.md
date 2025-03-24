# 🚀 Customer Churn Prediction App Deployment on Google Cloud

This guide provides step-by-step instructions to build, deploy, and manage your Customer Churn Prediction application using **Google Cloud Run** and **Google Container Registry (GCR)**.

---

## 📚 Prerequisites

Before proceeding, ensure the following are set up:

- Google Cloud account with billing enabled.
- Google Cloud SDK installed and configured.
- Docker installed on your machine.
- Project configured with `gcloud` CLI:
```bash
gcloud config set project [PROJECT_ID]

## 🔥 Step 1: Build and Submit Docker Image

To build and submit the Docker image to **Google Container Registry (GCR)**, run the following command:

```bash
gcloud builds submit --no-cache --tag gcr.io/[PROJECT_ID]/[APP_NAME]

## 🗑️ Step 2: Delete Existing Container Image (Optional)

If you need to delete the existing Docker image from **Google Container Registry (GCR)** before redeploying, run the following command:

```bash
gcloud container images delete gcr.io/[PROJECT_ID]/[APP_NAME]

## 📦 Step 3: Build and Tag Docker Image Again (Optional)

If you want to rebuild and tag the Docker image, run the following command:

```bash
gcloud builds submit --tag gcr.io/[PROJECT_ID]/[APP_NAME]

## 🚀 Step 4: Deploy Application to Google Cloud Run

To deploy the application using **Google Cloud Run**, run the following command:

```bash
gcloud run deploy [APP_NAME] \
    --image gcr.io/[PROJECT_ID]/[APP_NAME] \
    --platform managed \
    --region [REGION] \
    --allow-unauthenticated

## ✅ Step 5: Verify Deployment

After successful deployment, a URL will be generated. You can access your application using this URL.

To list all running services:

```bash
gcloud run services list

To get the URL of your deployed service:

```bash
gcloud run services describe [APP_NAME] --format 'value(status.url)'
