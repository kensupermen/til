## 1. Docker volume 
  Use `volume` to keep data from docker. Docker only install application, don't keep any data
  - Show list volume: `docker volume ls`
  - Remove all volume unuse: `docker volume prune`
  NOTE: Please naming for volume
## 2. Rebuild images
  `docker-compose build`
  NOTE: When you destroy container or rebuild images, plz don't destroy `volume`
## 3. How to build and run all container with docker-compose
  ```bash
    docker-compose build
    docker-compose run backend bundle install --jobs 4 --without development test
    docker-compose run backend rake assets:precompile
    docker-compose up -d
    docker-compose run backend rake db:setup
  ```
