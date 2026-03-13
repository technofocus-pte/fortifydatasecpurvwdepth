**Laboratorio 7 – Configurar Insider Risk Management**

**Introducción**

En este laboratorio, se aprenderá cómo configurar **Insider Risk Management** mediante las Insider Risk Management Policies. Se usarán los Sensitive Info Types creados en el Lab 1 y las DLP policies creadas en el Lab 4 para crear policies que protegerán a la organización contra el uso riesgoso del navegador o cualquier robo o filtración de datos.

Para lograrlo, se creará una infraestructura en Azure que representará los dispositivos de una organización. Se aprenderá cómo incorporar esos dispositivos en Azure AD e Intune, e instalar un MDM agent en ellos, de modo que puedan utilizarse para obtener alertas desde esas máquinas.

**Objetivos**

- Sincronizar los relojes de las máquinas virtuales para garantizar configuraciones de hora precisas durante las pruebas de las policies.

- Asignar usuarios al Insider Risk Management role group en Microsoft Purview.

- Habilitar analytics insights para la detección de riesgos internos a nivel de tenant y de usuario.

- Incorporar dispositivos Windows 10 a Microsoft Defender for Endpoint para monitoreo de riesgos internos.

- Crear y configurar Insider Risk Management policies para:\
  o Uso riesgoso del navegador\
  o Robo de datos por usuarios que están por abandonar la organización\
  o Filtraciones de datos por parte de usuarios

- Ponderar cada policy para simular escenarios de detección de riesgos internos para la cuenta MOD administrator..

**Ejercicio 1 – Configurar el entorno**

**Tarea 0 – Sincronizar el reloj de la máquina virtual**

1.  Cierre todas las pestañas del navegador **Microsoft Edge** que estén abiertas en su máquina virtual. Haga clic en el ícono de Windows y luego haga clic en **Settings**, como se muestra en la imagen.

> <img src="media/image1.png" style="width:6.26806in;height:5.35972in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  En la barra de búsqueda de **Windows Settings**, escriba **Date & time settings** y seleccione **Date & time settings** de la lista.

> <img src="media/image2.png" style="width:6.26806in;height:3.45417in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  En la página **Date & time**, navegue y haga clic en el botón **Sync now**.

> <img src="media/image3.png" style="width:6.26806in;height:3.39167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Ejercicio 2 – Crear políticas de Insider Risk Management**

**Requisitos previos**

**Paso 1 – Agregar usuarios al grupo de roles de Insider Risk Management**

1.  Abra el portal de **Microsoft Purview**: <https://purview.microsoft.com> e inicie sesión con las credenciales de **MOD Administrator**.

2.  En el menú de navegación izquierdo, haga clic en **Settings.**

> <img src="media/image4.png" style="width:6.26806in;height:3.43472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  En el panel **Settings**, navegue y haga clic en **Roles and scopes**. Haga clic en **Role groups**, luego seleccione la casilla junto a **Insider Risk Management** y haga clic en el ícono del lápiz para **Edit**.

> <img src="media/image5.png" style="width:6.26806in;height:4.52153in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image6.png" style="width:6.26806in;height:3.97361in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  En la página **Edit Members of the role group**, haga clic en **Choose users**.

> <img src="media/image7.png" style="width:6.26806in;height:3.48125in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Seleccione la casilla junto a **Alex Wilber**. Luego, haga clic en **Select**.\
    *En caso de que Alex Wilber ya esté seleccionado, ignore este paso*.

> **Nota:** Si no ve los nombres Megan Bowen y MOD Administrator en la lista de miembros para editar, además de Alex, seleccione también Megan Bowen y MOD Administrator.
>
> <img src="media/image8.png" style="width:6.26806in;height:3.49722in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  Asegúrese de que los nombres **MOD Administrator**, **Megan Bowen** y **Alex Wilber** estén visibles, luego haga clic en **Next**.

> <img src="media/image9.png" style="width:6.26806in;height:3.46597in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  Seleccione **Save** para agregar los usuarios al grupo de roles.

> <img src="media/image10.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer Description automatically generated" />

8.  Seleccione **Done** para completar los pasos.

> <img src="media/image11.png" style="width:6.26806in;height:3.53472in" alt="A screenshot of a computer Description automatically generated" />

**Paso 2 – Habilitar análisis de información para Insider Risk**

