# void-mongod
This binary in releases was generated using [staticx](https://github.com/JonathonReinhart/staticx) on the official Docker container of mongodb.
I've included a runit service to start it.

# Instructions
run the following:
  
```bash
# or your own binary
wget https://github.com/uditkarode/void-mongod/releases/download/v5.0.3/mongod

chmod +x mongod
sudo mv mongod /usr/local/bin
cd /tmp
git clone --depth 1 https://github.com/uditkarode/void-mongod
cd void-mongod
sudo mv mongod /etc/sv
sudo ln -sv /etc/sv/mongod /var/service
sudo sv start mongod
```

`mongod` will now run on system startup, and the logs will be saved to `/tmp/sv/log/mongod/current`.

