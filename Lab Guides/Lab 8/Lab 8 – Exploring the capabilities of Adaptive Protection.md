# Laboratorio 8 – Exploración de las características de Adaptive Protection

## Ejercicio 1 – Configuración de Adaptive Protection

### Tarea 1 – Establecer niveles de riesgo para Adaptive Protection

1.  En Microsoft Edge, abra una nueva ventana InPrivate, navegue
    a `https://purview.microsoft.com` e inicie sesión con el tenant de
    administrador.

2.  Desde la barra de navegación, vaya a **Solutions** \> **Insider
    risk** **management**.

![](./media/image1.png)

3.  Desde la subnavegación, seleccione **Adaptive Protection
    (Preview)**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

4.  Dado que utilizamos la opción de inicio rápido al
    habilitar **Adaptive Protection**, podemos ver 2 políticas de DLP
    creadas.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

5.  Ahora haga clic en **Risk levels for Adaptive Protection** en el
    submenú y seleccione **Data leaks by a user** en el menú
    desplegable.

![BrokenImage](./media/image4.png)



6.  En **Define conditions for risk levels**, seleccione **User performs
    at least 3 data exfiltration activities,
    each…** para **Elevated** risk. Seleccione **User performs at least
    2 data exfiltration activities, each…** para **Moderate** risk.
    **Select User performs at least 1 data exfiltration activities,
    each…** para **Minor** risk. Después haga clic en **Save**.

![BrokenImage](./media/image5.png)



7.  De igual manera, puede personalizar las condiciones de todas las
    pólizas disponibles en Insider Risk Management.

8.  Ahora podemos personalizar la política de DLP para cada nivel.

### Tarea 2 – Explorar las políticas de DLP predeterminadas para cada uno de los niveles de riesgo de

Adaptive Protection

1.  En Adaptive Protection, seleccione DLP Policies y seleccione
    Adaptive Protection Policy for Endpoint DLP.

![BrokenImage](./media/image6.png)



2.  Seleccione **Edit**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image7.png)

Una captura de pantalla de una descripción de pantalla de ordenador
generada automáticamente con un nivel de confianza medio

3.  Haga clic en Next till hasta llegar a **Customize advanced DLP
    rules**.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

4.  Compruebe las reglas y condiciones establecidas para cada nivel de
    riesgo. Haga clic en **Next**.

5.  En la página **Policy mode**, seleccione el botón junto a **Turn it
    on right away**. Haga clic en **Next**.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

6.  Seleccione **Submit**.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

7.  Repita los pasos para habilitar la política Adaptive Protection
    Policy para Teams y Exchange DLP.

8.  Por ahora no vamos a crear ninguna regla o política, pero puede
    explorar varias opciones disponibles después de completar el
    laboratorio.
