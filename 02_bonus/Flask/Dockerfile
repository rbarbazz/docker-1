FROM ubuntu

RUN apt-get update && apt-get install -y python-pip python-dev

COPY ./app /app

WORKDIR /app

RUN pip install -r requirements.txt

ENTRYPOINT ["python"]

CMD ["app.py"]

#Commands to use from this directory

#docker build -t flaski .
#docker run -it -p 5000:5000 flaski