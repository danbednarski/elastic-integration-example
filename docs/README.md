# Example API Integration

```
$ git clone (this)
$ elastic-package build
```

This will create some-name-version.zip

```bash
$ scp some-name-version.zip <manager-host-ip>:/home/otm
$ ssh otm@<manager-host-ip>
[otm@<manager-hostname> ~]$ # snag the so_elastic user pw
[otm@<manager-hostname> ~]$ sudo cat /opt/so/saltstack/local/pillar/elasticsearch/auth.sls
[otm@<manager-hostname> ~]$ curl -XPOST \
  -H 'content-type: application/zip' \
  -H 'kbn-xsrf: true' \
  http://127.0.0.1:5601/api/fleet/epm/packages \
  -u 'so_elastic:<elastic_password>' \
  --data-binary @sophos_central-1.19.0.zip
{"items":[{"id":"logs-sophos_central.event-1.19.0","type":"ingest_pipeline"},{"id":"logs-sophos_central.event","type":"index_template"},{"id":"logs-sophos_central.event@package","type":"component_template"},{"id":"logs-sophos_central.event@custom","type":"component_template"}],"response":[{"id":"logs-sophos_central.event-1.19.0","type":"ingest_pipeline"},{"id":"logs-sophos_central.event","type":"index_template"},{"id":"logs-sophos_central.event@package","type":"component_template"},{"id":"logs-sophos_central.event@custom","type":"component_template"}],"_meta":{"install_source":"upload"}}
```

The password comes from ``

Testing with custom API (localhost.run)

Seeing the request come into 

#### Todo:
- [x] Connect to operational API
- [x] Engrave into Elasticsearch
- [ ] Switch to proper VIPRE API
- [ ] Clean up data after ingest

אשרי הגפרור שנשרף והצית להבות,  
אשרי הלהבה שבערה בסתרי לבבות.  
אשרי הלבבות שידעו לחדול בכבוד...  
אשרי הגפרור שנשרף והצית להבות.
