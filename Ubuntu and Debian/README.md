#Problem [0]

**Update and Upgrade**

"sudo apt-get update && sudo apt-get upgrade"

`E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)`


`E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?`


#Solution [0]

**Type these command in your terminal:**

`sudo fuser -vki /var/lib/dpkg/lock`

`sudo fuser -vki /var/cache/apt/archives/lock`

`sudo fuser -vki /var/cache/debconf/config.dat`

`sudo dpkg --configure -a`

#Tips [0]

**How to remove unused Linux headers?**

#Way [0]

**Type these command in your terminal:**


`sudo apt-get purge $(dpkg -l linux-{image,headers}-"[0-9]*" | awk '/ii/{print $2}' | grep -ve "$(uname -r | sed -r 's/-[a-z]+//')") 
`

#Tips [1]

**How to remove java 7 and install java 8?**

#Way [0]

**Type these command in your terminal:**

`sudo rm /var/lib/dpkg/info/oracle-java7-installer*`

`sudo apt-get purge oracle-java7-installer*`

`sudo rm /etc/apt/sources.list.d/*java*`

`sudo apt-get update`

`sudo add-apt-repository ppa:webupd8team/java`

`sudo apt-get update`

`sudo apt-get install oracle-java7-installer`