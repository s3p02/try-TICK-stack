# Trying out tick stack

Telegraf - Agent that writes to InfluxDb, collects and reports metrics

InfluxDb - Timeseries Database,SCHEMA on the fly

Chronograf - UI

Kapacitor - Real-Time Streaming Data Processing Engine


## Why choose InfluxDb:

	1. Easy to get started
	2. Familiar query syntax
	3. No external dependencies : Written entirely in go [ Chuck Pro's ]
	4. Allows regular & irregular time series
	5. Scales Horizontally
	6. Not just a Db: Entire platform available TICK stack
	7. Can be used with Grafana

## Influx: Easier compared to Casandra, MongoDb, elastic and redis in terms of effort required, extra work, overhead with HIGH write & HIGH querying 


## 1. Install INfluxDb: on Ubuntu

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


```
show users

```
Edit Config: Locate the [http] section, uncomment the auth-enabled option, and set its value to true 


```
sudo vim /etc/influxdb/influxdb.conf 
```

```
sudo systemctl restart influxdb
```
Influx CLI
```
influx -username 'user_name' -password 'pass_word'
```

## 2. Install Telegraf: on Ubuntu


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


Influx CLI
```
influx -username 'user_name' -password 'pass_word'
```

```
show databases

use telegraf

show measurements

```

## 3. Install Kapacitor:

```
wget https://dl.influxdata.com/kapacitor/releases/kapacitor_1.5.1_amd64.deb

sudo dpkg -i kapacitor_1.5.1_amd64.deb

sudo apt-get update && sudo apt-get install kapacitor	
```
Locate the [[influxdb]] section and enter InfluxDb user_name & pass_word:

```
sudo vim /etc/kapacitor/kapacitor.conf
```

```
sudo systemctl start kapacitor
```

```
kapacitor list tasks
```

## 4. Install Chronograf:

```
wget https://dl.influxdata.com/chronograf/releases/chronograf_1.2.0~beta5_amd64.deb

sudo dpkg -i chronograf_1.2.0~beta5_amd64.deb

sudo systemctl start chronograf

```

Defaults to port 8888, no config available as of now, will be in future versions. Enable port 8888

http://your_server_ip:8888 or http://localhost:8888 if you've installed it locally.
