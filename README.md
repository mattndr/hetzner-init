Usage example:
```
curl -X POST -H "Authorization: Bearer <TOKEN>" -H "Content-Type: application/json" -d '{"automount": false, "name": "master-node-1", "server_type": "cx21", "image": "ubuntu-20.04", "location": "nbg1", "firewalls": [{"firewall": "359468"}], "networks": ["1480802"], "ssh_keys": ["mykey"], "volumes": [], "start_after_create": true, "user_data": "#include\nhttps://raw.githubusercontent.com/mattndr/hetzner-init/main/config.yaml", "labels": {"type":"master"}}' 'https://api.hetzner.cloud/v1/servers'
```
