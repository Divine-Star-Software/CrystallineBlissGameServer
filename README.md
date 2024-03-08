<h1 align="center">
 Crystalline Bliss Game Server
</h1>

<p align="center">
<img src="https://divine-star-software.github.io/DigitalAssets/images/logo-small.png">
</p>

---

Offical server for Crystalline Bliss. Use this to houst your own Crystalline Bliss servers.

## Server Config

You can configure the server with a `server.json` file at the root of this directory.

```ts
type GameServerData = {
  url: string;
  port: number;
  name: string;
  description: string;
  country: string;
  language: string;
  gameVersion: string;
  //default is ./cert/cert.key used for devopment or local use
  certKeyPath?: string;
  //default is ./cert/cert.crt used for devopment or local use
  certCrtPath?: string;
  logErrors?: boolean;
  //default is ./errors/
  logErrorsPath?: string;
  logGames?: boolean;
  //default is ./logs/
  logGamePath?: string;
};
```

## local

```bash
git clone https://github.com/Divine-Star-Software/CrystallineBlissGameServer.git
#create and update server.json
cp emplate-server.json server.json
vim server.json
npm install
npm run create-cert
npm run start
```

## nginx setup 

This is how to set the server up on a ubuntu server using Nginx, pm2, and certbot. 

```bash
git clone https://github.com/Divine-Star-Software/CrystallineBlissGameServer.git
#create and update server.json
cp emplate-server.json server.json
vim server.json
#allow the port for the server
sudo ufw allow 9000
#update the sites for the nginx setup
cd /etc/nginx/sites-available/
vim default

#add this to the config and use your own url
server {
    listen 80;
    server_name server.crystallinebliss.dev;

    location / {
        proxy_pass http://localhost:9000; # Forward requests to Node.js application
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}


sudo nginx -t
sudo systemctl reload nginx
#certify the domain the server will run on 
certbot --nginx -d server.crystallinebliss.dev
cd /to/where/server/is
# run the app in the background with pm2 
pm2 start ./code/server.js --name="game-server"
# restart
pm2 restart game-server
# stop
pm2 stop game-server
```


### Crystalline Bliss Links

- [Visit Site](https://crystallinebliss.dev/)
- [Steam Page](https://store.steampowered.com/app/2547740/Crystalline_Bliss/)
- [Join Discord](https://discord.gg/XaWSsKQauC)
- [Watch On YouTube](https://www.youtube.com/channel/UC-02oe0-jCSy5KMqVSuXWbg)
