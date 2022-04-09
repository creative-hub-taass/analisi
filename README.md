# Analisi e planning

* [![Project plan](https://img.shields.io/badge/GitHub-Project%20Plan%20Analisi-informational)](https://github.com/orgs/creative-hub-taass/projects/3)
* [![Milestones](https://img.shields.io/badge/GitHub-Milestones%20Analisi-informational)](https://github.com/creative-hub-taass/analisi/milestones?direction=asc&sort=due_date)
* [![Project plan](https://img.shields.io/badge/GitHub-Project%20Plan%20Back--end-informational)](https://github.com/orgs/creative-hub-taass/projects/4)
* [![Project plan](https://img.shields.io/badge/GitHub-Project%20Plan%20Front--end-informational)](https://github.com/orgs/creative-hub-taass/projects/5)
* [![Project plan](https://img.shields.io/badge/GitHub-Project%20Plan%20Android-informational)](https://github.com/orgs/creative-hub-taass/projects/6)

## Run instructions

### Kubernetes (local)

Open a terminal in the folder which contains all the creativeHub projects repositories, then execute these commands

#### Linux / Mac (bash)

```shell
minikube start
export GATEWAY_URL=http://localhost:8080
for f in ./**/orchestration/*.yaml; do cat $f | envsubst | kubectl apply -f -; done
minikube tunnel
```

#### Windows (Powershell)

```powershell
minikube start
$env:GATEWAY_URL = "http://localhost:8080"
Resolve-Path .\**\orchestration\*.yaml | Select -ExpandProperty Path | %{Get-Content $_ | envsubst | kubectl apply -f -}
minikube tunnel
```

### Kubernetes (Okteto)

Open a terminal in the folder which contains all the creativeHub projects repositories, then execute these commands

#### Linux / Mac (bash)

```shell
okteto kubeconfig
export GATEWAY_URL=https://api-gateway-acontenti.cloud.okteto.net
for f in ./**/orchestration/*.yaml; do cat $f | envsubst | kubectl apply -f -; done
```

#### Windows (Powershell)

```powershell
okteto kubeconfig
$env:GATEWAY_URL = "https://api-gateway-acontenti.cloud.okteto.net"
Resolve-Path .\**\orchestration\*.yaml | Select -ExpandProperty Path | %{Get-Content $_ | envsubst | kubectl apply -f -}
```
