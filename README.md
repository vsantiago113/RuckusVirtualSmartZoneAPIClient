# RuckusVirtualSmartZoneAPIClient
[Ruckus - Virtual SmartZone - High Scale Public API Reference Guide](http://docs.ruckuswireless.com/smartzone/5.2.1/vszh-public-api-reference-guide-521.html 'Ruckus - Virtual SmartZone - High Scale Public API Reference Guide')<br />

---

An API Client for the Virtual SmartZone - High Scale Public API Reference Guide to be able to easily use the API in a more standard way.

## How to install
```ignorelang
$ pip install RuckusVirtualSmartZoneAPIClient
```

## Usage
The argument 'method' must be specify every time.

#### Default arguments and attributes
```python
import RuckusVirtualSmartZoneAPIClient

client = RuckusVirtualSmartZoneAPIClient.Client(verify=False, warnings=False, api_version='v9_1')

client.get(url=None, method='', data=None, auth = None)

# client.headers
# client.base_url
# client.token
# client.auth
# client.server

```

#### Authentication
```python
import RuckusVirtualSmartZoneAPIClient

client = RuckusVirtualSmartZoneAPIClient.Client()
client.connect(url='https://localhost:8443', username='admin', password='Admin123')

client.disconnect()
```

#### The first query
```python
import RuckusVirtualSmartZoneAPIClient
import json

client = RuckusVirtualSmartZoneAPIClient.Client()
client.connect(url='https://localhost:8443', username='admin', password='Admin123')

zone_id = '1234567890asdfg'
response = client.get(method=f'/rkszones/{zone_id}/apgroups')
print(json.dumps(response.json(), indent=4))

client.disconnect()
```

#### Creating
```python
import RuckusVirtualSmartZoneAPIClient
import json

client = RuckusVirtualSmartZoneAPIClient.Client()
client.connect(url='https://localhost:8443', username='admin', password='Admin123')

zone_id = '1234567890asdfg'
response = client.post(method=f'/rkszones/{zone_id}/apgroups', data={'name': 'apGroupName',
                                                                     'description': 'apGroupDescription',
                                                                     'location': 'Location'})
print(json.dumps(response.json(), indent=4))

client.disconnect()
```

#### Updating
```python
import RuckusVirtualSmartZoneAPIClient
import json

client = RuckusVirtualSmartZoneAPIClient.Client()
client.connect(url='https://localhost:8443', username='admin', password='Admin123')

zone_id = '1234567890asdfg'
response = client.put(method=f'/rkszones/{zone_id}/apgroups', data={'name': 'apGroupNewName'})
print(json.dumps(response.json(), indent=4))

client.disconnect()
```

#### Deleting
```python
import RuckusVirtualSmartZoneAPIClient

client = RuckusVirtualSmartZoneAPIClient.Client()
client.connect(url='https://localhost:8443', username='admin', password='Admin123')

zone_id = '1234567890asdfg'
group_id = 'asdfgh123654798'
response = client.delete(method=f'/rkszones/{zone_id}/apgroups/{group_id}')
print(response.status_code)

client.disconnect()
```
