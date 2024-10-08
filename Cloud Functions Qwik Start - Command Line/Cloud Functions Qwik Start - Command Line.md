# Cloud Functions: Qwik Start - Command Line | [GSP080](https://www.cloudskillsboost.google/focuses/916?parent=catalog) |

## [Youtube Solution](https://youtu.be/xcl-Ai6bG8Q)

### Run the following Commands in CloudShell

```
export REGION=
```
```
#!/bin/bash
# Define color variables

BG_RED=`tput setab 1`
BG_GREEN=`tput setab 2`

BOLD=`tput bold`
RESET=`tput sgr0`
#----------------------------------------------------start--------------------------------------------------#

echo "${BG_RED}${BOLD}Starting Execution${RESET}"

gcloud config set compute/region $REGION

mkdir gcf_hello_world && cd $_

cat > index.js <<'EOF_END'
const functions = require('@google-cloud/functions-framework');

// Register a CloudEvent callback with the Functions Framework that will
// be executed when the Pub/Sub trigger topic receives a message.
functions.cloudEvent('helloPubSub', cloudEvent => {
  // The Pub/Sub message is passed as the CloudEvent's data payload.
  const base64name = cloudEvent.data.message.data;

  const name = base64name
    ? Buffer.from(base64name, 'base64').toString()
    : 'World';

  console.log(`Hello, ${name}!`);
});
EOF_END

cat > package.json <<'EOF_END'
{
  "name": "gcf_hello_world",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "start": "node index.js",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "dependencies": {
    "@google-cloud/functions-framework": "^3.0.0"
  }
}
EOF_END

npm install

gcloud services disable cloudfunctions.googleapis.com

gcloud services enable cloudfunctions.googleapis.com

sleep 15

gcloud functions deploy nodejs-pubsub-function \
  --gen2 \
  --runtime=nodejs20 \
  --region=$REGION \
  --source=. \
  --entry-point=helloPubSub \
  --trigger-topic cf-demo \
  --stage-bucket $DEVSHELL_PROJECT_ID-bucket \
  --service-account cloudfunctionsa@$DEVSHELL_PROJECT_ID.iam.gserviceaccount.com \
  --allow-unauthenticated \
  --quiet

gcloud functions describe nodejs-pubsub-function \
  --region=$REGION

echo -e "${BG_GREEN}${BOLD}Congratulations For Completing The Lab !!!${RESET}"
echo -e "${BG_GREEN}${BOLD}Subscribe to our Channel: \e]8;;https://www.youtube.com/@Arcade61432\e\\https://www.youtube.com/@Arcade61432\e]8;;\e\\${RESET}"


#-----------------------------------------------------end----------------------------------------------------------#
```

### Congratulations!!! You completed the Lab! 🎉

# Subscribe our channel [Arcade Crew](https://www.youtube.com/@Arcade61432)

### Don't Forget to Join the [Whatsapp Group](https://chat.whatsapp.com/FbVg9NI6Dp4CzfdsYmy0AE)
