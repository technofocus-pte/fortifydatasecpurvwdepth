# Laboratorio 9 – Configuración de Communication Compliance 

## Objetivo:

En este laboratorio, configurará una política de cumplimiento para
detectar cualquier información confidencial que comuniquen los usuarios
de su organización. Utilizará los tipos de información confidencial
creados en el laboratorio anterior para detectar los datos de salud de
los empleados o los IDs de los empleados que se comunican a través de
correos electrónicos.

## Ejercicio 1 – Habilitar permisos para Communication Compliance 

En esta tarea, asignará usuarios a grupos de funciones específicos para
segmentar el acceso y las responsabilidades de cumplimiento de las
comunicaciones entre los diferentes usuarios de su organización.

1.  El portal Microsoft Purview está abierto. Continúe con el paso 2,
    abra `https://purview.microsoft.com` e inicie sesión con las
    credenciales **MOD Administrator**.

2.  En el panel de navegación, seleccione **Settings**, y seleccione
    **Role** **groups** en **Role groups**, seleccione **Communication
    Compliance**. Luego seleccione **Edit**. En el panel lateral,
    seleccione de nuevo **Edit**.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

3.  En **Edit members of the role group** seleccione **Choose Users**.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

4.  Asegúrese de seleccionar **MOD Administrator**, **Megan Bowen**, y
    **Patti Fernandez**. Luego, seleccione **Select**.

![](./media/image3.png)

5.  Seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image4.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

6.  Seleccione **Save** para añadir los usuarios al grupo de funciones.
    Seleccione **Done** para completar los pasos.

