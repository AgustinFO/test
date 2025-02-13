# Solución

Decidí implementar una pipeline en Github Actions.

Previamente tuve que crear un nuevo workflow y configuré el archivo .yaml, al hacer el primer commit me creo el directorio .github/workflow. Además tuve que agregar los secrets para poder acceder a DockerHub.

La pipeline implementada se activa cuando se realiza un push y se detectan cambios en el index.html asociado al nginx, por lo que el path es 'prueba3/index.html'.
La pipeline se divide en 2 jobs:

- docker_build:
    - Checkout code: Se clona el repositorio.
    - Docker Login: Logea a una cuenta de Dockerhub.
    - Build and Push: Buildea la imagen y la pushea a DockerHub, utilizando como tags el nombre de usuario, el sha y la rama donde se implementa el cambio.

- deployment:
    - Checkout Code: se clona el repositorio
    - Deploy with Docker Compose: Levanta el servicio en una maquina virtual.

Alternativa no implementada:

Dependiendo el caso lo óptimo sería que la pipeline inicie en una rama que no sea la main, por ej. en una rama de staging o dev para poder testear los cambios realizados haciendo por ejemplo pruebas unitarias y luego hacerse un merge a la rama main, para luego hacer el deployment en la instancia o plataforma que se requiera.
El deployment en este caso es una mera demostración para probar el workflow.