FROM python:3

RUN set -eux; \
  export DEBIAN_FRONTEND=noninteractive \
  && apt-get update \
  && apt-get install -y --no-install-recommends \
             jq \
             man \
             unzip \
             vim \
             zip \
             liblzo2-dev \
  && rm -rf /var/lib/apt/lists/*

RUN mkdir /code
WORKDIR /code

RUN echo "from flask import Flask\napp=Flask(__name__)\napp.run('0.0.0.0')" > /code/app.py  

COPY requirements.txt /code/
RUN set -eux; \
  pip install -r requirements.txt

CMD ["python", "app.py"]
