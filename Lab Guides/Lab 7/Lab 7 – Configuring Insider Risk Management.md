# Laboratorio 7 – Configuración de Insider Risk Management

## Objetivo:

En este laboratorio aprenderemos a configurar Insider Risk Management
utilizando las políticas de Insider Risk Management. Utilizaremos los
tipos de información confidencial que creamos en el laboratorio 2 y las
políticas de DLP que creamos en el laboratorio 5 para crear políticas
que protegerán a la organización contra el uso arriesgado de navegadores
o cualquier robo o filtración de datos.

Para ello crearemos una infraestructura en Azure que representará los
dispositivos de una organización. Aprenderemos a incorporar esos
dispositivos en Azure AD e Intune, y a instalar un agente MDM en ellos,
de modo que puedan utilizarse para obtener alertas de esas máquinas.

## Ejercicio 1: Sincronizar el reloj de la máquina virtual

1.  Después de iniciar sesión en la máquina virtual, seleccione el icono
    de Windows. A continunación, busque **Date and time**, y seleccione
    **Date and time settings**.

![A screenshot of a computer Description automatically
generated](./media/image1.jpg)

Una captura de pantalla de la descripción de un ordenador generada
automáticamente

2.  En la pantalla de Settings que se abre, haga clic en  **Sync
    now** en Additional settings.

![A screenshot of a computer Description automatically
generated](./media/image2.jpg)

Una captura de pantalla de la descripción de un ordenador generada
automáticamente

3.  Esto se encarga de sincronizar la hora en caso de que la
    sincronización automática no funcione.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image3.png)

Una captura de pantalla de una descripción informática generada
automáticamente con una confianza media

## Ejercicio 2: Creación de políticas de Insider Risk Management

### Requisitos previos 

#### Paso 1 - Añadir usuarios al grupo de funciones de Insider Risk Management 

1.  Si el portal Microsoft Purview está Abierto, continúe con el paso 2;
    de lo contrario, abra el portal `https://purview.microsoft.com` e
    inicie sesión con las credenciales de **MOD Administrator**.

![](./media/image4.png)

2.  En la navegación seleccione **Settings**, y seleccione **Role
    groups** en **Role groups**, seleccione **Insider Risk Management**.
    A continuación, seleccione **Edit**. En el panel lateral, seleccione
    **Edit** de nuevo.

![](./media/image5.png)

3.  En la página **Edit Members of the role group**, seleccione **Choose
    users**.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

Una captura de pantalla de la descripción de un ordenador generada
automáticamente

4.  Seleccione la casilla situada cerca de **MOD Admin**,
    **Patti**, **Megan** and **Alex**. A continuación, elija **Select**.

![](./media/image7.png)

5.  A continuación, seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

Una captura de pantalla de la descripción de un ordenador generada
automáticamente

6.  Seleccione **Save** para añadir los usuarios al grupo de funciones.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

Una captura de pantalla de la descripción de un ordenador generada
automáticamente

7.  Seleccione **Done** para completer los pasos.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

Una captura de pantalla de la descripción de un ordenador generada
automáticamente

#### Paso 2 – Activación de análisis y perspectivas de riesgos internos

1.  En el portal de Microsoft Purview. Navegue hasta **Settings**, vaya
    a **Insider risk management**. Vaya a **Analytics**, active el botón
    de opción, y haga clic en **Save**.

![](./media/image11.png)

#### Paso 3 - Incorporación de un dispositivo 

En este escenario de implementación, usted incorporará dispositivos que
aún no han sido incorporados y sólo desea detectar actividades de riesgo
interno en dispositivos Windows 10.

Necesitamos registrar nuestro dispositivo/VM en Microsoft Entra ID como
prerrequisito para crear cualquier Insider Risk Policy.

1.  Abra la ventana **Setting** en su máquina virtual.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

Una captura de pantalla de la descripción de un ordenador generada
automáticamente

2.  Vaya a **Accounts** \> **Access work or school**. En la página
    **Access work or school**, haga clic en **Connect**.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

