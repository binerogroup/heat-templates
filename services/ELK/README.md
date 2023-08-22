# ELK Stack Deployment using OpenStack Heat

This Heat template automates the deployment of the ELK Stack (Elasticsearch, Logstash, Kibana) on OpenStack. Follow the steps below to deploy and configure the ELK Stack.

## Configuration

### Elasticsearch

1. **Access Elasticsearch:**
   - Retrieve the Elasticsearch node IP:

     ```bash
     openstack stack output show <stack_name> ElasticSearch_Node
     ```

   - Access Elasticsearch at `http://<elasticsearch_ip>:9200`.

2. **Bootstrap Password:**
   - The bootstrap password for Elasticsearch is generated during the deployment. You can retrieve it using:

     ```bash
     openstack stack output show <stack_name> BootstrapPassword
     ```

   - Use the bootstrap password for authenticating as the built-in users like `elastic` when required.

   - Initial passwords for the ELK stack can be found in elasticsearch server.
     ```bash
     cat /var/lib/cloud/scripts/per-instance/passwords.txt
     ```

### Logstash

1. **Logstash Configuration:**
   - Logstash is configured to read logs from `/var/log/*`. Adjust the Logstash configuration in the `logstash_userdata` section of the Heat template (`elk_stack_template.yaml`) to meet your specific log processing needs.

     - Refer to Logstash documentation for configuration details: [Logstash Configuration](https://www.elastic.co/guide/en/logstash/current/configuration.html)

     - Refer to Logstash documentation for adding Beats input: https://www.elastic.co/guide/en/logstash/current/input-plugins.html

   - To include other log files, update the Logstash configuration file (`/etc/logstash/conf.d/logstash.conf`) with additional `input` blocks.

   - Update the `<elasticsearch_ip>` in `logstash.conf`

   - After modifying the Logstash configuration, restart Logstash:

     ```bash
     systemctl restart logstash
     ```

   - Verify that Logstash is running without errors:

     ```bash
     systemctl status logstash
     ```

### Kibana

1. **Configure Kibana:**
   - Login to kibana server
   - Add the following details in the file `/etc/kibana/kibana.yml`:

     ```bash
     elasticsearch.password: "Get the password from Bootstrap passwords file, this password is Kibana_system password"
     elasticsearch.hosts: "["http://<elasticsearch_ip>:9200"]"
     ```
   - Save the file and restart kibana service.
     ```bash
     sudo systemctl restart kibana
     ```

2. **Access Kibana:**
   - Retrieve the Kibana link:

     ```bash
     openstack stack output show <stack_name> Kibana_Link
     ```

   - Access Kibana at the provided link (e.g., `http://<kibana_ip>:5601`).

3. **Login to Kibana:**
   - Open the Kibana link in a web browser.
   - Log in using the username `elastic` and the bootstrap password obtained earlier.

4. **Index Pattern:**
   - In Kibana, go to the "Management" tab.
   - Click on "Index Patterns" and create an index pattern for the Elasticsearch indices.

5. **Discover Logs:**
   - Go to the "Discover" tab in Kibana to start exploring and visualizing logs.

### Documentation:
   - Refer to Elastic documentation for detailed information on Elasticsearch, Logstash, and Kibana: [Elastic Documentation](https://www.elastic.co/guide/index.html)
