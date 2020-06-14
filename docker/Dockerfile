FROM amd64/python:3.8 as base 

FROM base as builder 

# Install dependencies
RUN mkdir /app 
COPY ./opt/requirements.txt /app
WORKDIR /app
RUN export TMPDIR='/var/tmp'

RUN pip install --prefix=/app -r ./requirements.txt

FROM base

COPY --from=builder /app /usr/local
COPY ./opt/app /app
WORKDIR /app
EXPOSE 8080
CMD ["python3", "./app.py"]
