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

# Project: https://github.com/52North/wps

## Install required dependencies > none?!

# Download release and deploy in Tomcat, see docs at https://wiki.52north.org/SensorWeb/SensorObservationServiceIVDocumentation
WORKDIR $CATALINA_HOME/webapps
RUN curl -L -o wps.war http://52north.org/downloads/send/15-wps/492-52n-wps-webapp-3-5-0 \
    #&& unzip -d wps wps.zip
    # \
    # webapp name fixed in several config files of the bundle
    #&& mv wps.war $CATALINA_HOME/webapps

# TODO geotools package: http://52north.org/downloads/send/15-wps/493-wps-3-5-0-geotools-package
# TODO change run command to use wps-config-file??

# docker build -t 52n-wps .
# docker run --name wps -p 80:8080 52n-wps
# http://localhost/wps
# Login: wps/wps