![A screenshot of a computer Description automatically
generated](./media/image5.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

![A screenshot of a computer Description automatically
generated](./media/image6.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

## Ejercicio 2 – Configuración de grupos para cumplimiento de comunicaciones 

En la política, utilizará direcciones de correo electrónico para
identificar a personas o grupos de personas. Para simplificar su
configuración, puede crear grupos para personas que revisan sus
comunicaciones y grupos para personas que revisan esas comunicaciones.

Puede utilizar PowerShell para configurar un grupo de distribución para
una política de cumplimiento de comunicaciones global para el grupo
asignado. Esto le permite detectar mensajes para miles de usuarios con
una sola política y mantener actualizada la política de cumplimiento de
comunicaciones a medida que nuevos empleados se unen a su organización.

1.  Abra **PowerShell** en modo administrador.

2.  Ingrese el siguiente cmdlet para utilizer el módulo **Exchange
    Online PowerShell** y conectarse a su tenant:

`Connect-ExchangeOnline`

![Text Description automatically generated](./media/image7.png)

Descripción del texto generada automáticamente

3.  Cuando aparezca la ventana **Sign in**, inicie sesión como **MOD
    Administrator**.

![BrokenImage](./media/image8.png)


4.  Cree un grupo de distribución específico para su política de
    cumplimiento de las comunicaciones globales con las siguientes
    propiedades:

    - **MemberDepartRestriction = Closed**. Garantiza que los usuarios
      no puedan eliminarse a sí mismos del grupo de distribución.

    - **MemberJoinRestriction = Closed**. Garantiza que los usuarios no
      puedan agregarse a sí mismos al grupo de distribución.

    - **ModerationEnabled = True**. Garantiza que todos los mensajes
      enviados a este grupo estén sujetos a aprobación y que el grupo no
      se utilice para comunicarse fuera de la configuración de la
      política de cumplimiento de comunicaciones.

`New-DistributionGroup -Name "Communication Compliance Group Contoso" -Alias "CCG_Contoso" -MemberDepartRestriction 'Closed' -MemberJoinRestriction 'Closed' -ModerationEnabled $true`

![BrokenImage](./media/image9.png)


**Nota:** Puede agregar un **Exchange Custom Attribute** como en el
**siguiente comando** para rastrear a los usuarios agregados a la
política de cumplimiento de comunicación en su organización.

`Set-DistributionGroup -Identity "Communication Compliance Group Contoso"-CustomAttribute1 "MonitoredCommunication"`

![A screen shot of a computer Description automatically
generated](./media/image10.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

5.  Ejecute el siguiente script de PowerShell en un programa recurrente
    para agregar usuarios a la política de cumplimiento de
    comunicaciones:

&nbsp;

    $Mbx = (Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize Unlimited -Filter {CustomAttribute9 -eq $Null})
    $i = 0
    ForEach ($M in $Mbx)
    {
    Write-Host "Adding" $M.DisplayName
    Add-DistributionGroupMember -Identity "Communication Compliance Group Contoso" -Member $M.DistinguishedName -ErrorAction SilentlyContinue
    Set-Mailbox -Identity $M.Alias -CustomAttribute1 "MonitoredCommunication"
    $i++
    }
    Write-Host $i "Mailboxes added to supervisory review distribution group."

![BrokenImage](./media/image11.png)



**Nota:** Se supone que este script debe ejecutarse después de cada
intervalo en particular. A partir de ahora podrá ver la lista de
distribución en Teams y grupos activos en el centro de administración de
Microsoft 365.

Si hace clic en el nombre del grupo, podrá ver todos los usuarios que
aparecen en la pestaña de miembros.

![BrokenImage](./media/image12.png)


## Ejercicio 3 – Creación de una política de cumplimiento de comunicaciones

1.  Si el portal de cumplimiento de Microsoft Purview está abierto,
    continúe con el paso 2, de lo contrario,
    abra `https://purview.microsoft.com` e inicie sesión como **MOD
    Administrator**.

2.  En el portal Microsoft Purview, seleccione **Solutions** \>
    **Communication compliance**.

3.  Seleccione en el submenú, seleccione **Policy**. Y luego seleccione
    **Create policy**.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

4.  Seleccione **Custom policy** en el menú desplegable.

![](./media/image14.png)

5.  En la página Name your DLP policy,
    escriba `My first communication compliance policy` en el cambo
    **Name** y `This is a policy to test communication compliance` en el
    campo **Description**. Seleccione **Next**.

![Graphical user interface, text, application Description automatically
generated](./media/image15.png)

Interfaz gráfica de usuario, texto, descripción de la aplicación
generada automáticamente

6.  En la página **Choose supervised users and reviewers**, mantenga el
    resto de la configuración predeterminada y en reviews, añada a
    **Patti Fernandez**. Después haga clic en **Next**.

![A screenshot of a computer Description automatically
generated](./media/image16.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

7.  En la página **communications**, marque todas las casillas debajo
    de **Microsoft 365 locations** y haga clic en **Next**.

![A screenshot of a computer Description automatically
generated](./media/image17.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

8.  En **Choose conditions and review percentage**, seleccione **Add
    condition**, en el menú desplegable, seleccione **Content contains
    any of these sensitive info types**.

![A screenshot of a computer screen Description automatically
generated](./media/image18.png)

Una captura de pantalla de una descripción de pantalla de ordenador
generada automáticamente

9.  En el cuadro **Content contains any of these sensitive info types**,
    selectcione **Add**, haga clic en **Sensitive info types**, y
    busque **contoso**. Marque las casillas de todos los tipos de
    información confidencial que creamos en los laboratorios anteriores.
    A continuación, haga clic en **Add.**

![Graphical user interface, text, application Description automatically
generated](./media/image19.png)

Interfaz gráfica de usuario, texto, descripción de la aplicación
generada automáticamente

10. En **Choose conditions and review percentage**, marque la casilla
    junto a **Use OCR to extract text from images**, establezca **Review
    percentage to 100%**, y luego haga clic en **Next**.

![Graphical user interface, application Description automatically
generated](./media/image20.png)

Interfaz gráfica de usuario, descripción de la aplicación generada
automáticamente

11. En la página **Review and finish**, seleccione **Create policy**.

![Graphical user interface, text, application Description automatically
generated](./media/image21.png)

Interfaz gráfica de usuario, texto, descripción de la aplicación
generada automáticamente

12. Aparece la página **Your policy was created** con las pautas sobre
    cuándo se activará la política y qué comunicaciones se capturarán.

![Graphical user interface, text, application Description automatically
generated](./media/image22.png)

Interfaz gráfica de usuario, texto, descripción de la aplicación
generada automáticamente

## Ejercicio 4 – Edición de una política de cumplimiento de comunicaciones 

1.  Si el portal de cumplimiento de Microsoft Purview está abierto,
    continúe con el paso 2, de lo contrario,
    abra `https://purview.microsoft.com` e inicie sesión como **MOD
    Administrator**.

2.  En el portal Microsoft Purview, vaya a **Settings** \>
    **Communication compliance** \> **Policies**, seleccione los tres
    puntos junto a **My first communication compliance policy** y
    seleccione **Edit**.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

3.  Deje **Name and describe your policy** en blanco y haga clic
    en **Next**.

![Graphical user interface, text, application Description automatically
generated](./media/image24.png)

Interfaz gráfica de usuario, texto, descripción de la aplicación
generada automáticamente

4.  En **Choose supervised user and reviewers** y en **Supervised
    users and groups**, seleccione el botón **Select users**.

![Graphical user interface, application, Teams Description automatically
generated](./media/image25.png)

Interfaz gráfica de usuario, aplicación, descripción de Teams generada
automáticamente

5.  En **Start typing to find users or groups**,
    busque **Communication** y seleccione **Communication Compliance
    Groups Contoso**.

![](./media/image26.png)

6.  En Choose supervised user and reviewers en Reviewers añada MOD
    Administrator a los Reviewers.

![Graphical user interface, application, Teams Description automatically
generated](./media/image27.png)

Interfaz gráfica de usuario, aplicación, descripción de Teams generada
automáticamente

7.  Seleccione **Next** hasta llegar a la página **Review and finish**.

8.  Haga clic en **Save**.

## Ejercicio 5 – Creación de plantillas de notificación y configuración de anonimización de usuarios 

1.  En el portal Microsoft Purview, seleccione Settings en la esquina
    superior derecha y seleccione **Communication compliance**.

![](./media/image28.png)

2.  Seleccione la pestaña **Privacy**. Para habilitar el anonimato,
    asegúrese de que **Show anonymized versions of usernames** esté
    seleccionado. Seleccione **Save**.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

3.  Vaya a la pestaña **Notice templates** y seleccione **Create notice
    template**.

![](./media/image30.png)

4.  En la página **Modify a notice template**, complete los siguientes
    campos:

    - Template name (requerido): `Sample Notice`

    - Send from (requerido): Seleccione **Patti Fernandez**
      escribiendo **Patti** y seleccionando el nombre en el menú
      desplegable.

    - Cc (opcional): Seleccione
      **MOD** **administrator** escribiendo **MOD** y seleccionando el
      nombre en el menú desplegable.

    - Subject
      (requerido): `Your communication violets company Communication compliance policy.`

    - Message body
      (requerido): `Please note this for future reference and provide an acceptable justification for your current communication.`

5.  Seleccione **Create** para crear y guardar la plantilla de aviso.

![A screenshot of a computer Description automatically
generated](./media/image31.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

## Ejercicio 6 – Validación de políticas de cumplimiento de comunicaciones 

En la cuenta de prueba no tendrá el privilegio de enviar ningún correo
electrónico, pero puede consultar los siguientes pasos para entender
cómo probar la política cuando tenga sus propias licencias. Puede
realizar los pasos, pero su correo no podrá llegar al destinatario desde
su tenant actual.

1.  Abra Outlook yendo a `https://outlook.office365.com/mail/`` `e
    inicie sesión con el nombre de usuario
    `adelev``@{TENANTPREFIX``}.onmicrosoft.com` y la contraseña de
    usuario.

2.  Envíe un correo electrónico a su cuenta de correo electrónico
    personal con el siguiente cuerpo de mensaje.

Message
body: `Employee Patti Fernandez EMP123456 is on absence because of the flu/influenza`

**Nota:** Los mensajes de correo electrónico pueden tardar
aproximadamente 24 horas en procesarse completamente en una política.
Las comunicaciones en Microsoft Teams, Yammer y plataformas de terceros
pueden tardar aproximadamente 48 horas en procesarse completamente en
una política.

Inicie sesión en `https://purview.microsoft.com/` como **Patti
Fernandez**. Vaya a **Communication compliance** \> **Alerts** para ver
las alertas de sus políticas pasadas 24 horas.

**Resumen:**

En este laboratorio aprendimos a habilitar los permisos para el
cumplimiento de las comunicaciones, crear las políticas, gestionarlas y,
a continuación, crear plantillas de avisos y configurar la anonimización
de usuarios.
