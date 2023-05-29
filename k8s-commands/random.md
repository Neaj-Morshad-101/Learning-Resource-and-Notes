### To run command inside a pod mypod 
`kubectl exec -it mypod-7f4666fb84-2h7sl -- sh`

### To port forward pods port 8080 to local-host 8080
`kubectl port-forward pod/mypod-7f4666fb84-2h7sl 8080:8080`