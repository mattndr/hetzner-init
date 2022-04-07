Usage example:
```
curl -X POST -H "Authorization: Bearer <TOKEN>" -H "Content-Type: application/json" -d '{"automount": false, "name": "myserver", "server_type": "cx21", "image": "ubuntu-20.04", "location": "nbg1", "firewalls": [], "networks": ["1480802"], "ssh_keys": ["mykey"], "volumes": [], "start_after_create": true, "user_data": "#include\nhttps://raw.githubusercontent.com/mattndr/hetzner-init/main/config-kubernetes.yaml"}' 'https://api.hetzner.cloud/v1/servers'
```
