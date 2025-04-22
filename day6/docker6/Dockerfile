FROM python:3.11-slim

WORKDIR /app
COPY /giropops-senhas/requirements.txt .
COPY /giropops-senhas/app.py .
COPY /giropops-senhas/templates templates/
COPY /giropops-senhas/static static/

RUN  pip install -r requirements.txt

EXPOSE 5000

CMD ["flask", "run","--host=0.0.0.0"]