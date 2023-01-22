# Install
brew install gofireflyio/aiac/aiac

# get api key 
sk-***********************

# export keys
export OPENAI_API_KEY=sk-***********************

# create gitignore file in root .gitignore
 aiac get gitignore to exclude AIAC/openia_key file

# create src
mkdir src

# get node application and save it in src/index.js
aiac get hello world node application

# get package.json and save it in src/package.json
aiac get package.json using index.js

# test it
node src/index.js

# dockerize
aiac get dockerfile for src/index.js

# test it
docker build -t chatgpt_devops_example:latest .
docker run -p 3000:3000 chatgpt_devops_example:latest 
docker tag chatgpt_devops_example:latest mitin20/chatgpt_devops_example:latest
docker push mitin20/chatgpt_devops_example:latest 

# k8s in k8s/chatgp_devops-example.yaml
mkdir k8s
aiac get k8s deployment and service manifest for mitin20/chatgpt_devops_example:latest image using container port 3000 and type ClusterIP

# test
kubectl apply -f k8s/
kubectl port-forward svc/chatgpt-devops-example-svc 8080:3000 
curl localhost:8080

# CICD in ../.github/workflows/ci.yaml
aiac get github actions to build chatgpt_devops_example AIAC/Dockerfile and push to dockerhub.io using DOCKER_USERNAME and DOCKER_PASSWORD

