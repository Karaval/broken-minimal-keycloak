FROM	python:3.8-slim
LABEL	name="minimal keycloak app"
LABEL	version="1.0"
LABEL	MAINTAINER="Jonathan.picard1607@gmail.com"
ENV	PYTHONUNBUFFERED=1
RUN	adduser --disabled-login worker
USER	worker
WORKDIR	/home/worker
COPY	--chown=worker requirements.txt .
RUN 	python3 -m pip install -r requirements.txt \
	&& rm requirements.txt
COPY	app.py .
ENTRYPOINT	["gunicorn", "app:app", "--bind=0.0.0.0:8000", "--workers=4", "--log-level=debug", "--reload"]
