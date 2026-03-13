**Laboratorio 6 – Crear y administrar directivas DLP**

**Introducción**

Usted es Patti Fernandez, la nueva Administradora de Cumplimiento en Contoso Ltd., encargada de configurar el tenant de Microsoft 365 de la compañía para la prevención de pérdida de datos. Contoso Ltd. es una empresa que ofrece instrucción de manejo en los Estados Unidos y se requiere garantizar que la información sensible de los clientes no salga de la organización.

**Objetivos**

- Crear y probar directivas DLP en Microsoft Purview.

- Utilizar PowerShell para administrar configuraciones DLP.

- Habilitar el monitoreo de archivos y crear directivas de archivos en Defender for Cloud Apps.

- Implementar DLP para Power Platform con el fin de controlar flujos de datos.

**Ejercicio 1 – Crear directivas DLP**

**Tarea 1 – Crear una directiva DLP en modo de prueba**

En este ejercicio se creará una directiva de Data Loss Prevention en el portal de Microsoft Purview para proteger datos sensibles que puedan ser compartidos por los usuarios. La directiva notificará a los usuarios cuando intenten compartir contenido que contenga información de tarjetas de crédito y les permitirá proporcionar una justificación para enviarla. La directiva se implementará en modo de prueba para evitar que la acción de bloqueo afecte a los usuarios por el momento.

1.  En **Microsoft Edge**, navegue a <https://purview.microsoft.com> y confirme que se ha iniciado sesión en el portal de **Microsoft Purview** como **Patti Fernandez.**

2.  En el portal de **Microsoft Purview**, en el panel de navegación izquierdo, seleccione **Solutions \> Data loss prevention**.

> <img src="media/image1.png" style="width:6.26806in;height:3.33333in" />

3.  En **Data loss prevention**, seleccione **Policies** y luego **+Create policy** para iniciar el asistente de creación de una nueva directiva DLP.

> <img src="media/image2.png" style="width:6.26806in;height:3.26875in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  En el panel **What info do you want to protect?**, seleccione **Enterprise applications and devices**.

> <img src="media/image3.png" style="width:6.26806in;height:3.53472in" />

5.  En la página **Start with a template or create a custom policy**, desplácese hacia abajo y seleccione **Custom** en la sección **Categories**. Luego seleccione **Custom policy** en **Regulations**. Seleccione **Next**.

> <img src="media/image4.png" style="width:6.26806in;height:3.3375in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  En la página **Name your DLP policy**, escriba Credit Card DLP Policy en el campo **Name** y Protect credit card numbers from being shared. en el campo **Description**. Seleccione **Next.**

> <img src="media/image5.png" style="width:6.26806in;height:3.31875in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  En la página **Assign admin units**, seleccione **Next**.

> <img src="media/image6.png" style="width:6.26806in;height:3.28889in" />

8.  En **Choose where to apply the policy**, marque **Teams chat and channel messages** y desmarque las demás opciones. Seleccione **Next**.

> <img src="media/image7.png" style="width:6.26806in;height:3.34167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  En **Define policy settings**, confirme que la opción **Create or customize advanced DLP rules** esté seleccionada y seleccione **Next**.

> <img src="media/image8.png" style="width:6.26806in;height:3.29931in" />

10. En **Customize advanced DLP rules**, seleccione **+ Create rule**.

> <img src="media/image9.png" style="width:6.26806in;height:3.32361in" />

11. En **Create rule**, escriba el nombre de la regla en el campo **Name**.

> <img src="media/image10.png" style="width:6.26806in;height:3.32639in" alt="A screenshot of a computer Description automatically generated" />

12. En la sección Conditions, seleccione **+ Add condition** y elija **Content is shared from Microsoft 365**.

> <img src="media/image11.png" style="width:6.26806in;height:3.32639in" />

13. En la sección agregada, seleccione **with people outside my organization**.

> <img src="media/image12.png" style="width:6.26806in;height:3.32639in" alt="A screenshot of a computer Description automatically generated" />

14. Seleccione nuevamente **+ Add condition** y elija **Content contains**.

> <img src="media/image13.png" style="width:6.26806in;height:3.32639in" alt="A screenshot of a computer Description automatically generated" />

15. En la nueva sección, seleccione **Add**, luego elija **Sensitive info types**.

> <img src="media/image14.png" style="width:6.26806in;height:3.32639in" />

