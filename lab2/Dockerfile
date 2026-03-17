FROM python:3.9-slim

WORKDIR /app

RUN apt-get update && apt-get install -y curl vim

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY app.py .

RUN useradd -m -u 1000 appuser
USER appuser

EXPOSE 5000

ENV FLASK_ENV=production

CMD ["python", "app.py"]