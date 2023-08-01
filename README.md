# Ansible Role: mirsg.tomcat

A role for installing and configuring Apache Tomcat.

## Role Variables

`tomcat_version`: The version of Tomcat to install. Defaults to `9.0.76`

`tomcat_webapp_name`: The name of the root web app. Defaults to "ROOT".

`tomcat`: A dictionary that contains the following:

`catalina_home`: The installation location. Defaults to "/usr/share/tomcat".

`config_file`: The location of the configuration file. Defaults to
"/usr/share/tomcat/conf/tomcat.conf".

`server_config_file`: The web app configuration file. Defaults to
"/usr/share/tomcat/conf/server.xml".

`service_config_file`: The location of the systemd service file. Defaults to
"/etc/systemd/system/tomcat.service".

`owner`: The OS user that has ownership of Tomcat. Defaults to "tomcat".

`group`: The default OS group the `owner` belongs in. Defaults to "tomcat".

`hostname`: The hostname of the deployed web app. Defaults to `localhost`.

`server_port`: The server port. Defaults to `8005`.

`catalina_port`: The catalina port. Defaults to `8983`.

`catalina_redirect_port`: Catalina port for redirects. Defaults to `8443`.

`shutdown_port`: Port for triggering server shutdown. Defaults to `8005`.

`port`: The web app HTTP port. Defaults to `8080`.

`root`: The root web app location. Defaults to "/usr/share/tomcat/webapps/{{
tomcat_webapp_name }}".

`root_webapp`: Path to the root web app war file. Defaults to
"/usr/share/tomcat/webapps/{{ tomcat_webapp_name }}.war".

`binary_url`: The URL of the binary to install from. Defaults to:

```yaml
"https://archive.apache.org/dist/tomcat/tomcat-\
{{ tomcat_version.split('.')[0] }}/v{{ tomcat_version }}/bin/\
apache-tomcat-{{ tomcat_version }}.tar.gz"
```

`items_to_restore`: A list containing the following items to be restored after
an upgrade. Defaults to:

```yaml
- "/usr/share/tomcat_bkp/webapps"
- "/usr/share/tomcat_bkp/.postgresql"
- "/usr/share/tomcat_bkp/logs"
- "/usr/share/tomcat_bkp/install_downloads"
```

## Example Playbook

Including an example of how to use your role (for instance, with variables
passed in as parameters) is always nice for users too:

```yaml
- hosts: servers
  roles:
    - { role: mirsg.tomcat }
```

## License

BSD

## Author Information

This role was created by the [Medical Imaging Research Software
Group](https://www.ucl.ac.uk/advanced-research-computing/expertise/research-software-development/medical-imaging-research-software-group)
at [UCL](https://www.ucl.ac.uk/).
