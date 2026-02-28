## 
create docker file
build the image
 [docker build -t esraaghazal/nodeapp .]
check by run a container with the image
  docker run -d -p 3000:3000 esraaghazal/nodeapp:latest
  in your browser machien ip :3000
  <img width="662" height="133" alt="image" src="https://github.com/user-attachments/assets/7c6b0f1c-b501-4de0-94b8-618657f34b00" />


push the image to docker hub 
  docker push esraaghazal/nodeap:latest
Create deployment and service files to host the app and make it accessable from the internet
  kubectl get node
  kubectl apply -f deployment.yaml
  kubectl get pod
  kubctl apply -f servicess.yaml
  kubectl get svc

using service url to access the website <http//:node ip: node port>
  <img width="712" height="161" alt="image" src="https://github.com/user-attachments/assets/0596faa1-813a-4bea-b08a-94affb4ef80b" />