3.  En el prompt **Set up a work or school account**, haga clic
    en **Join this device to Microsoft Entra ID**.

![](./media/image14.png)

4.  En el prompt de inicio de sesión, inicie sesión con las
    credenciales **MOD Administrator** proporcionadas en la pestaña de
    su entorno de laboratorio. 

![A screenshot of a computer Description automatically
generated](./media/image15.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

![Graphical user interface, application, PowerPoint Description
automatically generated](./media/image16.png)

Interfaz gráfica de usuario, aplicación, descripción de PowerPoint
generada automáticamente

5.  Presione **Join** en el prompt **Make sure this is your
    organisation**.

![Graphical user interface, text, application Description automatically
generated](./media/image17.png)

Interfaz gráfica de usuario, texto, descripción de la aplicación
generados automáticamente

6.  Una vez hecho esto, verá una ventana de confirmación **You’re all
    set!**. Haga clic en **Done**.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

7.  Vuelva a ir a **Accounts** \> **Access work or school**. En la
    página **Access work or school**, haga clic en **Connect**.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

8.  En el prompt **Set up a work or school account**, utilice las
    credenciales de administrador MOD para iniciar sesión.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

9.  En la página **Setting up your device**, seleccione **Got it**.

![A screenshot of a computer Description automatically
generated](./media/image20.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

10. Ahora vaya a **windows settings** \> **Accounts** \> **Access work
    or school** \> **Connected to Contoso MDM** \> **Info** \> **Sync**.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

![A screenshot of a computer Description automatically
generated](./media/image22.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

11. Haga clic en el símbolo de ventanas de su VM. Seleccione el
    usuario **Admin** y seleccione **Sign out**.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

12. En la pantalla de usuario, seleccione **Other user**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image24.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente con un nivel de confianza medio

13. Ingrese las credenciales de O365 proporcionadas en la página de
    inicio de su entorno de laboratorio e inicie sesión en la máquina
    virtual como **MOD Administrator**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image25.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente con un nivel de confianza medio

14. Cierre la aplicación de configuración de Windows. Inicie sesión en
    `https://purview.microsoft.com` utilizando su cuenta **MOD
    Administrator** en su máquina virtual de laboratorio.

15. Seleccione **Settings** \> **Device onboarding** \> **Devices**.

![](./media/image26.png)

16. Haga clic en **Turn on Device onboarding**.

![A screenshot of a computer Description automatically
generated](./media/image27.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

17. Desde **Settings** \> **Device onboarding** \> **Onboarding**. Haga
    clic en **Download package**.

![A screenshot of a computer Description automatically
generated](./media/image28.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

18. Haga clic con el botón derecho del mouse en el archive y seleccione
    **Extract all…**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image29.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente con un nivel de confianza medio

![A screenshot of a computer Description automatically
generated](./media/image30.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

19. Una vez hecho esto, abra la carpeta y ejecute el archive con
    derechos de **Administrador**.

![A computer screen with a computer screen Description automatically
generated](./media/image31.png)

Una pantalla de ordenador con una descripción de la pantalla de
ordenador generada automáticamente

20. Haga clic en **More info**.

![Graphical user interface, application Description automatically
generated](./media/image32.png)

Interfaz gráfica de usuario, descripción de la aplicación generada
automáticamente

21. Haga clic en **Run anyway**.

![A screenshot of a computer error Description automatically
generated](./media/image33.png)

Una captura de pantalla de una descripción de error de ordenador
generada automáticamente

22. En el símbolo del sistema, presione **Y** y presione enter para
    confirmar y continuar cuando se le solicite.

![A screenshot of a computer error Description automatically
generated](./media/image34.png)

Una captura de pantalla de una descripción de error de ordenador
generada automáticamente

23. Recibirá un mensaje que indica que el dispositivo se ha incorporado.
    En el símbolo del sistema, **Press any key to continue …**, presione
    cualquier tecla.

24. Una vez que el símbolo del sistema esté cerrado, ábralo en modo
    administrador para ejecutar una prueba de detección y, cuando se le
    indique, copie y ejecute el comando que aparece a continuación. La
    ventana del símbolo del sistema se cerrará automáticamente.

`powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference= 'silentlycontinue';(New-ObjectSystem.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe','C:\test-WDATP-test\invoice.exe');Start-Process 'C:\test-WDATP-test\invoice.exe'`

![Text Description automatically generated](./media/image35.png)

Descripción del texto generada automáticamente

25. Abra **settings** hacienda clic en la configuración en la navegación
    y Elija **Devices Onboarding** \> **Devices**.

**Nota:** Aunque normalmente se tarda unos 60 segundos en habilitar la
incorporación del dispositivo, por favor, espere hasta 30 minutos.

26. Podrá consultar la lista **Devices**. La lista estará vacía hasta
    que incorpore dispositivos. Una vez hecho esto, podrá ver sus
    máquinas virtuales en la lista como el dispositivo incorporado.

### Tarea 1: Crear una política para toda la organización para detectar y puntuar el uso de navegadores de riesgo

#### Paso 1 – Cree una nueva política 

1.  Si cerró la ventana del navegador en la tarea anterior,
    abra `https://purview.microsoft.com` e inicie sesión con las
    credenciales de administrador.

2.  Vaya a **Insider Risk Management** y seleccione la
    pestaña **Policies**. Seleccione **Create policy** para abrir el
    asistente de políticas.

![](./media/image36.png)

3.  En la página **Choose a policy template**, elija **Risky browser
    usage (preview)**, en **Risky browser usage (preview)**.

![A screenshot of a computer Description automatically
generated](./media/image37.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

4.  Asegúrese de que se cumplen todos los requisitos previos.

![A screenshot of a computer Description automatically
generated](./media/image38.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

5.  Seleccione **Next** para continuar.

![A screenshot of a computer Description automatically
generated](./media/image39.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

6.  En la página **Name and description**, complete los siguientes
    campos:

    - Name (requerido): `Risky usage of browser`

    - Description
      (opcional): `This is a test policy for the risky browser usage.`

7.  Seleccione **Next** para continuar.

![Graphical user interface, text, application Description automatically
generated](./media/image40.png)

Interfaz gráfica de usuario, texto, descripción de la aplicación
generados automáticamente

8.  En la página **Choose users, groups, & adaptive scopes**, seleccione
    **All users, groups, & adaptive scopes**. Seleccione **Next** para
    continuar

9.  En la página **Exclude users and groups**, seleccione **Next**.

10. En la página **Decide whether to prioritize**, seleccione **I don’t
    want to specify priority content right now** (podrá hacerlo después
    de cerear la política). Seleccione **Next** para continuar.

![Graphical user interface, text, application Description automatically
generated](./media/image41.png)

Interfaz gráfica de usuario, texto, descripción de la aplicación
generados automáticamente

11. En la página **Triggers for this policy**, seleccione **Turn on
    indicators**.

![A screenshot of a computer Description automatically
generated](./media/image42.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

12. En **Choose indicators to turn on**, seleccione **Select
    all under Risky browsing indicators (preview)**, y desmarque el
    resto de las casillas.

![A screenshot of a computer Description automatically
generated](./media/image43.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

13. Desplácese hacia abajo y seleccione **Save**.

14. En **Triggers for this policy**, en **Select which activities will
    trigger this policy**. Seleccione todas las opciones y haga clic en
    **Next**.

![Graphical user interface, text, application Description automatically
generated](./media/image44.png)

Interfaz gráfica de usuario, texto, descripción de la aplicación
generada automáticamente

15. En la página **Triggering thresholds for this policy**,
    seleccione **Use custom thresholds (Recomendado)**, cambie todos los
    umbrales a 1 por día y luego seleccione **Next**.

![Graphical user interface, application Description automatically
generated](./media/image45.png)

Interfaz gráfica de usuario, descripción de la aplicación generada
automáticamente

![A screenshot of a computer Description automatically
generated](./media/image46.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

16. En la página **indicators**, seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image47.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

17. En **Decide whether to use default or custom indicator thresholds**,
    seleccione **Use default thresholds for all indicators**, y después
    seleccione **Next**.

![Graphical user interface, text, application Description automatically
generated](./media/image48.png)

Interfaz gráfica de usuario, texto, descripción de la aplicación
generada

automáticamente

18. En **Review settings and finish**, seleccione **Submit**.

![Graphical user interface, text, application Description automatically
generated](./media/image49.png)

Interfaz gráfica de usuario, texto, descripción de la aplicación
generada

automáticamente

19. En **Your policy was created**, seleccione **Done**.

![A screenshot of a computer Description automatically
generated](./media/image50.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

20. Mantenga la pestaña abierta y continúe con la siguiente tarea.

#### Paso 2 – Puntúe la política 

1.  Haga clic en la nueva política llamada **Risky usage of browser**.
    Seleccione **Start scoring activity for users**.

![A screenshot of a computer Description automatically
generated](./media/image51.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

2.  En el campo **Reason** del panel **Add users to multiple policies**,
    escriba **Testing the policy**.

![A screenshot of a computer Description automatically
generated](./media/image52.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

3.  En el campo **This should last for (choose between 5 and 30 days)**,
    seleccione **10 days**.

4.  Utilice el campo **Search user to add to policies**. Añada **MOD
    Admin**. A continuación, haga clic en **Start scoring activity**.

5.  Una vez que reciba la confirmación de que ha iniciado **Scoring
    activity for 3 users**, haga clic en **Close**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image53.png)

Una captura de pantalla de una descripción de pantalla de ordenador
generada automáticamente con un nivel de confianza medio

### Tarea 2: Robo de datos por parte de usuarios que salen de la empresa

#### Paso – Cree una nueva política 

1.  Si cerró la ventana del navegador en la tarea anterior, abra
    <https://purview.microsoft.com> e inicie sesión con las credenciales
    de administrador.

2.  Vaya a **Insider Risk Management** y seleccione la pestaña
    **Policies**. Seleccione **Create policy** para abrir el asistente
    de políticas.

![](./media/image36.png)

3.  En la página Choose a policy template, elija Data theft by departing
    users, debajo de Data theft. Seleccione Next para continuar.

![A screenshot of a computer Description automatically
generated](./media/image54.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

4.  En la página **Name and description**, complete los siguientes
    campos:

    - Name (requerido): `Data theft by a user`

    - Description
      (opcional): `This is a test policy for the preventing data theft.`

5.  Seleccione **Next** para continuar.

![A screenshot of a computer Description automatically
generated](./media/image55.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

6.  En la página **Choose users, groups, & adaptive scopes**,
    seleccione **All users, groups, & adaptive scopes**.
    Seleccione **Next** para continuar.

7.  En la página **Exclude users, groups, & adaptive scopes**,
    seleccione **Next**.

8.  En la página **Decide whether to prioritize**, seleccione **I want
    to specify priority content**. Seleccione la casilla de verificación
    para **Sensitivity labels** y **Sensitive info types**. Seleccione
    **Next** para continuar.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image56.png)

Una captura de pantalla de una descripción de pantalla de ordenador
generada automáticamente con un nivel de confianza medio

9.  En la página **Sensitivity labels to prioritize**, seleccione **Add
    or edit sensitivity labels**. En el desplegable,
    seleccione **Internal/Employee data (HR)** y seleccione **Add**.
    Haga clic en **Next**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image57.png)

Una captura de pantalla de una descripción de pantalla de ordenador
generada automáticamente con un nivel de confianza medio

10. En la página **Sensitive info types to prioritize**,
    seleccione **Add or edit sensitive info types**. En el panel
    desplegable, busque y seleccione **Credit Card Number**, **Contoso
    Employee ID** y **Contoso Employee EDM**. Seleccione **Add**. Luego
    haga clic en **Next**.

![A screenshot of a computer Description automatically
generated](./media/image58.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

11. En **Decide whether to score only activity with priority content**,
    seleccione **Get alerts for all activity**. Seleccione **Next**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image59.png)

Una captura de pantalla de una descripción de pantalla de ordenador
generada automáticamente con un nivel de confianza medio

12. En la página triggers for this policy, seleccione el valor
    predeterminado y luego seleccione Next.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image60.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente con un nivel de confianza medio

13. En la página **Indicators**, seleccione **Turn on indicators** en el
    prompt.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image61.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente con un nivel de confianza medio

14. Seleccione **Select all under Office indicators** y haga clic
    en **Save**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image62.png)

Una captura de pantalla de una descripción de pantalla de ordenador
generada automáticamente con un nivel de confianza medio

15. Seleccione todas las opciones y haga clic en **Next**.

![A screenshot of a computer Description automatically
generated](./media/image63.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

16. En la página **Detection options**, selecione el valor
    predeterminado y después seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image64.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

17. En la página **indicators**, seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image47.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

18. En **Decide whether to use default or custom indicator thresholds**,
    seleccione **Customise thresholds**, utilice **1**, **2**, y **3**
    eventos para cada etapa respectivamente y luego seleccione Next.

![A screenshot of a computer screen Description automatically
generated](./media/image65.png)

Una captura de pantalla de una descripción de pantalla de ordenador
generada automáticamente

19. En **Review settings and finish**, seleccione **Submit**.

![A screenshot of a computer Description automatically
generated](./media/image66.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

20. En **Your policy was created**, seleccione **Done**.

![A screenshot of a computer Description automatically
generated](./media/image67.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

21. Mantenga la pestaña abierta y continúe con la siguiente tarea.

#### Paso 2 – Puntúe la política

1.  Haga clic en la nueva política denominada **Data theft by a user**.
    Seleccione **Start scoring activity for users**.

![A screenshot of a computer Description automatically
generated](./media/image68.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

2.  En el campo **Reason field in the Add users to multiple policies**,
    escriba **Testing the policy**.

![A screenshot of a computer Description automatically
generated](./media/image52.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

3.  En el campo **This should last for (choose between 5 and 30 days)**,
    seleccione **10** días.

4.  Utilice el campo **Search user to add to policies**. Añada **MOD
    Admin**. Después haga clic en **Start scoring activity**.

5.  Una vez que reciba la confirmación de que ha iniciado **Scoring
    activity for 1 user**, haga clic en **Close**.

![A screenshot of a computer Description automatically
generated](./media/image69.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

### Tarea 3: Filtración de datos por los usuarios 

#### Paso 1 – Cree una nueva política

1.  Si cerró la ventana del navegador en la tarea anterior, abra
    `https://purview.microsoft.com` e inicie sesión con las credenciales
    de administrador.

2.  Vaya a **Insider Risk Management** y seleccione la
    pestaña **Policies**. Seleccione **Create policy** para abrir el
    asistente de políticas.

![A screenshot of a computer Description automatically
generated](./media/image36.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

3.  En la página **Choose a policy template**, elija **Data leaks**, en
    **Data leaks**. Seleccione **Next** para continuar.

![A screenshot of a computer Description automatically
generated](./media/image70.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

4.  En la página **Name and description**, complete los siguientes
    campos:

    - Name (requerido): `Data leaks by a user`

    - Description
      (opcional): `This is a test policy for preventing data leaks.`

5.  Seleccione **Next** para continuar.

![A screenshot of a computer Description automatically
generated](./media/image71.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

6.  En la página **Choose users and groups**, seleccione **Include all
    users and groups**. Seleccione **Next** para continuar.

![A screenshot of a computer Description automatically
generated](./media/image72.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

7.  En la página **Exclude users and groups**, seleccione **Next**.

8.  En la página **Decide whether to prioritize**, seleccione **I want
    to specify priority content**. Seleccione la casilla de
    verificación **SharePoint sites**, **Sensitivity labels** y
    **Sensitive info types**. Seleccione **Next** para continuar.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image73.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente con un nivel de confianza medio

9.  En la página **SharePoint sites to prioritize**, seleccione **Add or
    edit SharePoint sites**. En el panel desplegable,
    seleccione `https://{TENANTPREFIX``}.sharepoint.com``/sites/ContosoWeb1`
    y seleccione **Add**. A continuación, haga clic en **Next**.

10. En la página **Sensitivity labels to prioritize**, seleccione **Add
    or edit sensitivity labels**. En el panel desplegable,
    seleccione **Internal/Employee data (HR)** y seleccione **Add**. A
    continuación, haga clic en **Next**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image57.png)

Una captura de pantalla de una descripción de pantalla de ordenador
generada automáticamente con una confianza media

11. En la página **Sensitive info types to prioritize**,
    seleccione **Add or edit sensitive info types**. En el panel
    desplegable, busque y seleccione **Credit Card Number**, **Contoso
    Employee ID** y **Contoso Employee EDM**. Seleccione **Add**. A
    continuación, haga clic en **Next**.

![A screenshot of a computer Description automatically
generated](./media/image58.png)

Una captura de pantalla de la descripción de un ordenador generada
automáticamente

12. En **Decide whether to score only activity with priority content**,
    seleccione **Get alerts for all activity**. Seleccione **Next**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image59.png)

Una captura de pantalla de una descripción de pantalla de ordenador
generada automáticamente con una confianza media

13. En la página **Triggers for this policy**, seleccione el botón de
    radio cerca de **User performs an exfiltration activity**. En select
    which activities will trigger this policy, seleccione todas las
    opciones disponibles especialmente **Download content from
    SharePoint**. y luego seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image74.png)

Una captura de pantalla de la descripción de un ordenador generada
automáticamente

14. En **Triggering thresholds for this policy**, seleccione **Use
    custom thresholds**. Fije cada umbral en **1** y
    seleccione **Next**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image75.png)

Una captura de pantalla de una descripción informática generada
automáticamente con una confianza media

15. Seleccione la configuración por defecto en la página
    **Indicators** y seleccione **Next**.

16. En **Decide whether to use default or custom indicator thresholds**,
    seleccione **Customise thresholds**, utilice **1**, **2**, y **3**
    eventos para cada etapa respectivamente y luego seleccione **Next**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image76.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente con un nivel de confianza medio

17. En **Review settings and finish**, seleccione **Submit**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image77.png)

Una captura de pantalla de una descripción informática generada
automáticamente con una confianza media

18. En **Your policy was created**, seleccione **Done**.

![A screenshot of a computer Description automatically
generated](./media/image78.png)

Una captura de pantalla de la descripción de un ordenador generada
automáticamente

19. Mantenga la pestaña abierta y continúe con la siguiente tarea.

#### Paso 2 – Puntúe la política

1.  Haga clic en la nueva política denominada **Data leaks by a user**.
    Seleccione **Start scoring activity for users**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image79.png)

Una captura de pantalla de una descripción informática generada
automáticamente con una confianza media

2.  En el panel **Reason field in the Add users to multiple policies**,
    escriba Testing the policy. En el campo **This should last for
    (choose between 5 and 30 days)**, seleccione **10** días. Utilice el
    campo **Search user to add to policies**. Añada **MOD Admin**. A
    continuación, haga clic en **Start scoring activity**.

3.  Una vez que obtenga la confirmación de ha iniciado **Scoring
    activity for 1 user**, haga clic en **Close**.

Ha creado correctamente las políticas de Insider Risk Management.

## Resumen:

En este laboratorio exploramos la configuración de Insider Risk
Management de principio a fin. Con su propia suscripción y licencias,
también puede utilizar esta guía de laboratorio para crear una
configuración de Azure que también se puede utilizar para crear varias
alertas (que incluye el envío de correos electrónicos con datos
restringidos, lo que no es posible desde una suscripción de prueba) para
las políticas de Insider Risk Management que puede utilizar para
explorar la característica Adaptive Protection en Purview.
