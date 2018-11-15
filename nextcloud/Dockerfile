FROM linuxserver/nextcloud

RUN apk update && \
    apk add --no-cache --update tesseract-ocr && \
    apk search -qe 'tesseract-ocr-data-*' | xargs apk add --no-cache --update
    
RUN mkdir -p /var/run/s6/services/fulltextsearch
ADD ./fulltextsearch /var/run/s6/services/fulltextsearch/run
RUN chmod +x /var/run/s6/services/fulltextsearch/run
