FROM nginx:alpine
#ARG ARTIFACT_URL
#ADD $ARTIFACT_URL .
#RUN unzip artifacts.zip
RUN pwd
COPY --chown=nginx:nginx ./dist/ /usr/share/nginx/html
COPY ./nginx/testfront.conf /etc/nginx/conf.d/default.conf
RUN ls -lah
