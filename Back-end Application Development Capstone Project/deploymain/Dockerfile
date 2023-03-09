# 1. insert code to python:3.9.16-slim as base image
FROM python:3.8.2


ENV PYTHONBUFFERED 1
ENV PYTHONWRITEBYTECODE 1

RUN apt-get update \
    && apt-get install -y netcat

ENV APP=/app

# 2. insert code to change the working directory to $APP
WORKDIR $APP
# 3. insert code to copy the requirements.txt file to $APP
COPY requirements.txt $APP
# 4. insert code to install requirements from requirements.txt
RUN pip3 install -r requirements.txt
# 5. insert code to copy the rest of the files into $APP
COPY . $APP
# 6. insert code to expose the port here 
EXPOSE 8000

RUN chmod +x /app/entrypoint.sh

ENTRYPOINT ["/bin/bash","/app/entrypoint.sh"]

# 7. insert code to set the run command to "python manage.py runserver 0.0.0.0:8000"

CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]