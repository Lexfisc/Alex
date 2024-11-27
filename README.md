# Alex Cisneros 
import requests

# URL base de la API (modificar según la documentación oficial)
base_url = "https://api.lib.harvard.edu/v2/items"

# Parámetros de búsqueda
query_params = {
    "q": "derecho constitucional",  # Buscar tema específico
    "start": 0,                     # Iniciar desde el primer resultado
    "limit": 10                     # Número de resultados por consulta
}

try:
    # Hacer la solicitud a la API
    response = requests.get(base_url, params=query_params)

    # Verificar el estado de la respuesta
    if response.status_code == 200:
        data = response.json()  # Convertir respuesta a JSON
        items = data.get("items", [])

        # Imprimir los títulos de los resultados
        for item in items:
            title = item.get("title", "Sin título")
            print(f"Título: {title}")
    else:
        print(f"Error en la solicitud: {response.status_code}")

except Exception as e:
    print(f"Ocurrió un error: {e}")