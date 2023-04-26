# azure-triton-mme

git clone https://github.com/Azure/azureml-examples --depth 1
cd azureml-examples
cd cli

cd endpoints/online/triton/single-model

az ml online-endpoint create -n triton-reactor-demo -f create-managed-endpoint.yaml

az ml online-deployment create --name blue --endpoint triton-reactor-demo -f my-create-managed-deployment.yaml --all-traffic


python triton_densenet_scoring.py --base_url=$scoring_uri --token=$auth_token


Download Data from  https://github.com/jayyanar/azure-triton-mme/blob/main/data.zip

python triton_densenet_scoring.py --base_url=$scoring_uri --token=$auth_token --image_path $IMAGE_PATH/peacock.jpg
python triton_densenet_scoring.py --base_url=$scoring_uri --token=$auth_token --image_path $IMAGE_PATH/dog_animal_boxer.jpg
python triton_densenet_scoring.py --base_url=$scoring_uri --token=$auth_token --image_path $IMAGE_PATH/horse_gallop_animal.jpg
python triton_densenet_scoring.py --base_url=$scoring_uri --token=$auth_token --image_path $IMAGE_PATH/scarlet_macaw_197565.jpg
python triton_densenet_scoring.py --base_url=$scoring_uri --token=$auth_token --image_path $IMAGE_PATH/fish_water_animal.jpg


============
ENV

IMAGE_PATH=/home/azureuser/cloudfiles/code/Users/<yourworkspace>/azureml-examples/cli/endpoints/online/triton/single-model/data


scoring_uri=”your inference URL”
auth_token=“add your auth from endpoint”