16. En el panel lateral, busque credit card number, presione Enter, seleccione la casilla junto a **Credit Card Number** y seleccione **Add**.<img src="media/image15.png" style="width:6.26806in;height:3.31528in" alt="A screenshot of a computer AI-generated content may be incorrect." />

17. En la página de creación de regla, seleccione **+ Add an action** y elija **Restrict access or encrypt the content in Microsoft 365 locations**.

> <img src="media/image16.png" style="width:6.26806in;height:3.32639in" />

18. En esta sección, asegúrese de seleccionar **Block users from receiving email or accessing shared SharePoint, OneDrive, and Teams files, and Power BI items**, y seleccione **Block only people outside your organization**.

> <img src="media/image17.png" style="width:6.26806in;height:3.32639in" alt="A screenshot of a computer Description automatically generated" />

19. En **User notifications**, active el interruptor.

> <img src="media/image18.png" style="width:6.26806in;height:3.32639in" alt="A screenshot of a computer Description automatically generated" />

20. En la página **Create rule**, en la sección **User overrides**, en **Allow overrides from M365 services**, marque la casilla **Allow overrides from M365 services**. Permite que los usuarios en Exchange, SharePoint, OneDrive y Teams omitan las restricciones de la directiva**.**

> <img src="media/image19.png" style="width:6.26806in;height:3.32639in" />

**Nota:** Si no pudo seleccionar la casilla **Allow overrides from M365 services,** active la casilla **Notify users in Office 365 with a policy tip,** la cual se encuentra en la página **Create rule,** en la sección **User notification \> Microsoft 365 services del paso anterior.** Luego, marque la casilla **Allow overrides from M365 services.** Permite que los usuarios en **Exchange, SharePoint, OneDrive y Teams** omitan las restricciones de la directiva.

21. Marque la casilla **Require a business justification to override**.

> <img src="media/image20.png" style="width:6.26806in;height:3.32639in" alt="A screenshot of a computer AI-generated content may be incorrect." />

22. En la sección **Incident reports**, en el menú desplegable **Use this severity level in admin alerts and reports**, seleccione **Low**.

> <img src="media/image21.png" style="width:6.26806in;height:3.32639in" />

23. Seleccione **Save**, luego seleccione **Next**.

> <img src="media/image22.png" style="width:6.26806in;height:3.32639in" alt="A screenshot of a computer Description automatically generated" />
>
> <img src="media/image23.png" style="width:6.26806in;height:3.33194in" alt="A screenshot of a computer AI-generated content may be incorrect." />

24. En la página **Policy mode**, asegúrese de que el botón de opción **Run the policy in simulation mode** esté seleccionado y asegúrese de que la casilla junto a **Show policy tips while in test mode** esté seleccionada. Luego, seleccione el botón **Next**.

> <img src="media/image24.png" style="width:6.26806in;height:3.34306in" alt="A screenshot of a computer AI-generated content may be incorrect." />

25. Seleccione **Submit** para crear la directiva.

> <img src="media/image25.png" style="width:6.26806in;height:3.32708in" alt="A screenshot of a computer AI-generated content may be incorrect." />

26. Una vez creada la directiva, seleccione **Done**.

> <img src="media/image26.png" style="width:6.26806in;height:3.35486in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> Ha creado una directiva DLP que escanea números de tarjetas de crédito en los chats y canales de Microsoft Teams y permite que los usuarios proporcionen una justificación empresarial para omitir la directiva.
>
> <img src="media/image27.png" style="width:6.26806in;height:3.33125in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Tarea 2 – Modificar una política de DLP**

En esta tarea, modificará la política de DLP existente creada en el paso anterior para incluir también el análisis de correos electrónicos en busca de información de tarjetas de crédito e informar a los usuarios si intentan compartir este contenido en un correo electrónico.

1.  **Seleccione** la casilla situada junto a *Credit Card DLP Policy* y luego **seleccione** el ícono **Edit** en la barra de comandos, como se muestra en la imagen.

> <img src="media/image28.png" style="width:6.26806in;height:3.31944in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  En la página **Name your DLP policy and Assign admin units**, seleccione **Next.**

> <img src="media/image29.png" style="width:6.26806in;height:3.34306in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image30.png" style="width:6.26806in;height:3.33472in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  En la página **Choose where to apply the policy**, seleccione únicamente la casilla situada junto a **Exchange email** y luego seleccione **Next** hasta llegar a la página **Review and finish.**

