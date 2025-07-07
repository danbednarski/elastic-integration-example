# Example API Integration

This is a generic integration for interacting with APIs, originally based on Elastic's built-in [Sophos Central package](https://github.com/elastic/integrations/tree/main/packages/sophos_central).

```bash
$ git clone https://github.com/danbednarski/elastic-integration-example.git
$ cd elastic-integration-example
$ elastic-package build
Package built: /home/administrator/elastic-integration-example/integrations/build/packages/name-version.zip
```

Currently, the API we're calling relies on a temporary domain from localhost.run. This is no longer necessary now that we've got HTTP requests working, and I'll switch to a stable, free, third party API on Monday. Anyway, take the ZIP file from the output.

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
  --data-binary @<name-version.zip>
{"items":[{"id":"logs-name.event-version","type":"ingest_pipeline"},{"id":"logs-name.event","type":"index_template"},{"id":"logs-name.event@package","type":"component_template"},{"id":"logs-name.event@custom","type":"component_template"}],"response":[{"id":"logs-name.event-version","type":"ingest_pipeline"},{"id":"logs-name.event","type":"index_template"},{"id":"logs-name.event@package","type":"component_template"},{"id":"logs-name.event@custom","type":"component_template"}],"_meta":{"install_source":"upload"}}
```

At this point, the package will appear as available to install in the Kibana UI:

_(lol later I'll add a screenie here i promise)_

When selecting which host to install the agent on, make sure to specify the field node:

<img width="806" alt="Screenshot 2025-07-05 at 11 37 35 PM" src="https://github.com/user-attachments/assets/22a1e769-5cff-43d0-abca-e5971b74341a" />

To verify that it's working, you'll want to check the index `sophos_central.event` on the manager's Kibana dev console. (Will change this so we create our own index)

#### Todo:
- [x] Connect to operational API
- [x] Engrave into ElasticSearch
- [ ] Switch to free Pokemon API
- [ ] Remove leftover cruft data  
- [ ] Switch to proper VIPRE API
- [ ] Clean up data after ingest
- [ ] Autodeploy package via API

אשרי הגפרור שנשרף והצית להבות,  
אשרי הלהבה שבערה בסתרי לבבות.  
אשרי הלבבות שידעו לחדול בכבוד...  
אשרי הגפרור שנשרף והצית להבות.
