# KONG API Gateway Stack basado en Docker #

## DESCRIPCION ##

Después de testear varias configuraciones para levantar un stack de Kong funcional he llegado a la configuración almacenada en este repositorio. Kong es una plataforma que proporciona un api gateway pensado bajo la arquitectura de microservicios.

## CONTENIDO ##
- PostgreSQL
- Kong (instancia para migración de parámetros)
- Kong (Server)
- Konga (Frontend para Kong)
- MongoDB (backend para Konga)

## Entornos ##
### Develop ###
Permite levantar stack en modo desarrollo con almacenamiento de las db dentro del contenedor correspondiente

### Load balancing y monitoreo ###
 Se agrega:
 - Traefik (HA-LB para contendores con agregación dinámica)**
 - CAdvisor (Monitoreo de contenedores con agreación dinámica)

***En caso de usar Traefik se deben agregar en la tabla hosts las siguientes URL:

127.0.0.1 konga.bydefault.test traefik.bydefault.test cadvisor.bydefault.test***

## BUILD Y EJECUCIÓN ##
### Docker Compose ###
#### Dev ####
`docker-compose -f docker-compose_dev.yml -d up`

#### Dev + LB ####
`docker-compose -f docker-compose_dev.yml -f docker-compose_lb-mon.yml -d up`