> <img src="media/image31.png" style="width:6.26806in;height:3.34792in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  Seleccione **Submit** para aplicar el cambio realizado en la política.

> <img src="media/image32.png" style="width:6.26806in;height:3.34306in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Una vez que la política se haya actualizado, seleccione el botón **Done.**

> <img src="media/image33.png" style="width:6.26806in;height:3.26806in" alt="A screenshot of a computer AI-generated content may be incorrect." />

Ha modificado correctamente una política de DLP existente y ajustado las ubicaciones en las que analiza contenido.

**Tarea 3 – Crear una política de DLP en PowerShell**

En esta tarea, utilizará PowerShell para crear una política de DLP que proteja los Contoso EmployeeIDs y evite que se compartan en Exchange. Los usuarios serán informados de que están intentando compartir datos confidenciales y se bloqueará el envío del correo electrónico si incluye Contoso EmployeeIDs.

1.  **Haga clic derecho** en el ícono de Windows en la barra de tareas y **seleccione** *Windows PowerShell (Admin)* para ejecutarlo como administrador.

> <img src="media/image34.png" style="width:6.26806in;height:5.25764in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  En el cuadro de diálogo *User Account Control*, **haga clic** en el botón *Yes*.

> <img src="media/image35.png" style="width:6.26806in;height:4.40764in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  En PowerShell, **ejecute** los siguientes comandos:

> Install-Module ExchangeOnlineManagement
>
> Import-Module ExchangeOnlineManagement
>
> <img src="media/image36.png" style="width:6.26806in;height:1.62222in" alt="A screenshot of a computer program AI-generated content may be incorrect." />
>
> <img src="media/image37.png" style="width:6.26806in;height:1.75972in" alt="A screen shot of a computer program AI-generated content may be incorrect." />

4.  En la ventana de PowerShell, **ingrese**, Connect-IPPSSession y luego inicie sesión como **Patti Fernandez**.

> <img src="media/image38.png" style="width:6.26806in;height:2.08681in" alt="A screen shot of a computer screen AI-generated content may be incorrect." />
>
> <img src="media/image39.png" style="width:6.26806in;height:5.29861in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> En caso de que aparezca el cuadro de diálogo **Automatically sign in to all desktop apps and websites on this device?**, seleccione **No, this app only**.
>
> <img src="media/image40.png" style="width:6.26806in;height:4.74792in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image41.png" style="width:6.26806in;height:2.39514in" alt="A screenshot of a computer error AI-generated content may be incorrect." />

5.  Ingrese el siguiente comando en PowerShell para crear una política de DLP que analice todos los buzones de Exchange:

> New-DlpCompliancePolicy -Name "EmployeeID DLP Policy" -Comment "This policy blocks sharing of Employee IDs" -ExchangeLocation All
>
> <img src="media/image42.png" style="width:6.26806in;height:3.85556in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  Ingrese el siguiente comando en PowerShell para agregar una regla de DLP a la política creada en el paso anterior:

> New-DlpComplianceRule -Name "EmployeeID DLP rule" -Policy "EmployeeID DLP Policy" -BlockAccess \$true -ContentContainsSensitiveInformation @{Name="Contoso Employee IDs"}
>
> <img src="media/image43.png" style="width:6.26806in;height:4.75208in" alt="A screenshot of a computer program AI-generated content may be incorrect." />
>
> <img src="media/image44.png" style="width:6.26806in;height:4.72778in" alt="A screenshot of a computer program AI-generated content may be incorrect." />

7.  Use el siguiente comando para revisar la regla **EmployeeID DLP rule**:

> Get-DLPComplianceRule -Identity "EmployeeID DLP rule"
>
> <img src="media/image45.png" style="width:6.26806in;height:4.60903in" alt="A screenshot of a computer program AI-generated content may be incorrect." />

Ha creado una política de DLP que analiza *Contoso EmployeeIDs* en Exchange mediante PowerShell.

**Tarea 4 – Activar una política en modo de prueba**

En esta tarea, activará la política de DLP de información de tarjetas de crédito que creó en modo de prueba para que aplique sus acciones de protección.

