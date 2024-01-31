# Docker-команда FROM вказує базовий образ контейнера
# Наш базовий образ - це Linux з попередньо встановленим python
FROM python:3.11

# Встановимо змінну середовища
ENV FINAL_PROJECT /finalproject
# Встановимо робочу директорію всередині контейнера
WORKDIR $FINAL_PROJECT

COPY pyproject.toml $FINAL_PROJECT/pyproject.toml
COPY poetry.lock $FINAL_PROJECT/poetry.lock

# Встановимо залежності всередині контейнера
RUN pip install poetry
RUN poetry config virtualenvs.create false && poetry install --only main

# Скопіюємо інші файли в робочу директорію контейнера
COPY . .

# Позначимо порт, де працює застосунок всередині контейнера
EXPOSE 5000

# Запустимо наш застосунок всередині контейнера
CMD ["python", "__main__.py"]