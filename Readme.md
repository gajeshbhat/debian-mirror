# Steps and Notes to setup a Debian Mirror on local PC with a static IP

## Hardware Requirements and Notes to consider
The hardware requirements for running a Debian mirror can vary greatly depending on the specifics of what you're mirroring (i.e., the number of architectures and sections you're mirroring), how often you update your mirror, the number of users accessing your mirror, your network capacity, and various other factors.

Here are some general minimum requirements:

1. **Disk Space:** The biggest factor is the size of the Debian archive you're mirroring. According to latest [figures](https://www.debian.org/mirror/size), at the time this note is being written full mirror (including all architectures and all sections of 'main', 'contrib', and 'non-free', as well as 'stable', 'testing', and 'unstable' releases) required over 4TB of storage. If you're just mirroring a single architecture (like 'amd64') and just the 'main' section, it will require significantly less space (~500 GB), but still several hundred gigabytes. Keep in mind that these figures are continuously increasing as more packages are added to the Debian repositories.

2. **CPU:** CPU usage for maintaining a mirror is generally quite low, since the work is largely I/O-bound rather than CPU-bound. A modest CPU should suffice.

3. **Memory:** RAM requirements are also not particularly high. Again, a modest amount (e.g., 2GB) should suffice in most cases.

4. **Network:** A fast and stable internet connection is crucial, especially if you plan to serve a larger number of users. You'll need sufficient bandwidth to handle multiple simultaneous connections. (Make sure your connection is not metered or has very high bandwidth availability, as mirroring can consume a large amount of bandwidth.)

5. **Operating System:** A stable Linux distribution, such as Debian itself, is generally a good choice for running the mirror. (I chose Debian 11 basic CLI installation)

Remember that these are very rough estimates and your specific requirements may vary. Monitoring your server's resource usage and adjusting as necessary is a good idea.


## Domain name and IP requirements

It is suggested that your domain name resolves to one IP address only. If you have multiple IP addresses, you should choose one to use for your mirror and make sure that your domain name resolves to that IP address only.

Make sure you setup your A record on your domain provider or whichever that manages your DNS records. In my case, I have a domain name registered with Godaddy  and I have setup an A record to point to my static IP address.

## Setting up the Debian Mirror

1. Download the latest version of ftpsync from the official repository. This is the recommended tool for mirroring the Debian archive.

```bash
curl -O https://ftp-master.debian.org/ftpsync.tar.gz
```

2. Extract the archive.

```bash
tar -xzf ftpsync.tar.gz
```

3. Create three folders, one to store the ftpsync binary file(bin), one for the ftpsync.conf(etc) and one to manage logs(logs). These can be in your home directory or anywhere you prefer.

```bash
mkdir -p ~/ftpsync/bin
mkdir -p ~/ftpsync/etc
mkdir -p ~/ftpsync/logs
```

4. Copy the ftpsync binary file (from extracted zip file) to the bin folder.

```bash
cp ftpsync ~/ftpsync/bin
```

5. Create a new file called ftpsync.conf in the etc folder and add the following lines to it. Replace the values with your own.

```bash


```
