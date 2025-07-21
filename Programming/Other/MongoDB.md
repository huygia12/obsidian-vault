### Control mongodb server
- Start mongodb server:
```bash
sudo systemctl start mongod
```

- Check mongodb server status:
```bash
sudo systemctl status mongod
```

- Run mongodb automatically whenever power-on:
```bash
sudo systemctl enable mongod
```

- Check if mongodb server run in local properly:
```bash
sudo netstat -plntu | grep 27017
```
