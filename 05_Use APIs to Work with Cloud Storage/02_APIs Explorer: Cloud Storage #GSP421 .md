# GSP421
>🚨 [PLEASE SUBSCRIBE OUR CHANNEL CLOUDHUSTLER](https://www.youtube.com/@cloudhustlers) **&** [JOIN OUR COMMUNITY](https://chat.whatsapp.com/KBfUcSleGGEFf2Xvvm8FW3)
## Run in Cloudshell
```cmd
gcloud services enable storage-api.googleapis.com
gsutil mb gs://$DEVSHELL_PROJECT_ID-qwiklabs-bucket01
gsutil mb gs://$DEVSHELL_PROJECT_ID-qwiklabs-bucket02
curl https://upload.wikimedia.org/wikipedia/commons/thumb/a/a4/Ada_Lovelace_portrait.jpg/800px-Ada_Lovelace_portrait.jpg --output demo-image1.png
gsutil cp demo-image1.png gs://$DEVSHELL_PROJECT_ID-qwiklabs-bucket01
curl https://upload.wikimedia.org/wikipedia/commons/thumb/a/a4/Ada_Lovelace_portrait.jpg/800px-Ada_Lovelace_portrait.jpg --output demo-image2.png
gsutil cp demo-image2.png gs://$DEVSHELL_PROJECT_ID-qwiklabs-bucket01
gsutil cp gs://$DEVSHELL_PROJECT_ID-qwiklabs-bucket01/demo-image1.png gs://$DEVSHELL_PROJECT_ID-qwiklabs-bucket01/demo-image1-copy.png
gsutil cp gs://$DEVSHELL_PROJECT_ID-qwiklabs-bucket01/* gs://$DEVSHELL_PROJECT_ID-qwiklabs-bucket02/
```
