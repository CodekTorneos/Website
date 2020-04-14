# Setup
- this guide will show you how to setup 2PG and the dashboard to customize 2PG, using your own bot

**Requirements**:
- NodeJS (bot + webapp)
- MongoDB Server (bot + api)
- Java (bot -> music server)
- Angular (webapp)

- ask people to test setup

## Bot
- the backend
-> TypeScript, ExpressJS

### Setup
- guide to setting up 2PG, and starting the bot, and precompiled webapp
1) `Fork` the [2PG Repo](https://github.com/theADAMJR/2pg), or download it
2) Open the downloaded folder in terminal and type `npm i` to install required packages
- This is done within the root of the folder
- cd [appFolderPath] (windows/linux)
3) Create `config.json` within the same folder
- This is also done within the root of the folder
`config.json` example
- Remove comments (// comment...)
- Replace all values with 
```
{
    "bot": {
        "token": "yourBotToken", // used for bot user login
        "secret": "oauthSecret", // used for webapp login integration
        "id": "discordBotId" // used for webapp login integration
    },
    "api": {
        "url": "https://2pg.xyz/api", // used for xp cards etc.
        "managerPermission": "MANAGE_GUILD" // required permission for managing dashboard 
        "defaultBackgroundPath": "api/modules/image/wallpaper.png", // default XP card background image
        "stripe": { // used for charging users $ for features
            "apiKey": "stripeSecretKey"
        }
    },
    "webapp": {
        "url": "https://2pg.xyz", // the URL of the dashboard
        "distPath": "dist/twopg-dashboard" // the compiled webapp; contains index.html (created with 'ng build --prod' in webapp)
    },
    "lavalink": { // used for music server
        "password": "youshallnotpass"
    },
    "tests": { // optional -> used for tests
        "guild": {
            "id": "yourTestGuildId" // used for integration tests
        }
    },
    "mongoURL": "mongodb://localhost/2PG", // database URL (port 27017)
    "modules": ["announce", "auto-mod", "general", "music", "xp"] // enabled modules used for validation in API
}
```
4) Type `mongod` to start the Mongo database server instance
5) Type `npm run start:music` to start the music server instance
5) Type `npm start` to start the bot

### Notes
- the `dist` folder contains the precompiled dashboard which is the product of `ng build --prod`
- `http://localhost:3000` is the default webapp address

## Dashboard
- the front end
-> TypeScript, Angular 9
[!] All code, tokens etc. here is publically available as it is bundled with the webapp.
- Angular is a front-end framework that allows you to build professional, single page web and mobile applications.