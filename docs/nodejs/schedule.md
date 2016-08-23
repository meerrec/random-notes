### How to use time schedule in node

> 2015-09-16
> Haochuan

#### [node-schedule](https://github.com/tejasmanohar/node-schedule)

- Syntax

```js
var schedule = require('node-schedule');

var j = schedule.scheduleJob('42 * * * *', function(){
    console.log('The answer to life, the universe, and everything!');
});
```
- About Cron Format

```
*    *    *    *    *    *
┬    ┬    ┬    ┬    ┬    ┬
│    │    │    │    │    |
│    │    │    │    │    └ day of week (0 - 7) (0 or 7 is Sun)
│    │    │    │    └───── month (1 - 12)
│    │    │    └────────── day of month (1 - 31)
│    │    └─────────────── hour (0 - 23)
│    └──────────────────── minute (0 - 59)
└───────────────────────── second (0 - 59, OPTIONAL)
```

Example: 

```
42 * * * * * // when minute is 42

*/5 * * * * * // every 5 sec
```

- More options

    - [node-cron](https://github.com/ncb000gt/node-cron)
    - [later](https://github.com/bunkat/later)


