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
# along with this program. If not, see <http://www.gnu.org/licenses/>.
FROM nginx:1.11
MAINTAINER Daniel Nüst <daniel.nuest@uni-muenster.de>

# Project: https://github.com/52North/helgoland

## Install required dependencies, including late Node.js
RUN apt-get update \
    && apt-get install -y --no-install-recommends --fix-missing \
    #ca-certificates \
    #build-essential \
	unzip \
    bzip2 \
    git \
    curl

RUN curl -sL https://deb.nodesource.com/setup_6.x | bash - \
	&& apt-get install -y \
    nodejs \
    && rm -rf /var/lib/apt/lists/*

#ENV branch master
ENV BRANCH develop

# Download sources, build, copy build to install loation, remove temp files
# Cannot simply run "npm install" because I'm root (need --allow-root for bower, and maybe --unsafe-perm for npm install), so instead run bower install  manually as well; then run grunt to get the distribution package in ./dist
WORKDIR /tmp
RUN curl -LO https://github.com/52North/helgoland/archive/$BRANCH.zip \
    && unzip $BRANCH.zip

WORKDIR /tmp/helgoland-$BRANCH
RUN npm install \
    && npm install -g bower \
    && bower install --allow-root \
    && npm install -g grunt \
    && grunt \
    && cp -r dist/* /usr/share/nginx/html/ \
    && cd .. \
    && rm -r helgoland-$BRANCH \
    && rm -r $BRANCH.zip

# Configure: https://github.com/52North/sensorweb-client-core#configuration and http://sensorweb.demo.52north.org/jsClient/settings.json
WORKDIR /usr/share/nginx/html
COPY settings.json settings.json

# leave default CMD
# docker build -t 52n-helgoland .
# docker run --name helgoland -p 80:80 52n-helgoland
# http://localhost