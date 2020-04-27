# Instalación de Grafana

1. Install the prerequisite package:

    `sudo apt-get install libfontconfig`

2. Download and install Grafana using the .deb package provided on the Grafana download page:

    `wget https://dl.grafana.com/oss/release/grafana_5.4.3_amd64.deb`

    `sudo dpkg -i grafana_5.4.3_amd64.deb`

3. Ensure Grafana starts at boot:

    `sudo systemctl enable --now grafana-server`

4. Access Grafana's web UI by going to IPADDRESS:3000.

5. Log in with the username admin and the password admin. Reset the password when prompted.

## Add a Data Source

1. Click Add data source on the homepage.

2. Select Prometheus.

3. Set the URL to <http://localhost:9090.>

4. Click Save & Test.

## Add a Dashboard

1. From the left menu, return Home.

2. Click New dashboard. The dashboard is automatically created.

3. Click on the gear icon to the upper right.

4. Set the Name of the dashboard to Forethought.

5. Save the changes.
