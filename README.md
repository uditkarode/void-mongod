# void-mongod
This binary in releases was generated using [staticx](https://github.com/JonathonReinhart/staticx) on the official Docker container of mongodb.
I've included a runit service to start it.

# Instructions
Make sure you have `git` and `wget` installed.
If not, you can do it with `xbps-install -S git wget`.

Run the following to install `mongod` with the service:
  
```bash
# or your own binary
wget https://github.com/uditkarode/void-mongod/releases/download/v5.0.3/mongod

chmod +x mongod
sudo mv mongod /usr/local/bin
cd /tmp
git clone --depth 1 https://github.com/uditkarode/void-mongod
cd void-mongod
sudo mv mongod.conf /etc/mongod.conf
sudo mv mongod /etc/sv
sudo ln -sv /etc/sv/mongod /var/service
sudo sv start mongod
```
  
If you see something like `warning: mongod: unable to open supervise/ok: file does not exist`, you can ignore it.
  
`mongod` is now running!
It will also autostart on every system boot.
The logs will be saved to `/tmp/sv/log/mongod/current`.

# Configuration
The config file is at `/etc/mongod.conf`. If you make any changes that involve logging/storing in new directories, make sure whatever directories you use exist on the filesystem. You can also add a line like `mkdir -p $YOUR_CUSTOM_FOLDER` in `/etc/sv/mongod/run`, just like and after the second line of that file just to be sure.
  
Note that mongod by default only accepts connections from localhost. If you want it to accept connections from anywhere, change the `127.0.0.1` in the configuration file to `0.0.0.0`.
