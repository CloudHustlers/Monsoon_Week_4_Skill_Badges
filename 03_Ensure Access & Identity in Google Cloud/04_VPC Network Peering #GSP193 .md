# GSP193
>🚨 [PLEASE SUBSCRIBE OUR CHANNEL CLOUDHUSTLER](https://www.youtube.com/@cloudhustlers) **&** [JOIN OUR COMMUNITY](https://chat.whatsapp.com/KBfUcSleGGEFf2Xvvm8FW3)
### Run in cloudshell 1
```cmd
export PROJECT_ID2=
```
```
gcloud compute networks create network-a --subnet-mode custom
gcloud compute networks subnets create network-a-subnet --network network-a \
    --range 10.0.0.0/16 --region us-west1 
gcloud compute instances create vm-a --zone us-west1-a --network network-a --subnet network-a-subnet --machine-type e2-small 
gcloud compute firewall-rules create network-a-fw --network network-a --allow tcp:22,icmp
```
### Open another Cloudshell 2
```cmd
export PROJECT_ID1=
```
```cmd
export PROJECT_ID2=
```
```cmd
gcloud config set project $PROJECT_ID2
gcloud compute networks create network-b --subnet-mode custom
gcloud compute networks subnets create network-b-subnet --network network-b \
    --range 10.8.0.0/16 --region us-west1 
gcloud compute instances create vm-b --zone us-west1-a --network network-b --subnet network-b-subnet --machine-type e2-small
gcloud compute firewall-rules create network-b-fw --network network-b --allow tcp:22,icmp
gcloud compute networks peerings create peer-ba \
  --network=network-b \
  --peer-project=$PROJECT_ID1 \
  --peer-network=network-a
```
### Run in Cloudhsell 1
```cmd
gcloud compute networks peerings create peer-ab \
  --network=network-a \
  --peer-project=$PROJECT_ID2 \
  --peer-network=network-b
```
