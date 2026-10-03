# fastapi-pricing-service
An asynchronous, lightweight backend microservice built with Python and FastAPI to fetch, compute, and serve real-time financial market metrics. The service queries external price feeds non-blockingly using HTTPX, enforces data validation with Pydantic, and minimizes latency through an in-memory TTL caching layer.

## Features
- Non-blocking asynchronous external market queries powered by `httpx`.
- Strict input and output data validation using Pydantic models.
- In-memory TTL cache to reduce redundant API calls and outbound network latency.
- Computation of financial metrics (returns, percentage changes, weighted holding values).
- Auto-generated OpenAPI interactive documentation available via Swagger UI.

## Tech Stack
- **Python 3.11+**
- **FastAPI** (Asynchronous web framework)
- **Uvicorn** (ASGI web server)
- **HTTPX** (Asynchronous HTTP client)
- **Pydantic** (Data modeling and validation)

## Getting Started

### Prerequisites
- Python 3.11 or higher installed on your machine.

### Installation and Run
1. Clone the repository:
   git clone https://github.com/your-username/market-metrics-microservice.git
   cd market-metrics-microservice

2. Create and activate a virtual environment:
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate

3. Install required packages:
   pip install -r requirements.txt

4. Run the microservice:
   uvicorn main:app --reload

5. View interactive API documentation:
   Open your browser at `http://127.0.0.1:8000/docs`.

## Key Endpoints
- `GET /health`: Health-check endpoint for service monitoring.
- `GET /api/metrics/{ticker}`: Get latest quotes and computed indicators for a symbol.
- `POST /api/metrics/calculate`: Calculate holding returns based on payload parameters.
- `DELETE /api/cache`: Clear the in-memory quotation cache.
