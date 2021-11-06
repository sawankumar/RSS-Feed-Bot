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

### Deploying on Railway
[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/new/template?template=https%3A%2F%2Fgithub.com%2Fsawankumar%2FRSS-Feed-Bot&plugins=postgresql&envs=API_ID%2CAPI_HASH%2CFEED_URLS%2CBOT_TOKEN%2CLOG_CHANNEL%2CINTERVAL%2CMAX_INSTANCES%2CMIRROR_CHAT_ID%2CMIRROR_CMD%2CSTR_SESSION&optionalEnvs=MIRROR_CHAT_ID%2CMIRROR_CMD%2CSTR_SESSION&API_IDDesc=Get+it+from+my.telegram.org&API_HASHDesc=Get+it+from+my.telegram.org&FEED_URLSDesc=RSS+Feed+URL+of+the+site.+Split+by+%7C+if+there+are+more+than+one.&BOT_TOKENDesc=Get+it+by+creating+a+bot+on+https%3A%2F%2Ft.me%2Fbotfather&LOG_CHANNELDesc=Create+a+channel+%2C+send+a+message+and+forward+that+message+to+%40username_to_id_bot+%2C+you+will+get+channel+id.&INTERVALDesc=Times+between+checks.&MAX_INSTANCESDesc=1+is+more+than+enough.&MIRROR_CHAT_IDDesc=Only+useful+if+u+filled+string+session+variable.+This+will+send+mirror+commands+on+your+behalf+to+the+mentioned+chat+id.&MIRROR_CMDDesc=Only+useful+if+u+filled+string+session+variable.Mirror+command+of+your+bot.&STR_SESSIONDesc=Fill+this+if+you+wanna+setup+autoleech+or+automirror+system.&INTERVALDefault=30&MAX_INSTANCESDefault=1)

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