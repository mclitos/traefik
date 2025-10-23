# traefik
## Gestor de dominios docker

Clona el Repositorio
```
git clone https://github.com/mclitos/traefik
```
Entra en la Carpeta
```
cd traefik
```
Edita el yml con el E-mail valido he un dominio propio valido 
```
 sudo nano docker-compose.yml
```
Levanta el Contenedor
```
docker-compose up -d
```


### Ver en "ip:8080"

## Para Añadir a los contenedores u aplicaciones 

```
    networks:
      - traefik_proxy
    labels:
      - traefik.enable=true
      - traefik.http.services.nombre-app.loadbalancer.server.port=80   # Poner el puerto interno que corresponda 
      - traefik.http.routers.nombre-app.rule=Host(`tudominio.com`)     # Poner un dominio válido y redirigir los DNS
      - traefik.http.routers.nombre-app.entrypoints=web,websecure
      - traefik.http.routers.nombre-app.tls=true
      - traefik.http.routers.nombre-app.tls.certresolver=myresolver

networks:
  traefik_proxy:
    external: true 
```
## Cambiar "nombre-app" por el que corresponda al servicio.