1.  En el portal de **Microsoft Purview**, navegue a **Settings**, luego desplácese hacia abajo y haga clic en **Insider risk management**.\
    En la página **Insider Risk Management settings – Analytics**, active los interruptores **Show insights at tenant level** y **Show insights at user level**. Luego haga clic en **Save**.

> <img src="media/image12.png" style="width:6.26806in;height:3.46944in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Paso 3 – Incorporar un dispositivo**

En este escenario de implementación, se incorporarán dispositivos que aún no han sido incorporados y únicamente se desea detectar actividades de riesgo interno en dispositivos Windows 10.\
\
Es necesario registrar el dispositivo/VM en Microsoft Entra ID como requisito previo para crear cualquier Insider Risk Policy.

1.  Haga clic en el ícono de **Windows**, luego seleccione **Settings**.

> <img src="media/image13.png" style="width:6.26806in;height:3.93403in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  Vaya a **Accounts \> Access work or school**. En la página **Access work or school**, haga clic en **Connect**.

> <img src="media/image14.png" style="width:6.26806in;height:3.75556in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image15.png" style="width:6.26806in;height:4.93542in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  En el mensaje **Set up a work or school account**, haga clic en **Join this device to Microsoft Entra ID**.

> <img src="media/image16.png" style="width:6.26806in;height:4.09514in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  En la ventana de inicio de sesión, inicie sesión con las credenciales de **MOD Administrator** proporcionadas en la pestaña **Resources** de su entorno de laboratorio.

> <img src="media/image17.png" style="width:6.26806in;height:5.95625in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image18.png" style="width:6.26806in;height:6.00347in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  En el mensaje **Make sure this is your organisation**, haga clic en **Join**.

> <img src="media/image19.png" style="width:6.26806in;height:3.65764in" alt="A screenshot of a computer error AI-generated content may be incorrect." />

6.  Una vez completado, aparecerá la ventana de confirmación **You're all set!**. Haga clic en **Done**.

> <img src="media/image20.png" style="width:6.26806in;height:5.82153in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  Nuevamente, en la página **Access work or school**, haga clic en **Connect**.

> <img src="media/image21.png" style="width:6.26806in;height:4.59444in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  En el mensaje **Set up a work or school account**, inicie sesión usando las credenciales de **MOD Administrator**.

> <img src="media/image22.png" style="width:6.26806in;height:5.86042in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image23.png" style="width:6.26806in;height:5.7in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  En el mensaje **Stay signed in?**, haga clic en **Yes**.

> <img src="media/image24.png" style="width:6.26806in;height:4.925in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. Si aparece el mensaje **Setting up your device**, seleccione **Got it**.

> <img src="media/image25.png" style="width:6.26806in;height:3.51458in" alt="A screenshot of a computer Description automatically generated" />

11. Ahora vaya a **Windows Settings \> Accounts \> Access work or school \> Connected to Contoso MDM \> Info \> Sync**.

> <img src="media/image26.png" style="width:6.26806in;height:4.30486in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image27.png" style="width:6.26806in;height:5.60347in" alt="A screenshot of a computer AI-generated content may be incorrect." />

12. Haga clic en el ícono de Windows en su VM. Seleccione el usuario **Admin** y haga clic en **Sign out**.

> <img src="media/image28.png" style="width:6.26806in;height:6.05972in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. En la pantalla de usuarios, seleccione **Other user**.

> <img src="media/image29.png" style="width:6.26806in;height:3.78403in" alt="A screenshot of a computer Description automatically generated with medium confidence" />

14. Ingrese las credenciales de **O365** mostradas en la página de inicio del laboratorio e inicie sesión como **MOD Administrator**.

> <img src="media/image30.png" style="width:6.26806in;height:4.95556in" alt="A screenshot of a login screen AI-generated content may be incorrect." />

15. Inicie sesión en <https://purview.microsoft.com> usando su cuenta **MOD Administrator** en la VM del laboratorio.

16. En el portal de Microsoft Purview, navegue y seleccione **Settings \> Device onboarding \> Devices**. Haga clic en **Turn on Device onboarding**.

<img src="media/image31.png" style="width:6.26806in;height:3.31875in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. En el cuadro de diálogo **Turn on device onboarding**, haga clic en **OK**.

> <img src="media/image32.png" style="width:6.26806in;height:4.00069in" alt="A screenshot of a computer AI-generated content may be incorrect." />

18. En el cuadro de diálogo **Device monitoring is being turned on**, haga clic en **OK**.

