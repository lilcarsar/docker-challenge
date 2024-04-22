# docker-challenge-template

https://medium.com/nerd-for-tech/deploy-a-custom-nginx-docker-image-and-push-it-to-docker-hub-118f1ab2186b
https://docs.docker.com/compose/compose-application-model/
https://www.geeksforgeeks.org/docker-compose/?ref=lbp
https://github.com/docker/welcome-to-docker
https://hub.docker.com/_/mariadb


# Challenge 1
What I did for challenge 1 is I created the public folder within the base challenge 1 folder, that public folder contains my 
index.html which is a basic HTML page with my name and my SAIT id. 
After building that I created a docker file from the links attached above, then I built a custom docker file that met my needs. 
The file is very similar to that of the first link, but when you first run the docker application it gives you quick guides on how to set up your first container and image. Part of the dockerfile was built from that. The GitHub link attached above also gave me a good basis for how to set up my dockerfile. After following that I used the command 'docker build -t challenge1 .' to send the dockerfile and all necessary information to docker desktop and my docker account. After doing that I selected images from the sidebar and chose challenge1 and selected run and in the optional arguments I added the port I wanted which was 8080, after doing that I went to localhost:8080 and it displayed my name and sait id

# Challenge 2
Challenge 2 was a bit more difficult as I had to dive further into the world of docker and understand what a docker compose file is. After reviewing some of the links listed above I discovered how to build the compose file which just primarily helps with defining ports and where to read the data from for the json data for the book collection. Before building the compose file I built the docker file, which again was much more similar to the one from the docker learning, as it helped to build one with node which still worked well as opposed to with NGinx since I genuinely forgot I was supposed to build it with NGinx since I was following the tutorial lol. It still ended up working in the end. After building both the Dockerfile and the docker-compose.yaml I ran the command 'docker build -t challenge2 .' which then sent the info to docker desktop and my account. After that I ran the server and went to localhost:8080/api/books and it displayed all the json data and after going to localhost:8080/api/books/1 it only displayed 1 book. Both are listed screenshots in my submission.

# Challenge 3
Challenge 3 started off as a semi difficult task for me as I didn't know where to start. After pasting the "docker" folder into the project I couldn't figure out how to build the docker compose file. I reviewed my previous docker compose files, and with the help of setting up my .env file and with the previous links I used I was able to build my .yml file. After building it I had issues specifically with this line "      - ./docker/nginx/nginx.conf:/etc/nginx/conf.d/default.conf". I was trying to get the nginx.conf file to work, but I couldn't figure out how to do it. I realized about 30 minutes later I had forgotten to add /docker/ in the build to properly reference the file. I made a similar mistake with the db "- ./docker/db/init/init.sql:/docker-entrypoint-initdb.d/init.sql". After solving that, it ran quite smoothly.

# Challenge 4
With challenge 4 being similar to challenge 3 I believed it would prove quite simple, as I had completed challenge 3 mere minutes before my inital attempt. I had to add edit the docker-compose file,
     ports:
      - "3003:3000"
      - "3004:3000"
      - "3005:3000"
    deploy:
      replicas: 3
adding these lines would hypothetically allow me to run more than one instance at a time. However when I ran it, no matter what I changed I kept running into an error that kept having whatever port I set it to be busy when I tried to run it. Somehow I was able to change it and allow for it to run multiple instances through sheer will power, after solving that bug, which I am led to believe arose from the nginx.conf file, I attempted to set up instances in there as opposed to just in the docker-compose. After making that change, it now allows running 3 instances at the same time.