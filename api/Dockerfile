FROM python:3.10

WORKDIR /app
EXPOSE 5050

# Copy Pipenv files and install pipenv
COPY Pipfile Pipfile.lock ./
RUN pip install pipenv

# Use Python to generate requirements.txt
RUN python -c "import pipenv; print(pipenv.cli.pipenv.convert_deps_to_pip())" > requirements.txt || pipenv requirements > requirements.txt

# Install dependencies
RUN pip install -r requirements.txt

# Copy the rest of the app
COPY . .

# Run the app
CMD ["python", "main.py"]
