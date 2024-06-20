# Installing Litecoin on Ubuntu (Any Version)

- Visit [litecoin.org](https://litecoin.org/) and get the latest download link for Litecoin.

(At the time of writing its 0.21.3, if there is a newer release please change the values accordingly)

```console
$ cd ~
```
```console
$ wget https://download.litecoin.org/litecoin-0.21.3/linux/litecoin-0.21.3-x86_64-linux-gnu.tar.gz
```
```console
$ tar -zxvf litecoin-0.21.3-x86_64-linux-gnu.tar.gz
```
```console
$ sudo install -m 0755 -o root -g root -t /usr/local/bin ~/litecoin-0.21.3/bin/*
```
```console
$ rm -rf ~/litecoin-0.21.3/ litecoin-0.21.3-x86_64-linux-gnu.tar.gz
```

After running the above commands, you can now use `litecoind` and `litecoin-cli` from anywhere in your terminal to control your node.

# Configuration

Let's setup our litecoin configuration file;

```console
$ cd ~
```
```console
$ mkdir .litecoin
```
```console
$ cd .litecoin
```
```console
$ nano litecoin.conf
```

Paste this into your `litecoin.conf` nano editor.

**(You "MUST" change rpcuser and rpcpassword values with strong credentials or you risk your wallets being compromised)**

```bash
rpcuser=CHANGEME     # YOU MUST CHANGE
rpcpassword=CHANGEME # YOU MUST CHANGE

# KEEP IF YOU WANT TO PRUNE YOUR BLOCKCHAIN #
#txindex=1
blockfilterindex=0
peerblockfilters=0

# OTHER SERVER SETTINGS #
server=1             # This enables our node to be used as a server, this lets us control our wallets and use in applications.
rpcbind=127.0.0.1    # Allows only access to the node from OUR ip.
bind=127.0.0.1       # Runs our node on our local ip

# This keeps the Litecoin process in background so we can close our terminal
daemon=1

# PRUNE #
prune=5120           # 5,120 MB aka 5GB
```

Press `CTRL + X` then press `Y` to save & exit the nano editor.

# Start Litecoind
Now for the best and easiest part, simply run `litecoind` to start the daemon.
```console
$ litecoind
```
