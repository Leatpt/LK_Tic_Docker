Kuidas rakendus Dockeris tööle panna?
1. Installin dockeri ja teen restardi
2. Login Docker Desktop-pi sisse
3. Installin "npm install -g create-react-app"
et seadistada React-i põhirakendus. 
4. cd react-docker-example/
5. Teen kausta faili Dockerfile ja lisan sinna järgmised read:
"FROM node:18-alpine
WORKDIR /react-docker-example/

COPY public/ /react-docker-example/public
COPY src/ /react-docker-example/src
COPY package.json /react-docker-example/

RUN npm install .
CMD ["npm", "start"] ."
6. docker image build -t react-example-image:latest .
Loon Docker image-i
7. Jooksutan konteineri käsklusega: docker run -p 3000:3000 react-example-image:latest
8. Nüüd ma saan rakendusele ligipääsu minnes http://localhost:3000


Probleemid:
1. npm run start tagastas errori. 
sass-loader'is oli probleem. 
Leidsin failide hulgast sass-loader'i ja lugesin README.md
Selle järgi jooksutasin git bash-is käskluse
" npm install sass-loader sass webpack --save-dev " 
Peale seda läks npm run start läbi.
2. Ma ei saa docker login käsklusega Docker Hub-i sisse logida:
error during connect: this error may indicate that the docker daemon is not running: Post "http://%2F%2F.%2Fpipe%2Fdocker_engine/v1.24/auth": open //./pipe/docker_engine: Access is denied.
3. docker push leatpt/tic-game-learning:tagname
annab sama errori, mis sisselogimise katsed.
4. "You're almost done!
We're redirecting you to the desktop app. If you don't see a dialog, please click the button below."
Ma ei saa Docker Desktopi sisse logida, annab sellise sõnumi ja midagi ei liigu edasi, isegi peale pikka ootamist.
5. Pidin uninstallima ja reinstallima Docker Desktopi, nüüd loob ühenduse
6. "npm install -g create-react-app" ei töötanud, googeldasin
ja kasutasin käsklust npx create-react-app react-docker-example.
See tegi lõpuks kausta nimega react-docker-example