**Laboratorio 3 – Administrar clasificadores entrenables**

**Introducción**

El tenant de **Contoso Ltd.** contiene una colección de sitios de **SharePoint** llamada **"Sales and Marketing"**, que se utilizará en el futuro para almacenar varios documentos e informes relacionados con finanzas. Debido a la naturaleza de estos documentos, es necesario crear un **trainable classifier** para reconocer y etiquetar estos archivos. Para este propósito, en este laboratorio activará clasificadores entrenables personalizados y creará uno nuevo.

**Objetivos**

- Crear un **trainable classifier** para identificar y categorizar datos típicos almacenados en los sitios de **SharePoint** seleccionados.

**Ejercicio 1 – Crear un clasificador entrenable**

En esta tarea, **Patti** creará un nuevo **trainable classifier** y seleccionará diferentes sitios de **SharePoint** para identificar los datos típicos creados y almacenados por **Contoso Ltd**.

1.  En **Microsoft Edge**, abra una **New InPrivate Window**, navegue a [**https://purview.microsoft.com**](https://purview.microsoft.com) e inicie sesión como **Patti Fernandez** usando el usuario **<PattiF@WWLxXXXXXX.onmicrosoft.com>** y la contraseña proporcionada en la pestaña de recursos.

2.  En la navegación izquierda, seleccione **Solutions \> Data Loss Prevention**.

> <img src="media/image1.png" style="width:6.26806in;height:3.30486in" />

3.  Expanda **Classifiers** en el panel izquierdo. Seleccione **Trainable Classifiers** en el subpanel de navegación. Seleccione **+ Create trainable classifier** para crear un nuevo clasificador.

> <img src="media/image2.png" style="width:6.26806in;height:3.30694in" />

4.  Ingrese la siguiente información:

5.  Name: **+++Contoso Company Data+++**

6.  Description: **+++Trainable classifier for company data produced and stored by Contoso Ltd.+++**

7.  Seleccione **Next**.

> <img src="media/image3.png" style="width:6.26806in;height:3.32014in" alt="A screenshot of a computer Description automatically generated" />

8.  Seleccione **Choose sites** para abrir el panel derecho.

> <img src="media/image4.png" style="width:6.26806in;height:3.32014in" alt="A screenshot of a computer Description automatically generated" />

9.  Seleccione los siguientes sitios de **SharePoint** y haga clic en **Add**:

    - Brand

    - Digital Initiative Public Relations

    - Work

    - Sales and Marketing

    - Mark 8 Project Team

> <img src="media/image5.png" style="width:6.26806in;height:3.32014in" />

10. Espere hasta que los sitios seleccionados se muestren en la lista y seleccione **Next**.

> <img src="media/image6.png" style="width:6.26806in;height:3.32014in" alt="A screenshot of a computer Description automatically generated" />

11. En la página **Source of the negative sample content**, haga clic en **+ Choose sites**.

> <img src="media/image7.png" style="width:6.26806in;height:3.39236in" alt="A screenshot of a computer AI-generated content may be incorrect." />

12. En el panel **Add SharePoint sites**, seleccione la casilla junto a **Learn**, luego haga clic en **Add**.

> <img src="media/image8.png" style="width:6.26806in;height:3.39375in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. Haga clic en **Next**.

> <img src="media/image9.png" style="width:6.26806in;height:3.44236in" alt="A screenshot of a computer AI-generated content may be incorrect." />

14. Revise la configuración y seleccione **Create trainable classifier**.

> <img src="media/image10.png" style="width:6.26806in;height:3.40347in" />

15. n la página **Your trainable classifier is being trained**, haga clic en **Done**.

> <img src="media/image11.png" style="width:6.26806in;height:3.42292in" alt="A screenshot of a computer AI-generated content may be incorrect." />

Los documentos y archivos en los sitios de **SharePoint** seleccionados ahora están siendo analizados, lo que puede tardar hasta 24 horas.

**Resumen:**

En este laboratorio, ha creado un **trainable classifier** en **Microsoft Purview** llamado **Contoso Company Data**, seleccionando sitios relevantes de **SharePoint** como fuentes de contenido positivo y negativo. Este clasificador analizará los documentos para identificar datos específicos de la empresa, con un tiempo de entrenamiento de hasta 24 horas.
