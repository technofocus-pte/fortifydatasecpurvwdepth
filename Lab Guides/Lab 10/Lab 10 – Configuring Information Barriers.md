# Laboratorio 10 – Configuración de barreras de información en Microsoft 365

## Objetivo:

Contoso tiene cinco departamentos: *Recursos Humanos, Ventas, Marketing,
Investigación y Manufactura*. Para cumplir con las regulaciones de la
industria, los usuarios de algunos departamentos no deben comunicarse
con otros departamentos, como se indica en la siguiente tabla:

[TABLE]

Para esta estructura, el plan de Contoso incluye tres políticas de IB:

1.  Una polítia de IB diseñada para evitar que ventas se comunique con
    investigación.

2.  Otra política de IB para evitar que investigación se comunique con
    ventas.

3.  Una política de IB diseñada para permitir que manufactura se
    comunique solo con recursos humanos y marketing.

## Ejercicio 1 – Requisitos previos

### Tarea 1 – Crear un segmento para los usuarios de su organización 

1.  En su VM, ejecute **PowerShell** como administrador.

![BrokenImage](./media/image1.png)



2.  Ejecute lo siguiente:

`Install-Module ExchangeOnlineManagement`

3.  Si aparece el mensaje ‘**Do you want PowerShellGet to install and
    import the NuGet provider now?**’ y ‘**Are you sure you want to
    install the modules from ‘PSGallery’?**’ escriba **y**, después
    presione enter.

![A screenshot of a computer Description automatically
generated](./media/image2.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

4.  Ejecute el siguiente comando una vez finalizada la instalación.

`Import-Module ExchangeOnlineManagement`

![A screenshot of a computer Description automatically
generated](./media/image3.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

5.  Ahora ejecute el siguiente comando para conectarse a Exchange
    Online.

`Connect-IPPSSession`

![A screenshot of a computer Description automatically
generated](./media/image4.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

6.  Inicie sesión con las credenciales de **MOD Administrator** que se
    proporcionan en la página de inicio del entorno de laboratorio.

![BrokenImage](./media/image5.png)


7.  Ejecute el siguiente commando uno por uno en **PowerShell** para
    crear la esctructura organizativa.

`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"`

![BrokenImage](./media/image6.png)


`New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"`

`New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"`

`New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"`

`New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"`

### Tarea 2 – Habilitar búsqueda de directorio limitada (Scoped Directory Search) en Microsoft Teams 

Para activar la búsqueda por nombre

1.  Vaya al centro de administración de Microsoft Teams en
    `https://admin.teams.microsoft.com`, seleccione **Teams** \> **Teams
    settings**.

![A screenshot of a computer Description automatically
generated](./media/image7.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

2.  En **Search by name**, junto a **Scope directory search using an
    Exchange address book policy**, active el botón **On**. Seleccione
    **Save**.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

## Ejercicio 2 – Creación de políticas de Barreras de Información (IB)

### Tarea 1 – Bloquear comunicaciones entre segmentos 

1.  Inicie sesión en `https://purview.microsoft.com/` utilizando las
    credenciales de MOD Administration, proporcionadas en la pestaña
    recursos de su entorno.

2.  En el panel de navegación izquierdo, seleccione **Solutions** \>
    **Information barriers**.

![](./media/image9.png)

3.  En el submenú, seleccione **Policies**. En la página **Policies**,
    seleccione **Create policy** para crear y configurar una nueva
    política de IB.

![A screenshot of a computer Description automatically
generated](./media/image10.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

4.  En la página **Name**, ingrese un nombre para la
    política—`Sales-Research`. A continuación, seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

5.  En la página **Assigned segment**, seleccione **Choose segment**. En
    el panel **On Select assigned segment for this policy**, seleccione
    Sales. Ahora seleccione **Add** para añadir el segment seleccionado
    a la política. Solo puede seleccionar un segmento.

![A screenshot of a computer Description automatically
generated](./media/image12.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

6.  Seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

7.  En **Communication and collaboration**, seleccione **Blocked**.
    Seleccione **Choose segment**, seleccione **Research** y luego
    seleccione **Add.**

![A screenshot of a computer Description automatically
generated](./media/image14.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

8.  En la página **Communication and collaboration**, seleccione el tipo
    de política Blocked en el campo **Communication and collaboration**.
    Seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image15.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

9.  En la página **Policy status**, cambie el estado de la política
    activa a **On**. Seleccione **Next** para continuar.

![BrokenImage](./media/image16.png)


10. En la página **Review your settings**, revise la configuración que
    ha elegido para la política y cualquier sugerencia o advertencia
    para sus selecciones. Seleccione **Edit** para cambiar cualquiera de
    los segmentos y el estado de la política o seleccione **Submit**
    para crear la política.

![BrokenImage](./media/image17.png)



11. Seleccione **Done** una vez creada la política.

![A screenshot of a computer Description automatically
generated](./media/image18.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

### Tarea 2 – Configuración de políticas de Barreras de Información (IB) mediante PowerShell 

1.  En su VM, ejecute **PowerShell** como administrador.

![BrokenImage](./media/image1.png)



2.  Ejecute lo siguiente:

`Import-Module ExchangeOnlineManagement`

![A screenshot of a computer Description automatically
generated](./media/image19.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

3.  Ahora ejecute el siguiente comando para conectarse a Exchange
    Online.

`Connect-IPPSSession`

![A screenshot of a computer Description automatically
generated](./media/image4.png)

Una captura de pantalla de una descripción de ordenador generada
automáticamente

4.  Inicie sesión con las credenciales de **MOD Administrator**
    proporcionadas en la página de recursos del entorno de laboratorio.

5.  Ejecute el siguiente commando para crear una política de IB llamada
    **Research-Sales**. Cuando esta política esté activada y aplicada,
    ayudará a evitar que los usuarios que están en el segment se
    comuniquen con los usuarios del segmento **Sales**.

`New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive`

![BrokenImage](./media/image20.png)



6.  Ejecute el siguiente commando para crear una política de IB llamada,
    **Manufacturing-HRMarketing**. Cuando esta política esté active y se
    aplique, **Manufacturing** solo podrá comunicarse con **HR** y
    **Marketing**. HR y Marketing no tienen restricciones para
    comunicarse con otros segmentos.

`New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive`

![A computer screen shot of a computer program Description automatically
generated](./media/image21.png)

Una captura de pantalla de un programa informático con una descripción
generada automáticamente

7.  Inicie sesión en `https://purview.microsoft.com/` utilizando las
    credenciales **MOD Administration**, proporcionadas en la página de
    inicio de su entorno.

8.  En el panel de navegación izquierdo, seleccione **Information
    barriers** \> **Policies**. En la página **Policies,** podrá ver las
    políticas que hemos creado.

![](./media/image22.png)

## Ejercicio 3 – Aplicar políticas de Barreras de Información (IB)

1.  Inicie sesión en `https://purview.microsoft.com/` utilizando las
    credenciales de MOD Administration, proporcionadas en la pesteña de
    recursos de su entorno.

2.  En en panel de navegación izquierdo, seleccione **Information
    barriers**.

![](./media/image9.png)

3.  En el submenú, seleccione **Policy applications**. Seleccione
    **Apply all policies**.

![](./media/image23.png)

**Resumen:**

En este laboratorio aprendimos a crear los segmentos para implementar
las políticas de IB. Creamos diferentes políticas para crear barreras de
información permitiendo o bloqueando la comunicación y la colaboración
entre diferentes segmentos.
