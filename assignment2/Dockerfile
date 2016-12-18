FROM python:2.7
MAINTAINER siddharth "siddharth.daftari@gmail.com"
COPY . /proxy
WORKDIR /proxy
RUN pip install -r requirements.txt
ENTRYPOINT ["python"]
EXPOSE 8000
CMD ["proxyServer.py"]
