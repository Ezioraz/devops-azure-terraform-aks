FROM python:3.11-slim

# Set working directory
WORKDIR /app

# Create non-root user (security best practice)
RUN addgroup --system appgroup && adduser --system appuser --ingroup appgroup

# Copy only requirements first (layer caching)
COPY requirements.txt .

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY app.py .

# Switch to non-root user
USER appuser

# Expose app port
EXPOSE 5000

# Run the app
CMD ["python", "app.py"]
