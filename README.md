# BLAPI - the BotListAPI

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/ebd62ee46cd84964975ae65ac9462fa1)](https://app.codacy.com/app/T0TProduction/BLAPI?utm_source=github.com&utm_medium=referral&utm_content=T0TProduction/BLAPI&utm_campaign=Badge_Grade_Dashboard)
[![dependencies Status](https://david-dm.org/T0TProduction/BLAPI/status.svg)](https://david-dm.org/T0TProduction/BLAPI) [![install size](https://packagephobia.now.sh/badge?p=blapi)](https://packagephobia.now.sh/result?p=blapi) [![jsDelivr](https://data.jsdelivr.com/v1/package/npm/blapi/badge?style=rounded)](https://www.jsdelivr.com/package/npm/blapi)

[![nodei](https://nodei.co/npm/blapi.png)](https://nodei.co/npm/blapi/)

BLAPI is a package to handle posting your discord bot stats to botlists.

It's intended to be used with discord.js, though you can also manually post your stats.

BLAPI fully supports external and discord.js internal sharding with and without the use of the [BotBlock API](https://botblock.org/api/docs#count).

## Installation

### NPM (recommended)

```bash
npm i blapi
```

### Yarn

```bash
yarn add blapi
```

## Usage

The list of all supported bot lists and their respective names for the apiKeys object are listed [below](https://github.com/T0TProduction/BLAPI#lists)

### With discord.js

```js
const Discord = require("discord.js");
const blapi = require("blapi");

let bot = new Discord.Client({ autoReconnect: true });

// Post to the APIs every 60 minutes; you can leave out the repeat delay as it defaults to 30
// If the interval is below 3 minutes BLAPI will not use the BotBlock API because of ratelimits
blapi.handle(bot, apiKeys, 60);
```

### Manually, without need of Discord libraries

```js
// If you want to post sharddata you can add the optional parameters
// shardID and shardCount should both be integers
// shardsArray should be an integer array containing the guildcounts of the respective shards
blapi.manualPost(guildCount, botID, apiKeys[, shardID, shardCount[, shardsArray]]);
```

### Turn on extended logging

```js
// Use this to get more detailed logging when using botBlock
// Errors will always be logged
blapi.setLogging(True);
```

### Turn off the use of the BotBlock API

```js
// Use this to turn off BotBlock usage
// By default it is set to true
blapi.setBotblock(False);
```

### apiKeys

The JSON object which includes all the API keys should look like this:

```json
{
  "bot list domain": "API key for that bot list",
  "bot list domain": "API key for that bot list",
  "bot list domain": "API key for that bot list"
}
```

an example would be:

```json
{
  "bots.ondiscord.xyz": "dsag38_auth_token_fda6gs",
  "discordbots.group": "qos56a_auth_token_gfd8g6"
}
```

## Lists

This is a list of all supported discord bot lists:

| Domain                 | Supports sharding | Is not extremely annoying |
|------------------------|-------------------|---------------------------|
| botlist.space          | ✔️ | ✔️ |
| botsfordiscord.com     | ❌ | ✔️ |
| bots.ondiscord.xyz     | ❌ | ✔️ |
| discord.boats          | ❌ | ✔️ |
| discordboats.club      | ❌ | ✔️ |
| discordbotindex.com    | ❌ | ✔️ |
| discordbots.org        | ✔️ | ❌ |
| discordbotlist.com     | ✔️ | ✔️ |
| discordbotlist.xyz     | ❌ | ✔️ |
| ls.terminal.ink        | ❌ | ✔️ |
| discordbotsreview.tk   | ❌ | ✔️ |
| discordbot.world       | ❌ | ✔️ |
| discord.bots.gg        | ✔️ | ✔️ |
| discordbotslist.com    | ❌ | ✔️ |
| discordbots.group      | ❌ | ✔️ |
| discord.services       | ❌ | ✔️ |
| discordsbestbots.xyz   | ✔️ | ✔️ |
| discordsextremelist.tk | ❌ | ✔️ |
| divinediscordbots.com  | ✔️ | ✔️ |


These lists are supported by being hardcoded, but BLAPI will always look for new additions on startup via the [BotBlock API](https://botblock.org/api/docs#lists)


If at any time you find other bot lists have added an API to post your guildcount, let us know on this repo or by contacting T0TProduction#0001 on Discord.

## Credit

All the people who helped making BLAPI are listed in [AUTHORS](https://github.com/T0TProduction/BLAPI/blob/master/AUTHORS)

By default we use the [BotBlock API](https://botblock.org/api/docs#count) to post all the data
