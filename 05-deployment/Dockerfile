# Base our image on this and add things on top of it
FROM python:3.8.12-slim 

RUN pip install pipenv

WORKDIR /app

COPY ["Pipfile", "Pipfile.lock", "./"]

RUN pipenv install --system --deploy

COPY ["predict.py", "model_C=1.0.bin", "./"]

EXPOSE 9696

ENTRYPOINT ["gunicorn", "--bind=0.0.0.0:9696", "predict:app"]

# docker run -it --rm python:3.8.11-slim (docker will find the image and download it)
# docker run -it --rm --entrypoint=bash python:3.8.12-slim (go in the image using terminal)

## apt-get update
## apt-get install wget

# docker build -t zoomcamp-test . (build an image called zoomcamp-test by using the Docker file in this directory ./.)
# docker run -it --rm --entrypoint=bash zoomcamp-test
# docker build -t zoomcamp-test .
# docker run -it --rm zoomcamp-test
# docker run -it --rm -p 9696:9696 zoomcamp-test