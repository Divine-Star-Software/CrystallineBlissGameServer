<h1 align="center">
 Crystalline Bliss Game Server
</h1>

<p align="center">
<img src="https://divine-star-software.github.io/DigitalAssets/images/logo-small.png">
</p>

---

Offical server for Crystalline Bliss. Use this to houst your own Crystalline Bliss servers.

Server Config

```ts
export type GameServerData = {
  url: string;
  port: number;
  name: string;
  description: string;
  country: string;
  language: string;
  gameVersion: string;
  //default is ./cert/cert.key
  certKeyPath?: string;
  //default is ./cert/cert.crt
  certCrtPath?: string;
  logErrors?: boolean;
  //default is ./errors/
  logErrorsPath?: string;
  logGames?: boolean;
    //default is ./logs/
  logGamePath?: string;
};
```

### Links

- [Visit Site](https://crystallinebliss.dev/)
- [Steam Page](https://store.steampowered.com/app/2547740/Crystalline_Bliss/)
- [Join Discord](https://discord.gg/XaWSsKQauC)
- [Watch On YouTube](https://www.youtube.com/channel/UC-02oe0-jCSy5KMqVSuXWbg)
