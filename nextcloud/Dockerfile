# hadolint disable=DL3007
FROM nextcloud:latest

ENV INOTIFY_CONFIG="/inotifyscan.ini"

RUN apt-get update && \
    apt-get -y --no-install-recommends install \
        gosu \
        inotify-tools \
        imagemagick \
        python \
        smbclient \
        tesseract-ocr \
        tesseract-ocr-deu \
        tesseract-ocr-jpn \
        unzip && \
    curl -o /tmp/master.zip https://codeload.github.com/Blaok/nextcloud-inotifyscan/zip/master && \
    unzip /tmp/master.zip -d /usr/local/src && \
    rm /tmp/master.zip && \
    /bin/chmod +x /usr/local/src/nextcloud-inotifyscan-master/nextcloud-inotifyscan && \
    ln -s /usr/local/src/nextcloud-inotifyscan-master/nextcloud-inotifyscan /usr/local/bin/nextcloud-inotifyscan && \
    mkdir -p /etc/inotifyscan && \
    apt-get -y remove unzip && \
    apt-get -y autoremove && \
    rm -rf /var/lib/apt/lists/* && \
    groupadd -g 1000 share && \
    usermod -a -G share root && \
    usermod -a -G share www-data
RUN mv /entrypoint.sh /entrypoint-nextcloud.sh
COPY ./inotifyscan.sh /entrypoint.sh
