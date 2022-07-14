<h1 align="center">RSS Feed Bot</h1> 

<hr>

A bot to post messages to Telegram Groups or Channels from rss feed.

This bot can also send /mirror commands to mirror bot using telegram account. Since one bot can't read another bot's message. So this bot will use TG account to interact with mirror bot. Fill `STR_SESSION` and `MIRROR_CHAT_ID` vars to enable it.

### Configuration Values
- `APP_ID` - Get it from [my.telegram.org](https://my.telegram.org/apps)
- `API_HASH` - Get it from [my.telegram.org](https://my.telegram.org/apps)
- `BOT_TOKEN` - Get it from [BotFather](https://t.me/BotFather)
- `FEED_URLS` - List of URLs of RSS Feed, sperated by `|` vertical bar.
- `LOG_CHAT` - ID of the Telegram Chat where messages are to be posted.
- `DATABASE_URL` - For Heroku, just add the `Heroku Postgres` add-on.
- `INTERVAL` - Checking Interval in seconds. (optional)
- `MAX_INSTANCES` - Max instances to be used while checking rss feed. (optional)

### Working as a Userbot to interact with mirror bot.

- `MIRROR_CHAT_ID` - Group/chat_id of mirror chat or mirror bot to send mirror command.
- `MIRROR_CMD` - if you have changed default command of mirror bot, replace this.
- `STR_SESSION` - String session, generate using your telegram mobile number for sending mirror command on your behalf. Generate by running
```
python gen_str.py 
```
(heroku users run in heroku console)

### How to Install Database ?

In the case of postgres, this is how you would set up a the database on a Arch Linux system. Other distributions may vary.

- Install postgresql:

`sudo pacman -Syy && sudo pacman -S postgresql`

- Change to the postgres user:

`sudo -iu postgres`

- Initialize the database cluster

`initdb --locale=en_US.UTF-8 -E UTF8 -D /var/lib/postgres/data`

- Create a new database user (change YOUR_USER appropriately):

`createuser -P -s -e YOUR_USER`

This will be followed by you needing to input your password.

- Create a new database table:

`createdb -O YOUR_USER YOUR_DB_NAME`

Change YOUR_USER and YOUR_DB_NAME appropriately.

- Testing your database connection:

`psql YOUR_DB_NAME -h YOUR_HOST YOUR_USER`

This will allow you to connect to your database via your terminal.
By default, YOUR_HOST should be 0.0.0.0:5432.

You should now be able to build your database URI. This will be:

`sqldbtype://username:pw@hostname:port/db_name`

To secure your DataBase installation, please read https://wiki.archlinux.org/index.php/PostgreSQL

Replace sqldbtype with whichever db youre using (eg postgres, mysql, sqllite, etc)
repeat for your username, password, hostname (localhost?), port (5432?), and db name.

## Deployment

### Deploying on Heroku
[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

### VPS or any other server/pc

- Install requirements from [requirements.txt](./requirements.txt)
```
pip3 install -r requirements.txt
```
- Deploy
```
python3 rss.py
```
