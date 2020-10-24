# MWDB Core

Malware repository component for automated malware collection/analysis systems. 

Formerly known as Malwarecage.

Under the hood of [mwdb.cert.pl service](https://mwdb.cert.pl) hosted by CERT.pl.

## Setup & documentation

If you want to learn more about setting up your own mwdb-core instance or mwdb.cert.pl service: go to the [mwdb-core documentation](https://mwdb.readthedocs.io/en/latest/).

```
sudo apt-get install build-essential libffi-dev python3 python3-dev python3-pip libfuzzy-dev
pip3 install ssdeep

sudo apt install docker.io
sudo docker run -d --name mwdb-postgres -e POSTGRES_DB=mwdb -e POSTGRES_USER=mwdb -e POSTGRES_PASSWORD=mwdb -p 127.0.0.1:54322:5432 postgres

pip3 install wheel
pip3 install mwdb-core

~/.local/bin/mwdb-core configure
choose 2
postgresql://mwdb:mwdb@127.0.0.1:54322/mwdb
enter 2x

screen
~/.local/bin/mwdb-core run
(ctrl ar)

sudo apt-get update
sudo apt-get install nginx
sudo unlink /etc/nginx/sites-enabled/default
cd etc/nginx/sites-available/
nano reverse-proxy.conf
paste this...

"
server {
    listen 80;
    location / {
        proxy_pass http://192.x.x.2;
    }
}
"

sudo ln -s /etc/nginx/sites-available/reverse-proxy.conf /etc/nginx/sites-enabled/reverse-proxy.conf\
mv default default.bak
service nginx configtest
service nginx restart
```

## Features

- Storage for malware binaries and static/dynamic malware configurations
- Tracking and visualizing relations between objects
- Quick search
- Data sharing and user management mechanism
- Integration capabilities via webhooks and plugin system

**Query your malware dataset with ease**

![](docs/_static/44dwH7g.gif)

![](docs/_static/uRL9dt6.gif)

**Convenient interface for your own analysis backend**

![](docs/_static/whJxE0j.png)

**Store configurations in organized way**

![](docs/_static/eMmEaQo.png)

**Visualize relationship between objects**

![](docs/_static/XPiIboW.gif)

## Contact

If you have any problems, bugs or feature requests related to MWDB, you're encouraged to create a GitHub issue. If you have other questions, question is related strictly with mwdb.cert.pl service or you want to contact the current maintainers directly, you can email:

- Paweł Srokosz (psrok1@cert.pl)
- Jarosław Jedynak (msm@cert.pl)
- CERT.PL (info@cert.pl)

## License

This software is licensed under [GNU Affero General Public License version 3](http://www.gnu.org/licenses/agpl-3.0.html) except for plugins.

For more information, read [LICENSE](LICENSE) file.

In case of any questions regarding the license send an e-mail to info@cert.pl.

![Co-financed by the Connecting Europe Facility by of the European Union](https://www.cert.pl/wp-content/uploads/2019/02/en_horizontal_cef_logo-1.png)
