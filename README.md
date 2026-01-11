# Lab3 : Versionnement des données et pipelines ML avec DVC
## Étape 1 : Initialisation de DVC dans le projet

Cette étape consiste à initialiser l’outil DVC dans le répertoire du projet afin de permettre le versionnement des données et des artefacts. La commande `dvc init` a été exécutée, ce qui a créé la structure de configuration nécessaire, notamment le dossier `.dvc/` et le fichier `.dvc/config`. 

<img width="1918" height="1079" alt="image" src="https://github.com/user-attachments/assets/528fee55-33db-42b6-a774-550f0c301aef" />

<img width="1919" height="936" alt="image" src="https://github.com/user-attachments/assets/444573e1-6cc8-466d-863a-8a072c826625" />

## Étape 2 : Versionner les données brutes avec DVC

Lors de cette étape, le fichier de données brutes `data/raw.csv` a été ajouté au suivi de DVC à l’aide de la commande `dvc add`. Cette action a généré un fichier de métadonnées `raw.csv.dvc` ainsi qu’une mise à jour du fichier `.gitignore` afin d’exclure le fichier de données du suivi Git. Seuls les fichiers de configuration DVC ont ensuite été versionnés avec Git, permettant de conserver un dépôt léger tout en assurant le suivi et la reproductibilité des données via DVC.

<img width="1914" height="249" alt="image" src="https://github.com/user-attachments/assets/565c5426-2f36-42f1-927e-4259610abee0" />


## Étape 3 : Configuration d’un remote DVC

Lors de cette étape, un espace de stockage distant pour DVC a été configuré afin de centraliser les données suivies. Un dossier local `dvc_storage` a été créé et déclaré comme remote par défaut à l’aide de la commande `dvc remote add -d`. Cette configuration a ensuite été enregistrée dans le fichier `.dvc/config`, qui a été ajouté et versionné avec Git. Cette étape permet d’assurer la persistance et le partage des données suivies par DVC indépendamment du dépôt Git.

<img width="1558" height="104" alt="image" src="https://github.com/user-attachments/assets/7d792283-1941-428e-8675-10a42ca5c7c2" />

<img width="1919" height="231" alt="image" src="https://github.com/user-attachments/assets/ea5d898a-7479-4df6-a9a8-26aed5ba36ac" />


## Étape 4 : Push des données dans le remote DVC

Lors de cette étape, un espace de stockage distant pour DVC a été configuré afin de centraliser les données suivies. Un dossier local `dvc_storage` a été créé et déclaré comme remote par défaut à l’aide de la commande `dvc remote add -d`. Cette configuration a ensuite été enregistrée dans le fichier `.dvc/config`, qui a été ajouté et versionné avec Git. Cette étape permet d’assurer la persistance et le partage des données suivies par DVC indépendamment du dépôt Git.

<img width="1559" height="97" alt="image" src="https://github.com/user-attachments/assets/6bb01f67-4d65-48ff-a810-42e1acdb3109" />

## Étape 5 : Simulation d’une collaboration : supprimer localement et récupérer depuis DVC

Lors de cette étape, le fichier de données *data/raw.csv* a été supprimé localement afin de simuler une perte ou une absence du dataset. Après vérification de sa suppression, la commande *dvc pull* a été exécutée pour récupérer automatiquement les données depuis le remote DVC. Le fichier a ainsi été restauré à l’identique, démontrant la capacité de DVC à récupérer les données suivies et à faciliter le travail collaboratif.

<img width="1363" height="27" alt="image" src="https://github.com/user-attachments/assets/2b878b48-faf5-40b1-9f5b-6c9740865ac7" />

<img width="1361" height="457" alt="image" src="https://github.com/user-attachments/assets/6d3310fd-a6de-4456-b522-d40ff13e7215" />

## Étape 6 : Versionner les données transformées

Lors de cette étape, le fichier de données transformées `registry/train_stats.json` a été ajouté au suivi de DVC à l’aide de la commande `dvc add`. Cette opération a généré un fichier de métadonnées `train_stats.json.dvc` ainsi qu’une mise à jour du fichier `.gitignore` afin d’exclure le fichier de données du suivi Git. Les fichiers de configuration DVC ont ensuite été versionnés avec Git, puis les données ont été envoyées vers le remote DVC via la commande `dvc push`, assurant ainsi un suivi cohérent et reproductible des données préparées du pipeline ML.

<img width="1364" height="251" alt="image" src="https://github.com/user-attachments/assets/2a8ee62d-0a5a-4c05-a316-a89996eedc4c" />

## Étape 7 : Création d’un pipeline reproductible dvc.yaml

Lors de cette étape, un pipeline de machine learning reproductible a été défini à l’aide de DVC en créant plusieurs stages dans le fichier `dvc.yaml`. Les étapes de préparation des données, d’entraînement du modèle et d’évaluation ont été ajoutées avec `dvc stage add`, en spécifiant pour chacune les scripts exécutés, les dépendances et les sorties générées. Cette configuration permet à DVC de suivre automatiquement les relations entre les différentes étapes du pipeline et d’assurer leur reproductibilité. Le fichier `dvc.yaml` a ensuite été versionné avec Git afin de conserver la définition complète du pipeline.

<img width="1357" height="240" alt="image" src="https://github.com/user-attachments/assets/efa5e815-f537-4345-8ef5-0cc234d76b3c" />

<img width="1362" height="233" alt="image" src="https://github.com/user-attachments/assets/32b9abb6-3fa9-4cdf-b609-63fceebf6765" />

<img width="1364" height="279" alt="image" src="https://github.com/user-attachments/assets/6b589af8-840f-44be-8a1c-94570fa1c99e" />

<img width="1919" height="503" alt="image" src="https://github.com/user-attachments/assets/a43aa58f-8689-40bc-93a2-e67d5ec75279" />

## Étape 8 : Reproduire automatiquement tout le pipeline

Lors de cette étape, une modification a été apportée au script de préparation des données afin de tester la reproductibilité du pipeline. La commande `dvc repro` a ensuite été exécutée, ce qui a déclenché automatiquement la réexécution des étapes impactées (préparation, entraînement et évaluation). Les fichiers générés ainsi que le fichier `dvc.lock` ont été mis à jour, confirmant que le pipeline est correctement orchestré et reproductible grâce à DVC.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/b9199bec-9f7b-47c4-8f9c-bb474008a957" />

<img width="1919" height="713" alt="image" src="https://github.com/user-attachments/assets/7b8904cf-9fb4-4a30-ad4c-04dd3eff2694" />

<img width="1919" height="188" alt="image" src="https://github.com/user-attachments/assets/083f3962-cbfc-4f90-b8da-ab40b829175a" />



