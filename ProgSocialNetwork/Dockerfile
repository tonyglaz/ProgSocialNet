FROM python:3.7

WORKDIR /usr/src/app

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1


RUN apt-get update \
    && apt-get install netcat -y
RUN apt-get upgrade -y && apt-get install \
    postgresql gcc python3-dev musl-dev -y

COPY ./req.txt /usr/src/req.txt
RUN pip install -r /usr/src/req.txt

COPY ./entrypoint.sh /usr/src/app/


COPY . /usr/src/app

RUN chmod 755 /usr/src/app/prestart.sh

EXPOSE 8000

#RUN apt-get update \
#    && apt-get install netcat -y
#RUN apt-get upgrade -y && apt-get install postgresql gcc python3-dev musl-dev -y
#RUN curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | POETRY_HOME=/opt/poetry python && \
#    cd /usr/local/bin && \
#    ln -s /opt/poetry/bin/poetry && \
#    poetry config virtualenvs.create false
#
#COPY ./pyproject.toml ./poetry.lock* /usr/src/app/
#
#RUN poetry install
#
##COPY ./entrypoint.sh /usr/src/app/
#
#COPY . /usr/src/app/
#
#RUN chmod 755 /usr/src/app/prestart.sh
##CMD /usr/src/app/prestart.sh
##ENTRYPOINT sh /usr/src/app/entrypoint.sh