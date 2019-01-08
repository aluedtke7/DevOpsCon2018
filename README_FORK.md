# Fork von aluedtke7
Ansible Projekt um einen Kubernetes Cluster lokal auf einer Ubuntu 18.04 Maschine zu installieren

Das Projekt ist in 3 Playbooks aufgeteilt. Das erste (prepareHost.yml) dient zur Vorbereitung der Linux Maschine, um die nötigen Tools bzw. die nötige Software zu installieren. Dieses Playbook muß normalerweise nur einmal ausgeführt werden.

Das zweite Playbook (createCluster.yml) dient dem Aufsetzen und starten des K8S Clusters.

Das dritte Playbook (destroyCluster.yml) dient dem Zerstören des K8S Clusters.

## Voraussetzungen
Ansible muss installiert sein (`sudo apt install ansible`). Die Playbooks müssen als normaler User ausgeführt werden (kein sudo).


## Playbooks
### Host vorbereiten (einmalig als erstes ausführen):
````
ansible-playbook prepareHost.yml
````

### K8S Cluster erstellen:
````
ansible-playbook createCluster.yml
````
Am Ende des Skriptes wird der Token für den admin_user angezeigt, damit man sich am K8S Dashboard anmelden kann. 
Hierzu einmalig `kubectl proxy` in einer Shell starten und dann im Webbrowser die Adresse
http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/ aufrufen.

### K8S Cluster zerstören:
````
ansible-playbook destroyCluster.yml
````
