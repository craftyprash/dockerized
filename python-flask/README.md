# Dockerize a Python flask web app

In the code we use host and port mapping:

```console
app.run(host='0.0.0.0', port='80')
```

Dockerfile for flask:

```console
FROM python:3.9

WORKDIR /code

COPY ./requirements.txt /code/requirements.txt

RUN pip install --no-cache-dir --upgrade -r /code/requirements.txt

COPY ./app /code/app

CMD [ "python", "app/main.py" ]
```

Run below commands to build and run Flask app:

```console
$ docker build -t flaskapi-image .
$ docker run -p 80:80 flaskapi-image
```

Open URL to invoke the Flask API:

```console
http://localhost
```