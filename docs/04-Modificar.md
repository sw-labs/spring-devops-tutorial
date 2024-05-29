# 4. Modificar

Al modificar la aplicación es necesario desplegar una nueva versión en la nube.


---

1. Revise la aplicación en la rama `feature/nueva-version`

    ```
    git checkout feature/nueva-version
    mvn spring-boot:run -pl helloworld
    ```

2. Haga un pull request e incorpore el cambio en la rama `main`

3. Revise el pipeline para ver si la aplicación se desplegó apropiadamente en el slot de `stage`

4. Revise la aplicación en el slot de `stage`


---
Siguiente: [5. Desplegar de nuevo](05-Desplegar.md)