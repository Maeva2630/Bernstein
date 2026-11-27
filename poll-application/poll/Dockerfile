FROM python:3.15-slim@sha256:63bb298d2b7b88f176f51b5189f54ce6535c997682ea70885d2132f5d473a8a5

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

RUN useradd --system --uid 10001 app
USER 10001

EXPOSE 80

CMD ["gunicorn", "--workers", "2", "--bind", "0.0.0.0:80", "wsgi:app"]
