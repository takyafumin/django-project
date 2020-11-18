FROM python:3.8

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    nodejs npm \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

COPY requirements.txt /tmp/
RUN pip install --no-cache-dir -r /tmp/requirements.txt

CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]

