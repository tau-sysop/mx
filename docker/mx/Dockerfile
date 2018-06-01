# @(#) $Tau: mx/docker/mx/Makefile $

## ------------------------------------------------------------------------- ##
##                          T A U    P R O J E C T                           ##
## ------------------------------------------------------------------------- ##
##                                                                           ##
##  Licensed under the Apache License, Version 2.0 (the "License");          ##
##  you may not use this file except in compliance with the License.         ##
##                                                                           ##
##  You may obtain a copy of the License at:                                 ##
##                                                                           ##
##      http://www.apache.org/licenses/LICENSE-2.0                           ##
##                                                                           ##
##  Unless required by applicable law or agreed to in writing, software      ##
##  distributed under the License is distributed on an "AS-IS" BASIS,        ##
##  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. ##
##  See the License for the specific language governing permissions and      ##
##  limitations under the License.                                           ##
##                                                                           ##
## ------------------------------------------------------------------------- ##

FROM tauproject/core:shimmer
WORKDIR /tmp
RUN DEBIAN_FRONTEND=noninteractive \
	apt-get update -qq -y && \
	apt-get install -qq -y postfix inetutils-syslogd

EXPOSE 10025/tcp
EXPOSE 10587/tcp

RUN mkdir -p /app/etc /app/config /app/mail /app/db /app/ssl
COPY scripts/docker/entrypoint /app/entrypoint
COPY docker/mx/main.cf /app/config/main.cf
COPY docker/mx/master.cf /app/config/master.cf

CMD [ "run" ]

ENTRYPOINT [ "/app/entrypoint" ]
