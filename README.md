# Nest.js Lab (TypeScript Crash Course, Day 2)

Let's build an API for Rumblr (https://rumblr.webflow.io) in Nest.js and TypeScript!

### Resources

- Day 1 Repo: https://github.com/heypoom/typescript-crash-course
- Slides: TBD

### Installation

```bash
$ yarn
```

### Running the app

```bash
# development
$ yarn start

# watch mode
$ yarn start:dev

# production mode
$ yarn start:prod
```

## Test

```bash
# unit tests
$ yarn test

# e2e tests
$ yarn test:e2e

# test coverage
$ yarn test:cov
```

# Services and API Specs

The below API spec is provided as an example. You can ignore this entirely and create your own schema.

Take a look at the Rumblr screenshots and go wild. Feel free to add more response fields as you like! :D

APIs that should be covered from Rumblr:

- Fighters API
- Challenge API
- Fights API
- Chat API

## Fighters API

**Get 10 fighters for our Tinder-like feed**

Frontend should be able to specify the amount of fighters.

```
GET /fighters/?count=10

[
  { "username": "mattyice67", "photo": "https://i.pravatar.cc/850", "level": "amateur" },
  { "username": "poom", "photo": "https://i.pravatar.cc/850", "level": "expert" },
]
```

**Get a fighter by their username.**

- Ideas: Age, Height, Weight, Level, Last Fight, MMA Specialty, Record.
- Take a look at https://rumblr.webflow.io for inspiration :P

```
GET /fighters/mattyice67

{
  "photo": "https://i.pravatar.cc/850",
  "username": "mattyice67",
  "level": "amateur",
}
```

## Matches API

**Query the active matches with you.**

```
GET /matches

[
  {
    "username": "mattyice67",
    "photo": "https://i.pravatar.cc/850",
    "level": "amateur"
  },
]
```

**Challenge a fighter to a fight!**

```
POST /challenge/mattyice67
```

## Fights API

**Query nearby fights.**

```
GET /fights?near=13.111,100.69

{
  "fights": [
    {
      "fighters": ["mattyice67", "noobmaster69"],
      "location": { "lat": 0, "lon": 0 },
      "time": 1637306407807
    }
  ]
}
```

**Schedule a fight.**

```
POST /fights/schedule/mattyice67 {
  "location": { "lat": 0, "lon": 0 },
  "time": 1637306407807
}
```

**Cancel a fight.**

```
POST /fights/cancel/mattyice67
```

## Chat API

**Add a chat message**

```
POST /messages/mattyice67 {
  "message": "Bro, your face is pissing me off. Wanna throw down?"
}
```

**Query the chat messages.**

```
GET /messages/mattyice67

[
  { "from": "mattyice67", "message": "Hell yeah bro, I'mma f*ck you up.", "timestamp": 1637306628892 }
  { "from": "noobmaster69", "message": "Bro, your face is pissing me off. Wanna throw down?", "timestamp": 1637306628892 }
]
```
