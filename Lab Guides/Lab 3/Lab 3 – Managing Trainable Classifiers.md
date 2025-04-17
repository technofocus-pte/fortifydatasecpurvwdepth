# Laboratorio 3 – Gestión de clasificadores entrenables

## Objetivo:

El tenant de Contoso Ltd. contiene colecciones de sitios de SharePoint
que se usarán para almacenar documentos y reportes financieros, por lo
que deberá crear un clasificador entrenable para reconocer y etiquetar
estos archivos, activando clasificadores personalizados y creando uno
nuevo en este laboratorio.

## Ejercicio 1 – Creación de un clasificador entrenable

En esta tarea, Patti creará un nuevo clasificador entrenable y
seleccionará diferentes sitios de SharePoint para identificar datos
típicos creados y almacenados por Contoso Ltd.

1.  En **Microsoft Edge**, abra una **nueva ventana InPrivate**, vaya a
    `https://purview.microsoft.com` e inicie sesión como **Patti
    Fernandez** utilizando el nombre de usuario
    `PattiF``@{TENANTPREFIX``}.onmicrosoft.com` y la contraseña de
    usuario que figura en su pestaña de recursos.

2.  Desde el menú de navegación de la izquierda, seleccione
    **Solutions** \> **Data Loss Prevention**.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

3.  Expanda **Classifiers** desde el panel izquierdo. Seleccione
    **Trainable Classifiers** desde el panel de subnavegación.
    Seleccione **+ Create trainable classifier** para crear un nuevo
    clasificador.

![](./media/image2.png)

4.  Ingrese la siguiente información en la página **Name and describe
    your trainable classifier**:

    - Name: `Contoso Company Data`

    - Description:
      `Trainable classifier for company data produced and stored by Contoso Ltd.`

5.  Seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

8.  Seleccione **Choose sites** para abrir el panel lateral derecho.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

9.  Seleccione los siguientes sitios de SharePoint y seleccione **Add**.

    - Brand

    - Digital Initiative Public Relations

    - Work

    - Sales and Marketing

    - Mark 8 Project Team

![](./media/image5.png)

10. Espere hasta que el sitio elegido aparezca en la lista y seleccione
    **Next**.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

11. En la página **Source of the negative sample content**, seleccione
    el sitio **Learn**, y luego seleccione **Next**.

12. Revise la configuración y seleccione **Create trainable
    classifier**.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

13. Cuando aparezca el mensaje Your trainable classifier was created,
    seleccione **Done**.

Ahora se están analizando los documentos y archivos del sitio de
SharePoint elegido, lo que puede tardar hasta 24 horas. Una vez que esté
listo, puede realizar lo siguiente.

- Test the classifier

- Review the classifier

- Publish the classifier

Puede explorar los clasificadores ya existentes para una revisión más
detallada.

## Resumen:

Ha creado correctamente un clasificador personalizado entrenable que
coincide con los archivos almacenados en los sitios de SharePoint
existentes de Contoso Ltd.
