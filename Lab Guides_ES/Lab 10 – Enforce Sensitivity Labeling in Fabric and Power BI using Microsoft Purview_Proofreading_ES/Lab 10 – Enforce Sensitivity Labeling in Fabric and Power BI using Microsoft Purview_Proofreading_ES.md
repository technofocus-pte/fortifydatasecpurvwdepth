**Laboratorio 10 – Aplicar el etiquetado de *sensitivity labels* en Fabric y Power BI mediante Microsoft Purview**

**Introducción**

En el tenant deben habilitarse las **sensitivity labels** de **Microsoft Purview Information Protection** para Fabric y Power BI (incluido **Power BI Desktop**). Cuando se habilitan las sensitivity labels:

- Los usuarios y grupos de seguridad específicos de la organización pueden aplicar sensitivity labels a su contenido de Fabric. En el servicio de Fabric, esto significa cualquier elemento de Fabric. En Power BI Desktop, significa sus archivos **.pbix**.

- En el servicio, todos los miembros de la organización pueden ver esas etiquetas. En Desktop, solo los miembros de la organización que tengan publicadas dichas etiquetas pueden verlas.

**Objetivo**

- Habilitar y priorizar una directiva manual de *Sensitivity label* en Microsoft Fabric mediante Microsoft Purview.

**Ejercicio 1 – Activar la versión de prueba de Microsoft Fabric y acceder al Purview Hub**

1.  Abra Microsoft Edge y en la barra de direcciones ingrese la siguiente URL para abrir el portal de Fabric:- https://app.fabric.microsoft.com

<img src="media/image1.png" style="width:6.26806in;height:4.21667in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Nota:** En caso de que acceda directamente al portal de Fabric, omita los pasos 2 y 3.

2.  Ingrese sus credenciales del tenant.

<img src="media/image2.png" style="width:6.26806in;height:4.86597in" />

<img src="media/image3.png" style="width:6.26806in;height:4.37778in" />

3.  En el campo de contraseña, ingrese la contraseña del tenant. Luego seleccione **Sign in**.

<img src="media/image4.png" style="width:6.26806in;height:4.27222in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

4.  En el cuadro de diálogo **Welcome to the Fabric view**, seleccione **Cancel**.

<img src="media/image5.png" style="width:6.26806in;height:4.27222in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Seleccione el ícono de perfil en la barra de comandos.

<img src="media/image6.png" style="width:6.26806in;height:4.27222in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  Navegue y seleccione el botón **Free trial**.

<img src="media/image7.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  En la ventana **Activate your 60-day free Fabric trial capacity**, en **Trial capacity region**, asegure que la región **Default – West US 3** esté seleccionada. Luego seleccione **Activate**.

<img src="media/image8.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  En el cuadro de diálogo **Successfully upgraded to a free Microsoft Fabric trial**, seleccione **Got it**.

<img src="media/image9.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  Seleccione el ícono de **Settings** en la barra de comandos.

<img src="media/image10.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. En la sección **Governance and insights**, seleccione el enlace **Microsoft Purview hub (preview)**. Luego, en la página **Microsoft Purview hub (preview)**, navegue y seleccione el mosaico **Information Protection**.

<img src="media/image11.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

<img src="media/image12.png" style="width:6.26806in;height:3.69028in" alt="A screenshot of a computer AI-generated content may be incorrect." />

11. En caso de que aparezca el cuadro de diálogo **Pick an account**, seleccione su ID de tenant.

<img src="media/image13.png" style="width:6.26806in;height:3.78958in" />

12. En el cuadro de diálogo **Welcome to Information Protection in the new Microsoft Purview portal**, seleccione **Get started**.

<img src="media/image14.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Ejercicio 2 – Crear y configurar una política de Sensitivity Label para Fabric y Power BI**

1.  En el **Information Protection** blade, navegue y seleccione el menú desplegable junto a **Policies**.

<img src="media/image15.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  Seleccione **Label publishing policies**. En la página **Label publishing policies**, navegue y seleccione **Publish label**.

<img src="media/image16.png" style="width:6.26806in;height:3.68611in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  En la página **Create policy**, navegue y seleccione el enlace **Choose sensitivity label to publish**.

<img src="media/image17.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  En el panel **Sensitivity label to publish** que aparece en el lado derecho, seleccione la casilla junto a **Confidential** y luego seleccione **Add**.

<img src="media/image18.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Seleccione **Next**.

<img src="media/image19.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  En la página **Assign admin units**, seleccione **Next**.

<img src="media/image20.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  En la página **Publish to users and groups**, asegure que la casilla junto a **Users and groups** esté seleccionada y luego seleccione **Next**.

<img src="media/image21.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  En la página **Policy settings**, seleccione la casilla **Require users to apply a label to their Fabric and Power BI content**. Luego seleccione **Next**.

<img src="media/image22.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

<img src="media/image23.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  En **Default settings for documents – Apply a default label to documents**, seleccione **Next**.

<img src="media/image24.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

10. En **Default settings for documents – Apply a default label to emails**, seleccione **Next**.

<img src="media/image25.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

11. En **Default settings for meetings and calendar events**, seleccione **Next**.

<img src="media/image26.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

12. En **Default settings for Fabric and Power BI content**, seleccione **Next**.

<img src="media/image27.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. En la página **Name your policy**, en el campo **Name**, ingrese: Manual Labeling – HR Confidential Docs. Luego seleccione **Next**.

<img src="media/image28.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

14. En la página **Review and finish**, seleccione **Submit**.

<img src="media/image29.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

15. La política se crea correctamente. Seleccione **Done**.

<img src="media/image30.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

16. En la página **Label policies**, verifique que la política **Manual Labeling – HR Confidential Docs** se ha creado correctamente.

<img src="media/image31.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. Seleccione **Manual Labeling – HR Confidential Docs**, luego seleccione el menú de puntos suspensivos horizontales (**…**) y elija **Move up** para cambiar la prioridad.

<img src="media/image32.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

<img src="media/image33.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

18. Nuevamente seleccione **Manual Labeling – HR Confidential Docs**, seleccione el menú de puntos suspensivos horizontales y elija **Move up**.

<img src="media/image34.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

19. Verifique que la prioridad de **Manual Labeling – HR Confidential Docs** se ha actualizado a **1**.

<img src="media/image35.png" style="width:6.26806in;height:3.78958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Resumen**

En este laboratorio, se activó la versión de prueba de Microsoft Fabric, se accedió al portal de Microsoft Purview y se creó una política obligatoria de Sensitivity labels que requiere que los usuarios apliquen la etiqueta **Confidential** al contenido de Fabric y Power BI. Posteriormente, la política fue priorizada para su aplicación.
