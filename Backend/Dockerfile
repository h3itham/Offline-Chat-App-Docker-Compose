FROM python:3.8-alpine 
RUN mkdir /src
WORKDIR /src
COPY server/ /src 
RUN apk add  --virtual .build-deps python3-dev gcc musl-dev build-base jpeg-dev zlib-dev mariadb-connector-c-dev\
    && pip install --upgrade pip \
    && apk del .build-deps
RUN pip install PyMySQL
RUN pip install -r requirements.txt 

CMD ["python", "manage.py", "migrate" ]
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]

