FROM tomcat:9
MAINTAINER Daniel Nüst <daniel.nuest@uni-muenster.de>
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

# Project: https://github.com/52North/sos

## Install required dependencies > none?!

# Download release and deploy in Tomcat, see docs at https://wiki.52north.org/SensorWeb/SensorObservationServiceIVDocumentation
WORKDIR /tmp
RUN curl -L -o sos-bundle.zip http://52north.org/downloads/send/3-sos/491-52n-sensorweb-sos-bundle-4-3-7 \
    && unzip -d sos-bundle sos-bundle.zip \
    # webapp name fixed in several config files of the bundle
    && cp sos-bundle/*/bin/target/*.war $CATALINA_HOME/webapps/52n-sos-webapp.war \
    && rm -r *

# TODO add local configuration file, requires building the service: https://wiki.52north.org/SensorWeb/SensorObservationServiceIVDocumentation#C1_41_Building_a_Preconfigured_Service
# 

# FIXME http://localhost/52n-sos-webapp/static/client/jsClient and http://localhost/52n-sos-webapp/static/doc/api-doc are not available

# leave default CMD
# docker build -t 52n-sos .
# docker run --name sos -p 80:8080 52n-sos
# http://localhost/52n-sos-webapp