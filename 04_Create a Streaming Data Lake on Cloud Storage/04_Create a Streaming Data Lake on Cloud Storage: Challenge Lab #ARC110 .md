# ARC110
>🚨 [PLEASE SUBSCRIBE OUR CHANNEL CLOUDHUSTLER](https://www.youtube.com/@cloudhustlers) **&** [JOIN OUR COMMUNITY](https://chat.whatsapp.com/KBfUcSleGGEFf2Xvvm8FW3)
## Run in Cloushell
```cmd
TOPIC_ID=
```
### Put your message inside the quotation mark
```cmd
MESSAGE=""
````
```cmd
REGION=
```
```cmd
PROJECT_ID=$(gcloud config get-value project)
BUCKET_NAME="${PROJECT_ID}-bucket"
gcloud config set compute/region $REGION
gcloud services disable dataflow.googleapis.com
gcloud services enable dataflow.googleapis.com
gsutil mb gs://$BUCKET_NAME
gcloud pubsub topics create $TOPIC_ID
gcloud app create --region=$REGION
echo "y" | gcloud scheduler jobs create pubsub publisher-job \
    --schedule="* * * * *" \
    --topic=$TOPIC_ID \
    --message-body="$MESSAGE"
gcloud scheduler jobs run publisher-job
git clone https://github.com/GoogleCloudPlatform/java-docs-samples.git
cd java-docs-samples/pubsub/streaming-analytics
mvn compile exec:java \
-Dexec.mainClass=com.examples.pubsub.streaming.PubSubToGcs \
-Dexec.cleanupDaemonThreads=false \
-Dexec.args=" \
    --project=$PROJECT_ID \
    --region=us-central1 \
    --inputTopic=projects/$PROJECT_ID/topics/$TOPIC_ID \
    --output=gs://$BUCKET_NAME/samples/output \
    --runner=DataflowRunner \
    --windowSize=2"
```
