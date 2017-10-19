## 1. Docker volume 
  Use `volume` to keep data from docker. Docker only install application, don't keep any data
  - Show list volume: `docker volume ls`
  - Remove all volume unuse: `docker volume prune`
  - NOTE: Please naming for volume
## 2. Rebuild images
  `docker-compose build`
  - NOTE: When you destroy container or rebuild images, plz don't destroy `volume`
## 3. How to build and run all container with docker-compose
  ```bash
    docker-compose build
    docker-compose run backend bundle install --jobs 4 --without development test
    docker-compose run backend rake assets:precompile
    docker-compose up -d
    docker-compose run backend rake db:setup
  ```
## 4. ADD vs COPY
  Both ADD and COPY adds local files when building a container but ADD does some additional magic like adding remote files and ungzipping and untaring archives.
  Only use ADD if you understand this difference.
## 5. ADD your code last
  ADD invalidates your cache if files have changed. Don't invalidate the cache by adding frequently changing stuff too high up in your Dockerfile. 
  Add your code last, libraries and dependencies first. For node.js apps that means adding your package.json first, running npm install and only then adding your code.

## 6. Docker for production
