FROM python:alpine3.6
ENV PYTHONUNBUFFERED 1
RUN apk add --update --no-cache \
    libffi-dev \
    build-base \
    postgresql-dev \
    linux-headers \
    zlib-dev \
    jpeg-dev
RUN pip3 install --no-cache-dir uwsgi
RUN mkdir /code
WORKDIR /code
ADD requirements /code/requirements
RUN pip3 install --no-cache-dir -r requirements/production.txt
ADD src /code/
ADD docker /docker
CMD ["/docker/app/docker-entrypoint.sh"]
