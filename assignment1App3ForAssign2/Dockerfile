FROM python:2.7
MAINTAINER siddharth "siddharth.daftari@gmail.com"
COPY . /app
WORKDIR /app
RUN pip install -r requirements.txt
ENTRYPOINT ["python"]
EXPOSE 3002
CMD ["app.py"]
