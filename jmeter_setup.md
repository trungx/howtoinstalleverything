# INSTALLING JMETER

## Requirement

- Linux 64-bit x86 ubuntu 18.04 (micro: 1CPU, 1GB RAM, 50GB SSD)
- JDK 11.0.4/13 or higher
- Jmeter 5.1.1 or higher

## Install JDK

- `sudo apt update`
- JDK 11:
  - `apt-get install default-jdk`
- JDK 13:
  - `sudo add-apt-repository ppa:linuxuprising/java`
  - `sudo apt-get update`
  - `sudo apt-get install oracle-java13-installer`
- `javac -version`  or  `java --version`

## Install Jmeter

- `wget http://mirrors.viethosting.com/apache//jmeter/binaries/apache-jmeter-5.1.1.zip`
- `apt-get update && apt-get install zip` then `unzip apache-jmeter-5.1.1.zip`

## Install Jmeter Plugin

- `cd apache-jmeter-5.1.1.zip/lib/`
- `wget -O cmdrunner-2.2.jar http://search.maven.org/remotecontent?filepath=kg/apc/cmdrunner/2.2/cmdrunner-2.2.jar`
- `cd apache-jmeter-5.1.1.zip/lib/ext/`
- `wget -O jmeter-plugins-manager-1.3.jar http://search.maven.org/remotecontent?filepath=kg/apc/jmeter-plugins-manager/1.3/jmeter-plugins-manager-1.3.jar`
- `cd apache-jmeter-5.1.1.zip/`
- `java -cp lib/ext/jmeter-plugins-manager-1.3.jar org.jmeterplugins.repository.PluginManagerCMDInstaller`
- Verify installation: `cd bin/ && ./PluginsManagerCMD.sh help`
- Install plugin [Weighted Switch Controller]: `./PluginsManagerCMD.sh install jpgc-wsc`
  
## Config Jmeer log file

- Config file: `apache-jmeter-5.1.1/bin/log4j2.xml`
- Todo: understand config file
  