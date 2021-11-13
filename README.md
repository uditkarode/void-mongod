# void-mongod
This binary in releases was generated using [staticx](https://github.com/JonathonReinhart/staticx) on the official Docker container of mongodb.
I've included a runit service to start it.

# Instructions
First, download the most recent `mongod` binary from [releases](https://github.com/uditkarode/void-mongod/releases) (or make one yourself) and move it to `/usr/local/bin/mongod`.
Once you're done, run the following:
  
```bash
# Assuming you've dealt with adding mongod to your system already
chmod +x /usr/local/bin/mongod
cd /tmp
git clone --depth 1 https://github.com/uditkarode/void-mongod
sudo mv mongod /etc/sv
sudo ln -sv /etc/sv/docker /var/service
sudo sv start mongod
```

`mongod` will now run on system startup, and the logs will be saved to `/tmp/sv/log/mongod/current`.

