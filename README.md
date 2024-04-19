# pnp-metrics-api
## Usage examples
### CURL
### NOTE: If you are getting errors with adding the PNP data source and testing it we have added the fix to this release.
#### also fixed the problem where the data returned would always be 0. 
##### Query metrics of a service on a specific host
```
curl -s -u '<username>:<password>' -H "Content-Type: application/json" -X POST -d '
{
   "targets":[
      {
         "host":"host1.example.org",
         "service":"_HOST_",
         "perflabel":"rta",
         "type":"AVERAGE"
      },
      {
         "host":"host2.example.org",
         "service":"_HOST_",
         "perflabel":"rta",
         "type":"AVERAGE"
      }
   ],
   "start":'UNIXEPOCHTIMESTAMP_START',
   "end":'UNIXEPOCHTIMESTAMP_END'
}' https://example.org/pnp4nagios/index.php/api/metrics
```
#### List all hosts
```
curl -s -u '<username>:<password>' https://example.org/pnp4nagios/index.php/api/hosts
```

#### List services of a host
```
curl -s -u '<username>:<password>' -H "Content-Type: application/json" -X POST -d '
{
   "host":"host.example.org"
}' https://example.org/pnp4nagios/index.php/api/services
```

You can use regular expressions for host lists:

```
curl -s -u '<username>:<password>' -H "Content-Type: application/json" -X POST -d '
{
   "host":"/^local"
}' https://example.org/pnp4nagios/index.php/api/services
```


#### List labels of a service of specific host
```
curl -s -u '<username>:<password>' -H "Content-Type: application/json" -X POST -d '
{
   "host":"host.example.org",
   "service":"_HOST_"
}' https://example.org/pnp4nagios/index.php/api/labels
```
