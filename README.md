# data-engineering-zoomcamp--docker-workshop
docker workshop from datatalks

# helper 
 * docker run -it --rm \
  -e POSTGRES_USER="root" \
  -e POSTGRES_PASSWORD="root" \
  -e POSTGRES_DB="ny_taxi" \
  -v ny_taxi_postgres_data:/var/lib/postgresql \
  -p 5432:5432 \
  postgres:18
  

* docker run -it --rm --network=pipeline_default taxi_ingest:v0001 --pg-user=root --pg-pass=root --pg-host=pgdatabase --pg-port=5432 --pg-db=ny_taxi --target-table=yellow_taxi_trips

# pour debug avec docker-compose 

* docker ps #Containers actifs (ID, image, ports, statut)
* docker ps -a #Tous les containers, y compris ceux qui ont crashé
* docker logs <container> #Logs du container — premier réflexe quand un container s'arrête

* docker network ls #Lister tous les réseaux Docker
* docker network inspect <réseau> #Voir quels containers sont attachés — clé pour diagnostiquer les problèmes DNS
* docker network prune #Supprimer les réseaux inutilisés (orphelins d'anciens compose)

* docker volume ls #Lister tous les volumes
* docker volume inspect <volume> #Voir le mountpoint et les métadonnées
* docker volume prune #Supprimer les volumes non attachés à un container

* docker-compose up -d Démarrer en arrière-plan
* docker-compose down #Arrêter et supprimer les containers et réseaux
* docker-compose down -v #Idem + supprime les volumes — utile pour repartir propre
* docker-compose logs -f <service>  #Suivre les logs d'un service en temps réel
* docker-compose ps #État des services du compose (plus lisible que docker ps)

* docker exec -it <container> bash #Ouvrir un shell dans un container actif

