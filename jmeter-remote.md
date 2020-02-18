# JMETER REMOTE (MASTER-SLAVE)

## Master config

- `cd apache-jmeter-5.1.1/bin/`
- `vi jmeter.properties` add list ip remote host at `remote_hosts=127.0.0.1,10.0.3.133` separate by comma
- `vi user.properties` enable and change config `server.rmi.ssl.disable=true`
- run command: `./jmeter-server` to sart server.
- open a ssh terminal to run command: `./jmeter -n -t /home/ubuntu/jmeter-run/example1.jmx -R 10.0.1.19,10.0.3.133 -l /home/ubuntu/jmeter-run/600userslogin.jtl`

## Slave config

- `cd apache-jmeter-5.1.1/bin/`
- `vi user.properties` enable and change config `server.rmi.ssl.disable=true`
- `./jmeter-server -Jparam=n` n is the order number of server


## Optional

- For run a server independency: `JVM_ARGS="-Xms3072m -Xmx3072m" /home/ubuntu/apache-jmeter-5.1.1/bin/jmeter -n -t /home/ubuntu/jmeter-run/SFS_Booking_Hotel_Services_2.jmx -l /home/ubuntu/jmeter-run/200us_dashboard_2003.jtl`
- For set RAM in use of java: `export _JAVA_OPTIONS="-Xms1536m -Xmx3072m"`


## Note

- Need to config log file output at `log4j2.xml` (@todo)