# azure-triton-mme
## Step 1 - Provision Azure Machine Learning Workspace
## Step 2 - Git Clone from Azure Example

git clone https://github.com/Azure/azureml-examples --depth 1

cd azureml-examples/cli/endpoints/online/triton/single-model

## Step 3 - Create Endpoint
az ml online-endpoint create -n triton-reactor-demo -f create-managed-endpoint.yaml

## Step 4 - Perform Deployment - Change the Instance type in create-managed-deployment.yaml if needed. Ensure your subscription have quota to create VM, If not Please raise a request to Increase

az ml online-deployment create --name blue --endpoint triton-reactor-demo -f create-managed-deployment.yaml --all-traffic

## Step 5 - Set the Environment Variable - Get the Endpoint URL and Auth Token from Console
scoring_uri=”your inference URL”
auth_token=“add your auth from endpoint”
MAGE_PATH=/home/azureuser/cloudfiles/code/Users/<yourworkspace>/azureml-examples/cli/endpoints/online/triton/single-model/data

## Step 6 -  Download Test data locally
Download Data from  https://github.com/jayyanar/azure-triton-mme/blob/main/data.zip

## Step 7 -  Test 
python triton_densenet_scoring.py --base_url=$scoring_uri --token=$auth_token

python triton_densenet_scoring.py --base_url=$scoring_uri --token=$auth_token --image_path $IMAGE_PATH/peacock.jpg
python triton_densenet_scoring.py --base_url=$scoring_uri --token=$auth_token --image_path $IMAGE_PATH/dog_animal_boxer.jpg
python triton_densenet_scoring.py --base_url=$scoring_uri --token=$auth_token --image_path $IMAGE_PATH/horse_gallop_animal.jpg
python triton_densenet_scoring.py --base_url=$scoring_uri --token=$auth_token --image_path $IMAGE_PATH/scarlet_macaw_197565.jpg
python triton_densenet_scoring.py --base_url=$scoring_uri --token=$auth_token --image_path $IMAGE_PATH/fish_water_animal.jpg