> <img src="media/image33.png" style="width:6.26806in;height:3.74375in" alt="A screenshot of a computer AI-generated content may be incorrect." />

19. Espere unos minutos y luego actualice la página.

> <img src="media/image34.png" style="width:6.26806in;height:3.84583in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image35.png" style="width:6.26806in;height:3.65347in" alt="A screenshot of a computer AI-generated content may be incorrect." />

20. Desde **Settings \> Device onboarding \> Onboarding**, haga clic en **Download package**.

> <img src="media/image36.png" style="width:6.26806in;height:3.39028in" alt="A screenshot of a computer AI-generated content may be incorrect." />

21. Una vez descargado, copie el archivo al escritorio. Haga clic derecho sobre el archivo y seleccione **Extract all…**, luego haga clic en **Extract**.

> <img src="media/image37.png" style="width:6.26806in;height:4.69514in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image38.png" style="width:6.26806in;height:5.37778in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image39.png" style="width:6.26806in;height:4.61944in" alt="A screenshot of a computer AI-generated content may be incorrect." />

22. Una vez extraído, abra la carpeta y ejecute el archivo **con derechos de administrador**.

> <img src="media/image40.png" style="width:6.26806in;height:3.92083in" alt="A computer screen with a computer screen Description automatically generated" />

23. Si aparece el mensaje **Search for app in the Store?**, haga clic en **Yes**; si no aparece, ignore.

24. En el mensaje **The publisher could not be verified. Are you sure you want to run this software?**, haga clic en **Run**.

> <img src="media/image41.png" style="width:6.26806in;height:4.48889in" alt="A screenshot of a computer AI-generated content may be incorrect." />

25. Si aparece el mensaje **User Account Control**, haga clic en **Yes**.

> <img src="media/image42.png" style="width:6.26806in;height:4.31181in" alt="A screenshot of a computer error AI-generated content may be incorrect." />

26. En la ventana de **Command Prompt**, presione **Y** y luego presione **Enter** para confirmar.\
    Aparecerá un mensaje indicando que el dispositivo está incorporado.\
    Cuando vea el mensaje **Press any key to continue...**, presione cualquier tecla.

> <img src="media/image43.png" style="width:6.26806in;height:2.29861in" alt="A screenshot of a computer error Description automatically generated" />

27. Después de cerrarse la ventana, abra **Command Prompt** como administrador: escriba *cmd* en la búsqueda de Windows, haga clic derecho en **Command Prompt** y seleccione **Run as administrator**.

> <img src="media/image44.png" style="width:6.26806in;height:5.90208in" alt="A screenshot of a computer AI-generated content may be incorrect." />

28. En el mensaje **User Account Control**, haga clic en **Yes**.

> <img src="media/image42.png" style="width:6.26806in;height:4.31181in" alt="A screenshot of a computer error AI-generated content may be incorrect." />

29. Ejecute la prueba de detección ingresando el siguiente comando (la ventana se cerrará automáticamente):

> powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden \$ErrorActionPreference= 'silentlycontinue';(New-ObjectSystem.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe','C:\test-WDATP-test\invoice.exe');Start-Process 'C:\test-WDATP-test\invoice.exe'
>
> <img src="media/image45.png" style="width:6.26806in;height:3.30625in" alt="Text Description automatically generated" />

30. Cierre la conexión de la máquina virtual.

31. Abra **Settings** en el portal y seleccione **Devices Onboarding \> Devices**.

> **Nota:** Aunque usualmente toma 60 segundos habilitar el onboarding, puede tardar hasta 30 minutos.

32. Será posible verificar la lista **Devices**. La lista permanecerá vacía hasta que se incorporen los dispositivos; una vez completado el proceso, será posible ver las máquinas virtuales en la lista como dispositivos incorporados.

**Tarea 1 – Crear una directiva para toda la organización para detectar y puntuar el uso riesgoso del navegador**

**Paso 1 – Crear una nueva directiva**

1.  En el portal de **Microsoft Purview**, seleccione **Solutions**, luego seleccione **Insider Risk Management**.

> <img src="media/image46.png" style="width:6.26806in;height:3.48403in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  Seleccione **Policies**. En la página **Policies**, seleccione **+Create policy \> Custom policy**.

> <img src="media/image47.png" style="width:6.26806in;height:3.46319in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  En la página **Choose a policy template**, seleccione **Risky browser usage (preview)**, bajo **Risky browser usage (preview)**.

> <img src="media/image48.png" style="width:6.26806in;height:3.92083in" alt="A screenshot of a computer Description automatically generated" />

4.  Revise todos los requisitos previos.

> <img src="media/image49.png" style="width:6.26806in;height:3.92083in" alt="A screenshot of a computer Description automatically generated" />

5.  Seleccione **Next** para continuar.

> <img src="media/image50.png" style="width:6.26806in;height:3.92083in" alt="A screenshot of a computer Description automatically generated" />

6.  En la página **Name and description**, complete los siguientes campos:

    - Name: Risky usage of browser

    - Description: This is a test policy for the risky browser usage

7.  Seleccione **Next** para continuar.

> <img src="media/image51.png" style="width:6.26806in;height:3.92083in" alt="Graphical user interface, text, application Description automatically generated" />

8.  En la página **Choose users, groups, & adaptive scopes**, seleccione **All users, groups, & adaptive scopes**. Seleccione **Next** para continuar.

> <img src="media/image52.png" style="width:6.26806in;height:3.6125in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  En la página **Exclude users and groups**, seleccione **Next**.

> <img src="media/image53.png" style="width:6.26806in;height:3.45625in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. En la página **Decide whether to prioritize**, seleccione **I don't want to priority content right now**. Luego, seleccione **Next** para continuar.

> <img src="media/image54.png" style="width:6.26806in;height:3.49514in" alt="A screenshot of a computer AI-generated content may be incorrect." />

11. En la página **Choose triggering event for this policy**, seleccione el botón **Turn on indicators**.

> <img src="media/image55.png" style="width:6.26806in;height:3.45069in" alt="A screenshot of a computer Description automatically generated" />

12. En el cuadro de diálogo **Turn on indicators for your organization**, desplácese hacia abajo y seleccione **Choose indicators to turn on**.

> <img src="media/image56.png" style="width:6.26806in;height:3.94097in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image57.png" style="width:6.26806in;height:3.9875in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. En el cuadro de diálogo **Choose indicators to turn on**, asegúrese de que, bajo **Risky browsing indicators (preview)**, todos los indicadores estén seleccionados.

> <img src="media/image58.png" style="width:6.26806in;height:4.00833in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image59.png" style="width:6.26806in;height:3.73472in" alt="A screenshot of a computer Description automatically generated" />

14. Desplácese hacia abajo y seleccione **Save**.

15. En la página **Choose triggering event for this policy**, asegúrese de que esté seleccionada la opción **User browsed to a potentially risky website**. Bajo **Select which activities will trigger this policy**, seleccione todas las opciones y luego seleccione **Next**.

> <img src="media/image60.png" style="width:6.26806in;height:3.92083in" alt="Graphical user interface, text, application Description automatically generated" />

16. En la página **Choose thresholds for triggering events**, seleccione la opción **Choose your own thresholds**, cambie todos los umbrales a **1 per day** y luego seleccione **Next.**

> <img src="media/image61.png" style="width:6.26806in;height:3.47153in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image62.png" style="width:6.26806in;height:4.12708in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. En la página **Indicators**, seleccione **Next**.

> <img src="media/image63.png" style="width:6.26806in;height:3.92083in" alt="A screenshot of a computer Description automatically generated" />

18. En la página **Choose threshold type for indicators**, asegúrese de que esté seleccionada **Apply thresholds provided by Microsoft**, luego seleccione **Next**.

> <img src="media/image64.png" style="width:6.26806in;height:3.44792in" alt="A screenshot of a computer AI-generated content may be incorrect." />

19. En la página **Review settings and finish**, seleccione **Submit**.

> <img src="media/image65.png" style="width:6.26806in;height:3.44514in" alt="A screenshot of a computer AI-generated content may be incorrect." />

20. En la página **Your policy was created**, seleccione **Done**.

> <img src="media/image66.png" style="width:6.26806in;height:3.4375in" alt="A screenshot of a computer AI-generated content may be incorrect." />

21. Mantenga la pestaña abierta y continúe con la siguiente tarea.

**Paso 2 – Puntuar la directiva**

1.  Seleccione la nueva directiva denominada **Risky usage of browser**. Seleccione **Start scoring activity for users**.

> <img src="media/image67.png" style="width:6.26806in;height:3.50417in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  En el campo **Reason for scoring activity**, ingrese *Testing the policy*. En el campo **Scoring activity for this many days (between 5 and 30)**, seleccione *10 days*.

> <img src="media/image68.png" style="width:6.26806in;height:3.45625in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  En el campo **Score activity for these users**, escriba **MOD** y seleccione **MOD administrator**.

> <img src="media/image69.png" style="width:6.26806in;height:3.45833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  Seleccione **Start scoring activity**.

> <img src="media/image70.png" style="width:6.26806in;height:3.46389in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Seleccione **Close**.

> <img src="media/image71.png" style="width:6.26806in;height:3.46528in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Tarea 2 – Robo de datos por usuarios que están por salir**

**Paso 1 – Crear una nueva directiva**

1.  En la página **Policies**, seleccione **+ Create policy** y luego **Custom policy**.

> <img src="media/image72.png" style="width:6.26806in;height:3.46181in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  En la página **Choose a policy template**, seleccione **Data theft by departing users** en la sección *Data theft*. Seleccione **Next**.

> <img src="media/image73.png" style="width:6.26806in;height:3.73472in" alt="A screenshot of a computer Description automatically generated" />

3.  En la página **Name and description**, complete los siguientes campos:

    - Name: Data theft by a user

    - Description: This is a test policy for preventing data theft

4.  Seleccione **Next**.

> <img src="media/image74.png" style="width:6.26806in;height:3.73472in" alt="A screenshot of a computer Description automatically generated" />

5.  En **Choose users, groups, & adaptive scopes**, seleccione \*\***All users, groups, and adaptive scopes\*\***, luego seleccione **Next**.

\![A screenshot of a computer Description automaticall generated\](./media/uu1.png)

6.  En **Exclude users and groups (optional)**, seleccione **Next**.

\![A screenshot of a computer Description automaticall generated\](./media/uu2.png)

6.  En **Decide whether to prioritize content**, seleccione **I want to prioritize content**. Seleccione únicamente las casillas **Sensitivity labels** y **Sensitive info types**. Seleccione **Next**.

> <img src="media/image75.png" style="width:6.26806in;height:3.73472in" alt="A screenshot of a computer screen Description automatically generated with medium confidence" />

7.  En **Sensitivity labels to prioritize**, seleccione **Add or edit sensitivity labels**. En el buscador, escriba *employee* y presione **Enter**. Seleccione **Internal/Employee data (HR)** y luego **Add**. Seleccione **Next**.

> <img src="media/image76.png" style="width:6.26806in;height:3.73472in" alt="A screenshot of a computer screen Description automatically generated with medium confidence" />

8.  En **Sensitive info types to prioritize**, seleccione **Add or edit sensitive info types**. Busque y seleccione **Credit Card Number**, **Contoso Employee ID** y **Contoso Employee EDM**. Seleccione **Add**, luego **Next**.

> <img src="media/image77.png" style="width:6.26806in;height:3.73472in" alt="A screenshot of a computer Description automaticall generated" />

9.  En **Decide whether to score only activity with priority content**, asegúrese de que **Get alerts for all activity** esté seleccionado. Seleccione **Next**.

> <img src="media/image78.png" style="width:6.26806in;height:3.73472in" alt="A screenshot of a computer screen Description automatically generated with medium confidence" />

10. En **Choose triggering event for this policy**, mantenga la selección predeterminada y seleccione **Next**.

> <img src="media/image79.png" style="width:6.26806in;height:4.06597in" alt="A screenshot of a computer AI-generated content may be incorrect." />

11. En la página **Indicators**, abra el menú desplegable de **Office indicators (31/31 selected)**.

> <img src="media/image80.png" style="width:6.26806in;height:3.47708in" alt="A screenshot of a computer AI-generated content may b incorrect." />

12. Verifique que todos los indicadores de Office estén seleccionados y seleccione **Next**.

> <img src="media/image81.png" style="width:6.26806in;height:3.48194in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. En **Detection options**, mantenga todas las opciones en su estado predeterminado y seleccione **Next**.

> <img src="media/image82.png" style="width:6.26806in;height:3.48264in" alt="A screenshot of a computer AI-generated content may be incorrect." />

14. En **Choose threshold type for indicators**, seleccione **Choose your own thresholds**. Luego, desplácese hacia abajo y abra el menú **Office indicators**.

> <img src="media/image83.png" style="width:6.26806in;height:3.47847in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image84.png" style="width:6.26806in;height:4.1125in" alt="A screenshot of a computer AI-generated content may be incorrect." />

15. En **Sharing SharePoint files with people outside the organization**, configure los umbrales en **1**, **2** y **3** eventos para cada etapa, respectivamente. Seleccione **Next**.

> <img src="media/image85.png" style="width:6.26806in;height:3.47917in" alt="A screenshot of a computer AI-generated content may be incorrect." />

16. En **Review settings and finish**, seleccione **Submit**.

> <img src="media/image86.png" style="width:6.26806in;height:3.45764in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. En **Your policy was created**, seleccione **Done**.

> <img src="media/image87.png" style="width:6.26806in;height:3.43819in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Paso 2 – Calificar la directiva**

1.  Seleccione la nueva directiva denominada **Data theft by a user**. Seleccione **Start scoring activity for users**.

> <img src="media/image88.png" style="width:6.26806in;height:3.44722in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  En el campo **Reason for scoring activity**, escriba *Testing the policy*. En **Scoring activity for this many days (between 5 and 30)**, seleccione **10 days**.

> <img src="media/image68.png" style="width:6.26806in;height:3.45625in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  En el campo **Score activity for these users**, escriba **MOD** y seleccione **MOD Administrator**.

> <img src="media/image69.png" style="width:6.26806in;height:3.45833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  Luego, haga clic en el botón **Start scoring activity**.

> <img src="media/image70.png" style="width:6.26806in;height:3.46389in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Haga clic en el botón **Close**.

> <img src="media/image89.png" style="width:6.26806in;height:6.02361in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Tarea 3 – Fugas de datos por usuarios**

**Paso 1 – Crear una nueva política**

1.  En la página **Policies**, haga clic en **+ Create policy** y luego seleccione **Custom policy**.

> <img src="media/image72.png" style="width:6.26806in;height:3.46181in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  En la página **Choose a policy template**, elija **Data leaks** dentro de **Data leaks**. Seleccione **Next** para continuar.

> <img src="media/image90.png" style="width:6.26806in;height:3.75069in" alt="A screenshot of a computer Description automatically generated" />

3.  En la página **Name and description**, complete los siguientes campos:

    - Name: Data leaks by a user

    - Description: This is a test policy for preventing data leaks

4.  Seleccione **Next** para continuar.

> <img src="media/image91.png" style="width:6.26806in;height:3.75069in" alt="A screenshot of a computer Description automatically generated" />

5.  En la página **Choose users, groups, & adaptive scopes**, asegúrese de que el botón de opción **All users, groups, and adaptive scopes** esté seleccionado. Luego, haga clic en **Next** para continuar.

> <img src="media/image92.png" style="width:6.26806in;height:4.06458in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> En la página **Exclude users and groups (optional)**, haga clic en **Next**.

6.  En la página **Decide whether to prioritize**, seleccione **I want to priority content**. Marque las casillas **SharePoint sites**, **Sensitivity labels** y **Sensitive info types**. Haga clic en **Next**.

> <img src="media/image93.png" style="width:6.26806in;height:3.75069in" alt="A screenshot of a computer Description automatically generated wit medium confidence" />

7.  En la página **SharePoint sites to prioritize**, seleccione **Add or edit SharePoint sites**. En el panel lateral, escriba, https://WWLxXXXXXX.sharepoint.com/sites/ContosoWeb1, luego seleccione la casilla junto a **Contoso Web 1** y haga clic en **Add**. Después, haga clic en **Next**.

> **Nota:** XXXXXX **Tenant Prefix** está disponible en la pestaña **Resources.**
>
> <img src="media/image94.png" style="width:6.26806in;height:3.43333in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image95.png" style="width:6.26806in;height:3.42431in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image96.png" style="width:6.26806in;height:3.40139in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  En la página **Sensitivity labels to prioritize**, seleccione **Add or edit sensitivity labels**. En el panel lateral, escriba **employee**, luego seleccione la casilla **Internal/Employee data (HR)** y haga clic en **Add**. Después, haga clic en **Next.**

> <img src="media/image97.png" style="width:6.26806in;height:3.76667in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image98.png" style="width:6.26806in;height:4.03958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  En la página **Sensitive info types to prioritize**, seleccione **Add or edit sensitive info types**. En el panel lateral, busque y seleccione **Credit Card Number**, **Contoso Employee ID** y **Contoso Employee EDM**. Seleccione **Add** y luego haga clic en **Next**.

\![A screenshot of a computer Description automatically generated\](./media/image79.png)

11. En la página **Decide whether to score only activity with priority content**, seleccione **Get alerts for all activity** y haga clic en **Next**.

> <img src="media/image99.png" style="width:6.26806in;height:4.025in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

12. En la página **Choose triggering event for this policy**, asegúrese de que el botón de opción **User performs an exfiltration activity** esté seleccionado. Bajo **Select which activities will trigger this policy**, seleccione:

- **Download content from SharePoint**

- **Sending email with attachments to recipients outside the organization**

- **Sharing SharePoint files with people outside the organization\**
  Luego, haga clic en **Next**

> <img src="media/image100.png" style="width:6.26806in;height:4.1in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />
>
> <img src="media/image101.png" style="width:6.26806in;height:4.20278in" alt="A screenshot of a computer AI-generated content may be incorrect." />

13. En la página **Choose thresholds for triggering events**, seleccione el botón de opción **Choose your own thresholds**. Establezca cada umbral en **1** y haga clic en **Next**.

> <img src="media/image102.png" style="width:6.26806in;height:4.10694in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image103.png" style="width:6.26806in;height:3.98403in" alt="A screenshot of a computer AI-generated content may be incorrect." />

14. Mantenga la configuración predeterminada en la página **Indicators** y seleccione **Next**.

> <img src="media/image104.png" style="width:6.26806in;height:4.06111in" alt="A screenshot of a computer AI-generated content may be incorrect." />

15. Mantenga la configuración predeterminada en la página **Detection options** y seleccione **Next**.

> <img src="media/image105.png" style="width:6.26806in;height:4.125in" alt="A screenshot of a computer screen AI-generated content may be incorrect." />

16. En la página **Choose threshold type for indicators**, asegúrese de que el botón de opción **Choose your own thresholds** esté seleccionado. Luego, en **Office indicators**, use **1, 2 y 3 eventos** para cada etapa respectivamente y seleccione **Next**.

> <img src="media/image106.png" style="width:6.26806in;height:4.19306in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image107.png" style="width:6.26806in;height:4.10833in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image108.png" style="width:6.26806in;height:4.14861in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. En **Review settings and finish**, seleccione **Submit**.

> <img src="media/image109.png" style="width:6.26806in;height:4.17222in" alt="A screenshot of a computer AI-generated content may be incorrect." />

18. En **Your policy was created**, seleccione **Done**.

> <img src="media/image110.png" style="width:6.26806in;height:4.17083in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Paso 2 – Puntuar la política**

1.  En la página **Policies**, seleccione la casilla junto a la nueva política llamada **Data leaks by a user**. Luego, seleccione **Start scoring activity for users**.

> <img src="media/image111.png" style="width:6.26806in;height:3.42361in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  En el campo **Reason for scoring activity**, escriba **Testing the policy**. En el campo **Scoring activity for this many days (between 5 and 30)**, seleccione **10 days**. En el campo **Score activity for these users**, escriba **MOD** y luego seleccione **MOD administrator**.

> <img src="media/image68.png" style="width:6.26806in;height:3.45625in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image69.png" style="width:6.26806in;height:3.45833in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  Luego, haga clic en el botón **Start scoring activity**.

> <img src="media/image70.png" style="width:6.26806in;height:3.46389in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  Haga clic en el botón **Close**.

> <img src="media/image112.png" style="width:6.26806in;height:5.78194in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Resumen:**

En este laboratorio, primero preparó el entorno sincronizando los relojes de las VM y registrando los usuarios y dispositivos requeridos para **Insider Risk Management** en **Microsoft Purview**. Habilitó insights de análisis y verificó la versión del cliente antimalware de **Defender** en todas las VM objetivo. Después de registrar los dispositivos, creó tres políticas diferentes de **Insider Risk Management** para monitorear y puntuar actividades relacionadas con el uso arriesgado del navegador, el posible robo de datos por usuarios que abandonan la organización y las fugas de datos por usuarios internos. Cada política se personalizó con etiquetas de sensibilidad, sitios de **SharePoint** y tipos de información sensible como contenido prioritario, y se configuraron umbrales para activar alertas y puntuaciones. Finalmente, inició las actividades de puntuación para simular escenarios reales de riesgo interno y evaluar la efectividad de las políticas configuradas.
