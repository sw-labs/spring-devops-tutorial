# 2. Crear App Service

Para desplegar la aplicación en Azure App Services es necesario crear un Plan de App Service y crear una Aplicación Web.

---

1. (Si no tiene) Cree una suscripción de Azure para Estudiantes

    - Ir al sitio https://azure.microsoft.com/en-us/free/students
    - Ingresar sus datos y crear la suscripción

2. Cree un grupo de recursos

3. Cree un Plan de App Services

    - Cree un plan de tipo `Premium v3 P0V3` o algún otro que soporte slots

4. Cree una Aplicación Web en el plan 

    - Utilice el stack de `Java 21`
    - No habilite (aún) el despliegue continuo con Github Actions
    - No habilite el esquema de monitoreo
    - Asigne etiquetas al nuevo recurso
        - Ambiente: Desarrollo
        - Proyecto: Ejemplo

5. Revise la aplicación web que acaba de crear

----
Siguiente: [3. Desplegar](03-Desplegar.md)
