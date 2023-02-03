https://earthly.dev/blog/k8s-gitops-with-fluxcd/

kubectl create namespace 2048-game

git add .

git commit -m "Automating Flux deployment" 

git branch -M main

## Replace the URL below with the url of the Git Repository you created 

git remote add origin https://github.com/remotejob/2048.git

eval "$(ssh-agent -s)"

ssh-add ~/.ssh/id_github

git remote set-url origin https://<githubtoken>@github.com/remotejob/2048.git

git push -u origin main

kubectl apply -f flux.yaml

kubectl port-forward service/game-service 8086:80 -n 2048-game