  
<a href="https://github.com/vdarkobar/Home_Cloud#proxmox">Home</a> | <a href="https://github.com/vdarkobar/NextCloud/blob/main/README.md#nextcloud">NextCloud</a>
  
#### Edit *config.php* file:
```
sudo nano /home/<USER>/NextCloud/files/config/config.php
```  
  
 Slow login, edit: *'overwrite.cli.url' => ...*
```
# change to (if using domain name):
'overwrite.cli.url' => 'https://example.com', 'overwritehost' => 'example.com', 'overwriteprotocol' => 'https',
# or (if subdomain):
'overwrite.cli.url' => 'https://subdomain.example.com', 'overwritehost' => 'subdomain.example.com', 'overwriteprotocol' => 'https',
```
Default landing app after login, add at the end:*
```
'defaultapp' => 'files',
# ...
  'installed' => true,
  'instanceid' => 'ocjoficzuewq',
  'defaultapp' => 'files',
);
```