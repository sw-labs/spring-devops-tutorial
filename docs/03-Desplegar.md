# 3. Desplegar

Es posible desplegar la aplicación usando un pipeline de Github Actions. Existen varias formas de crear este pipeline. La forma más sencilla puede ser  el uso del portal de Azure.

---

1. En el portal de Azure, seleccione la aplicación web a utilizar. 

2. Cree un nuevo slot, seleccionando en el menú a la izquierda la opción `Slots` / `Espacios de Implementación` y haciendo clic en `Add slot`.

    - Defina `stage` como nombre del slot.

3. Seleccione el slot que acaba de crear.

4. Genere el pipeline de implementación en la página del slot, seleccionando la opción `Centro de Implementación` 

    - En origen, seleccione `Github`
    - Seleccione el usuario, organización, repositorio y rama del repositorio con el código fuente
    - Seleccione `identidad asignada por el usuario`

5. (Opcionalmente) revise el código fuente del pipeline haciendo clic en `Archivo de versión preliminar`

6. Haga clic en el botón de Guardar ubicado en la parte superior.

7. En Github, vaya al repositorio del proyecto. Observe los pipelines en ejecución en la sección de `Actions`. El flujo puede aparecer con errores.

8. Seleccione el pipeline que ha fallado y haga clic en el nombre del archivo, debajo del título del pipeline.

8. Modifique el archivo del pipeline para corregir los errores

    - Modifique la versión de Java, para usar la versión 21 con la distribución Zulu.

    ```
      - name: Set up Java version
        uses: actions/setup-java@v1
        with:
          java-version: '21'
          distribution: 'zulu'    
    ```

    - Modifique el comando de compilación para que no se ejecuten las pruebas

    ```
      - name: Build with Maven
        run: mvn clean install -DskipTests
    ```

    - Modifique la tarea de grabación del paquete para utilizar los binarios de la carpeta de `helloworld`

    ```
      - name: Upload artifact for deployment job
        uses: actions/upload-artifact@v3
        with:
          name: java-app
          path: '${{ github.workspace }}/helloworld/target/*.jar'        
    ```


9. Haga clic en el botón `Commit` en la parte superior derecha. Ingrese una descripción y guarde el archivo.

10. Revise de nuevo la sección de `Actions` y verifique que el pipeline funciona bien.

11. Revise el funcionamiento de la aplicación en el slot de `stage`

12. Intercambie el slot de `stage` al stage de `producción`

13. Revide el funcionamiento de la aplicaicón en el slot de `producción`

---
Siguiente: [4. Modificar Aplicación](04-Modificar.md)