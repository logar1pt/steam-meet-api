FROM python:3.9

ENV PYTHONUNBUFFERED=1 LANG=ru_RU.UTF-8 LANGUAGE=ru_RU LC_ALL=ru_RU.UTF-8

RUN groupadd -r app && useradd -r -g app app \
    && apt-get update \
    && pip install -U pip \
    && pip install poetry

COPY ./pyproject.toml ./poetry.lock /
COPY ./docker/etc/start-dev.sh /start-dev.sh

RUN chmod +x ./start-dev.sh
RUN apt-get update
RUN poetry config virtualenvs.create false && poetry install

WORKDIR /app

EXPOSE 8010