1.  En una ventana **InPrivate de Microsoft Edge**, navegue a [**https://purview.microsoft.com**](https://purview.microsoft.com) y asegúrese de haber iniciado sesión en el portal de **Microsoft Purview** como **Patti Fernandez**.

2.  En el portal de **Microsoft Purview**, en el panel de navegación izquierdo, seleccione **Solutions \> Data loss prevention**.

> <img src="media/image46.png" style="width:6.26806in;height:2.95764in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  En **Data loss prevention**, seleccione **Policies**, luego seleccione la política denominada **Credit Card DLP Policy** y después seleccione **Edit policy** (icono de lápiz) para abrir el asistente de políticas.

> <img src="media/image47.png" style="width:6.26806in;height:2.97569in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  Seleccione **Next** hasta llegar a la página **Test or turn on the policy** y seleccione **Turn the policy on immediately**.

> <img src="media/image48.png" style="width:6.26806in;height:3.08819in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Seleccione **Next**, luego seleccione **Submit** para activar la política.

> <img src="media/image49.png" style="width:6.26806in;height:3.52569in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  Una vez que la política se haya actualizado, seleccione **Done**.

> <img src="media/image50.png" style="width:6.26806in;height:3.12014in" alt="A screenshot of a computer AI-generated content may be incorrect." />

Ha activado correctamente la política de DLP. Si la política detecta un intento de compartir información de tarjetas de crédito, ahora bloqueará el intento y permitirá que los usuarios proporcionen una justificación empresarial para invalidar la acción de bloqueo.

**Ejercicio 2 – Administrar políticas de DLP**

**Tarea 1 – Modificar la prioridad de una política**

Después de crear dos políticas de DLP, desea asegurarse de que la política más restrictiva se procese con una prioridad más alta que la política menos restrictiva. Por este motivo, desea mover la **EmployeeID DLP Policy** a una prioridad superior.

1.  En **Microsoft Edge**, navegue a [**https://purview.microsoft.com**](https://purview.microsoft.com) y asegúrese de haber iniciado sesión en el portal de **Microsoft Purview** como **Patti Fernandez**.

2.  En el portal de Microsoft Purview, en el panel de navegación izquierdo, seleccione **Solutions \> Data loss prevention**.

> <img src="media/image46.png" style="width:6.26806in;height:2.95764in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  En **Data loss prevention**, seleccione **Policies**, luego seleccione la política denominada **Credit Card DLP Policy**. Seleccione **Move to top (highest priority)**.

> <img src="media/image51.png" style="width:6.26806in;height:2.98542in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  En la ventana **Data loss prevention**, seleccione **Refresh** y revise la prioridad en la columna **Order** de la tabla de políticas.

> <img src="media/image52.png" style="width:6.26806in;height:3.01597in" alt="A screenshot of a computer AI-generated content may be incorrect." />

Ha modificado correctamente la prioridad de sus políticas de DLP. Si ambas políticas coinciden con el mismo contenido, se aplicará la acción de la política con mayor prioridad.

**Tarea 2 – Habilitar la supervisión de archivos en Microsoft Defender**

Desea utilizar las políticas de archivos en **Microsoft Defender** para proteger archivos en sus ubicaciones de OneDrive y SharePoint Online. Antes de poder crear una política de archivos, es necesario habilitar la supervisión de archivos para que Microsoft Defender pueda analizar los archivos de su organización.

1.  Abra una nueva pestaña en su navegador habitual Microsoft Edge, introduzca la siguiente URL en la barra de direcciones para abrir el portal de Microsoft Defender:  https://security.microsoft.com. Luego, inicie sesión en el portal de Microsoft Defender como **MOD Administrator**.

2.  En el portal de Microsoft Defender, desplácese hacia abajo y haga clic en **System \> Settings** en el menú de navegación del lado izquierdo. En la página **Settings**, haga clic en **Cloud Apps**.

> <img src="media/image53.png" style="width:6.26806in;height:3.72917in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  Ahora, desplácese hacia abajo hasta la sección **Information Protection**, luego haga clic en **Files**. En la página **Files**, seleccione la casilla situada junto a **Enable file monitoring**, luego haga clic en el botón **Save**.

> <img src="media/image54.png" style="width:6.26806in;height:2.98403in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Nota:** Si la supervisión de archivos (File monitoring) ya se encuentra habilitada de forma predeterminada, entonces ignore el paso anterior y continúe con la siguiente tarea.

Ha habilitado correctamente la supervisión de archivos en Microsoft Defender for Cloud Apps y ahora puede analizar archivos en busca de contenido sensible utilizando políticas de archivos.

**Tarea 3 – Crear una File Policy para Microsoft Defender**

En esta tarea, se desea crear una File Policy en Microsoft Defender para analizar archivos en OneDrive y SharePoint Online y poner automáticamente en cuarentena los archivos que contengan información de tarjetas de crédito si son compartidos.

1.  Ahora, bajo la misma sección **Information Protection**, haga clic en **Microsoft Information Protection**, luego seleccione la casilla junto a **Automatically scan new files for Microsoft Information Protection sensitivity labels and content inspection warnings**. Después, haga clic en el botón **Save**.

> <img src="media/image55.png" style="width:6.26806in;height:3.00139in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image56.png" style="width:6.26806in;height:2.98819in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  En **Inspect protected files**, haga clic en **Grant Permission**.

> <img src="media/image57.png" style="width:6.26806in;height:3.21389in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  Aparecerá el cuadro de diálogo **Pick an account**, luego seleccione las credenciales del tenant **MOD Administrator.**

\![A screenshot of a computer AI-generated content may be incorrect.\](./media/image58.png)

4.  En la página **Permissions requested**, haga clic en el botón **Accept**.

> <img src="media/image58.png" style="width:6.26806in;height:4.51111in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Se observará el estado **Active**, lo que indica que el permiso se ha concedido correctamente.

> <img src="media/image59.png" style="width:6.26806in;height:3.08056in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  En la subnavegación, bajo la sección **Connected apps**, haga clic en **App Connectors**, luego asegúrese de que **Microsoft 365** esté agregado.

> <img src="media/image60.png" style="width:6.26806in;height:3.01667in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  Ahora, en el panel de navegación izquierdo del portal de Microsoft Defender, expanda **Policies** bajo la sección **Cloud Apps** y seleccione **Policy management**.

> <img src="media/image61.png" style="width:6.26806in;height:3.09167in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  En la página **Policies**, haga clic en **Create policy**, luego seleccione **File policy**.

> <img src="media/image62.png" style="width:6.26806in;height:2.95556in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  En la página **Create file policy**, escriba Credit Card Information for files. en el campo **Policy name** y escriba Protect credit card numbers from being shared in files. en el campo **Description**.

> <img src="media/image63.png" style="width:6.26806in;height:3.40556in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. Mantenga la **Policy Severity** en **Low** (un icono iluminado) y asegúrese de que la categoría esté establecida en **DLP**. Para una file policy, esto debería ser el valor predeterminado.

> <img src="media/image64.png" style="width:6.26806in;height:3.03958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

11. En el área **Files matching all of the following**, expanda el menú desplegable **Public (Internet), External, Public** y agregue **Internal**.

> <img src="media/image65.png" style="width:6.26806in;height:3.4375in" alt="A screenshot of a computer AI-generated content may be incorrect." />

12. En la sección **Apply to**, en el menú desplegable **Inspection Method**, seleccione **Data Classification Service**.

> <img src="media/image66.png" style="width:6.26806in;height:4.625in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> **Nota:** Si aún no ve **Data Classification Service** en el menú desplegable, seleccione **None** por el momento. Una vez finalizado, regrese más tarde a **Policies \> Policy management \> All Policies \> Search for name: Credit card \> Select Credit Card Information for files.**

<img src="media/image67.png" style="width:6.26806in;height:3.57292in" alt="A screenshot of a computer Description automatically generated" />

13. En el menú desplegable **Choose inspection type…**, seleccione **Sensitive information type…**

<img src="media/image68.png" style="width:6.26806in;height:3.92083in" alt="Graphical user interface, text, application Description automatically generated" />

14. En el cuadro de diálogo **Select a sensitive information type**, escriba Credit Card Number en la barra de búsqueda, seleccione la casilla situada junto a **Credit Card Number**, luego haga clic en el botón **Done**.

> <img src="media/image69.png" style="width:6.26806in;height:2.90903in" alt="A screenshot of a computer AI-generated content may be incorrect." />

15. En la sección **Alerts**, seleccione la casilla junto a **Create an alert for each matching file**. Luego, haga clic en el botón **Save as default settings**.

> <img src="media/image70.png" style="width:6.26806in;height:4.11944in" alt="A screenshot of a computer AI-generated content may be incorrect." />

16. En la sección **Governance actions**, expanda **Microsoft OneDrive for Business** y seleccione **Put in user quarantine**.

> <img src="media/image71.png" style="width:6.26806in;height:4.12847in" alt="A screenshot of a computer Description automatically generated" />

17. En la sección **Governance actions**, expanda **Microsoft SharePoint Online** y seleccione **Put in user quarantine**.

> <img src="media/image72.png" style="width:6.26806in;height:4.12847in" alt="A screenshot of a computer Description automatically generated" />

18. Seleccione **Create** en la parte inferior de la página.

> <img src="media/image73.png" style="width:6.26806in;height:3.92083in" alt="Graphical user interface, text, application Description automatically generated" />

19. Seleccione la **imagen de perfil** del **MOD Admin** en la esquina superior derecha y seleccione **Sign out** junto al ícono del engranaje, luego cierre el navegador.

> <img src="media/image74.png" style="width:6.26806in;height:3.24444in" alt="A screenshot of a computer AI-generated content may be incorrect." />

Ha creado una file policy que analizará continuamente los archivos guardados en OneDrive y SharePoint para detectar información de tarjetas de crédito y los pondrá en cuarentena si se comparten dentro de su organización.

**Tarea 4 – Crear una DLP Policy para Power Platform**

Su empresa usa Power Automate flows para compartir datos entre SharePoint Online y Salesforce. En esta tarea, se creará una DLP policy para Power Platform que permita que los flows existentes continúen funcionando, pero que impida la creación de nuevos flows que compartan datos entre SharePoint Online y aplicaciones definidas como no empresariales (*non-business*).

1.  En **Microsoft Edge**, navegue a https://admin.powerplatform.microsoft.com e inicie sesión en el Power Platform admin center como **MOD Administrator**.

2.  En la página principal del **Power Platform** **admin center**, navegue y haga clic en **Security**.

> <img src="media/image75.png" style="width:6.26806in;height:3.12083in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  Luego, haga clic en el icono **Data and privacy** como se muestra en la imagen.

> <img src="media/image76.png" style="width:6.26806in;height:3.33056in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  En la página **Data protection and privacy**, navegue y haga clic en **Data policy**.

> <img src="media/image77.png" style="width:6.26806in;height:3.3in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  En la página **Data policies**, seleccione **+ New Policy**.

> <img src="media/image78.png" style="width:6.26806in;height:3.92083in" alt="Graphical user interface, application, Teams Description automatically generated" />

6.  En la página **Name your policy**, escriba **Tenant-wide SharePoint Policy**, luego seleccione **Next**.

> <img src="media/image79.png" style="width:6.26806in;height:3.92083in" alt="Graphical user interface, text, application Description automatically generated" />

7.  En la pestaña **Non-business \| Default**, seleccione **SharePoint** y **Salesforce**, luego seleccione **Move to Business** en la parte superior de la página.

> <img src="media/image80.png" style="width:6.26806in;height:3.35208in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  En la página **Assign connectors**, seleccione la pestaña **Business** para verificar que tanto SharePoint como Salesforce aparecen ahora en ella.

> <img src="media/image81.png" style="width:6.26806in;height:3.92083in" alt="Graphical user interface, application Description automatically generated" />

9.  Seleccione **Next** dos veces.

> <img src="media/image82.png" style="width:6.26806in;height:3.92083in" alt="Graphical user interface, application Description automatically generated" />
>
> <img src="media/image83.png" style="width:6.26806in;height:3.92083in" alt="Graphical user interface, text, application Description automatically generated" />

10. En la página **Define scope**, seleccione **Add all environments**, luego seleccione **Next**.

> <img src="media/image84.png" style="width:6.26806in;height:3.92083in" alt="Graphical user interface, text, application Description automatically generated" />

11. En la página **Review and create policy**, revise la configuración de la policy y seleccione **Create policy**.

> <img src="media/image85.png" style="width:6.26806in;height:3.92083in" alt="A screenshot of a computer Description automatically generated" />
>
> Ha creado una Power Platform DLP policy que evita que los usuarios creen flows que incluyan un conector de SharePoint Online y cualquier conector que no sea Salesforce.
>
> <img src="media/image86.png" style="width:6.26806in;height:2.84653in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Resumen:**

En este laboratorio, se crearon y administraron Data Loss Prevention (DLP) policies para proteger datos confidenciales como números de tarjetas de crédito e identificaciones de empleados en Microsoft Teams, Exchange, OneDrive, SharePoint y Power Platform. Se construyeron policies mediante Microsoft Purview y PowerShell, se habilitaron notificaciones y reemplazos de usuario, se priorizaron policies, se activó el monitoreo de archivos en Microsoft Defender y se configuraron acciones de cuarentena de archivos. Además, se creó una Power Platform DLP policy para restringir el intercambio de datos con conectores no empresariales.
