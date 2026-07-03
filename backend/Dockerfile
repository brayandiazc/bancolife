FROM python:3.14-slim

# Establecer directorio de trabajo
WORKDIR /app

# Instalar dependencias del sistema
RUN apt-get update && apt-get install -y \
  gcc \
  netcat-traditional \
  && rm -rf /var/lib/apt/lists/*

# Copiar archivo de dependencias
COPY requirements.txt .

# Instalar dependencias de Python
RUN pip install --no-cache-dir -r requirements.txt

# Copiar código de la aplicación
COPY . .

# Exponer puerto
EXPOSE 5000

# Comando para ejecutar la aplicación
CMD ["python", "app.py"] 