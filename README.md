# try-TICK-stack
trying out tick stack

Why choose InfluxDb:

	1. Easy to get started
	2. Familiar query syntax
	3. No external dependencies : Written entirely in go [ Chuck Pro's ]
	4. Allows regular & irregular time series
	5. Scales Horizontally
	6. Not just a Db: Entire platform available TICK stack
	7. Can be used with Grafana

Influx: Easier compared to Casandra, MongoDb, elastic and redis in terms of effort required, extra work, overhead with HIGH write & HIGH querying 


# Install INfluxDb: on Ubuntu

```
sudo apt-get install influxdb

sudo systemctl start influxdb

systemctl status influxdb

```

Create User:


```
CREATE USER "user_name" WITH PASSWORD 'pass_word' WITH ALL PRIVILEGES

```
See Users created:


```show users

```
Edit Config: Locate the [http] section, uncomment the auth-enabled option, and set its value to true 


```
sudo vim /etc/influxdb/influxdb.conf 
```

```
sudo systemctl restart influxdb
```



# Install Telegraf: on Ubuntu


``` wget https://dl.influxdata.com/telegraf/releases/telegraf_1.7.4-1_amd64.deb

sudo dpkg -i telegraf_1.7.4-1_amd64.deb

sudo apt-get update && sudo apt-get install telegraf 
```


Edit Config:

Locate the [outputs.influxdb] section and provide username and password


```

sudo vim /etc/telegraf/telegraf.conf


```

Start Telegraf:


```
sudo systemctl restart telegraf

```
