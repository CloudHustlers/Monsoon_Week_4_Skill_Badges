# GSP752
>🚨 [PLEASE SUBSCRIBE OUR CHANNEL CLOUDHUSTLER](https://www.youtube.com/@cloudhustlers) **&** [JOIN OUR COMMUNITY](https://chat.whatsapp.com/KBfUcSleGGEFf2Xvvm8FW3)
## Run in cloudshell 
```cmd
export PROJECT_ID=$(gcloud config get-value project)
echo 'provider "google" {
  project     = "'"$PROJECT_ID"'"
  region      = "us-central-1"
}
resource "google_storage_bucket" "test-bucket-for-state" {
  name        = "'"$PROJECT_ID"'"
  location    = "US"
  uniform_bucket_level_access = true
}
terraform {
  backend "local" {
    path = "terraform/state/terraform.tfstate"
  }
}' > main.tf
terraform init
terraform apply -auto-approve
echo 'provider "google" {
  project     = "'"$PROJECT_ID"'"
  region      = "us-central-1"
}
resource "google_storage_bucket" "test-bucket-for-state" {
  name        = "'"$PROJECT_ID"'"
  location    = "US"
  uniform_bucket_level_access = true
}
terraform {
  backend "gcs" {
    bucket  = "'"$PROJECT_ID"'"
    prefix  = "terraform/state"
  }
}' > main.tf
yes | terraform init -migrate-state
gsutil label ch -l 'key:value' gs://$PROJECT_ID
terraform refresh
```
