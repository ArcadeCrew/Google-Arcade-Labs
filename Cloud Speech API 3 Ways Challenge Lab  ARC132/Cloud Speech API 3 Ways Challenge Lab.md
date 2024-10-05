# Cloud Speech API 3 Ways: Challenge Lab || [ARC132](https://www.cloudskillsboost.google/focuses/67215?parent=catalog) ||

## Solution [here](https://youtu.be/iLn4-TvJXno)

### Run below Commands in CloudShell

```
export ZONE=$(gcloud compute instances list lab-vm --format 'csv[no-heading](zone)')
gcloud compute ssh lab-vm --project=$DEVSHELL_PROJECT_ID --zone=$ZONE --quiet
```

* Go to `Credentials` from [here](https://console.cloud.google.com/apis/credentials)

```
export API_KEY=
export task_2_file_name=""
export task_3_request_file=""
export task_3_response_file=""
export task_4_sentence=""
export task_4_file=""
export task_5_sentence=""
export task_5_file=""
```
```
curl -LO raw.githubusercontent.com/ArcadeCrew/Google-Arcade-Labs/blob/main/Cloud%20Speech%20API%203%20Ways%20Challenge%20Lab%20%20ARC132/ARC132.sh
sudo chmod +x ARC132.sh

./ARC132.sh
```

### Congratulations 🎉 You completed the Lab !

# Subscribe our channel [Arcade Crew](https://www.youtube.com/@Arcade61432)

### Don't Forget to Join the [Whatsapp Group](https://chat.whatsapp.com/FbVg9NI6Dp4CzfdsYmy0AE)
