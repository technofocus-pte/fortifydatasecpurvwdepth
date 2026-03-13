**Laboratorio 8 – Configurar las Information Barriers**

**Introducción**

Contoso cuenta con cinco departamentos: **HR**, **Sales**, **Marketing**, **Research** y **Manufacturing**. Para cumplir con las regulaciones de la industria, los usuarios de algunos departamentos no deben comunicarse con otros departamentos, según se muestra en la siguiente tabla:

| **Segmento** | **Puede comunicarse con** | **No puede comunicarse con** |
|----|----|----|
| HR | Todos | (sin restricciones) |
| Sales | HR, Marketing Manufacturing | Research |
| Marketing | Todos | (sin restricciones) |
| Research | HR, Marketing, Manufacturing | Sales |
| Manufacturing | HR, Marketing | Cualquier otro que no sea HR o Marketing |

Para esta estructura, el plan de Contoso incluye tres políticas de **IB**:

1.  Una política de IB diseñada para evitar que Sales se comunique con Research.

2.  Otra política de IB para evitar que Research se comunique con Sales.

3.  Una política de IB diseñada para permitir que Manufacturing se comunique únicamente con HR y Marketing.

**Objetivos**

- Configurar segmentos de la organización mediante PowerShell para la implementación de **Information Barriers** (IB).

- Habilitar la búsqueda de directorio delimitada en **Microsoft Teams** para aplicar la visibilidad de usuarios según segmentos.

- Crear políticas de **Information Barrier (IB)** mediante el portal de **Microsoft Purview** y PowerShell para controlar la comunicación entre segmentos.

**Ejercicio 1 – Prerrequisitos**

**Tarea 1 – Crear un segmento para los usuarios de su organización**

1.  Haga clic derecho en el ícono de **Windows**, luego navegue y haga clic en **Windows PowerShell (Admin)**. 

> <img src="media/image1.png" style="width:6.26806in;height:5.25764in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  En el cuadro de diálogo **User Account Control**, haga clic en el botón **Yes**.

> <img src="media/image2.png" style="width:6.26806in;height:4.40764in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  Ejecute lo siguiente:

> Install-Module ExchangeOnlineManagement

4.  Si se le solicita ‘**Do you want PowerShellGet to install and import the NuGet provider now?**’ y ‘**Are you sure you want to install the modules from 'PSGallery'?**’ escriba **y** y presione **Enter**.

> <img src="media/image3.png" style="width:6.26806in;height:2.04931in" alt="A screenshot of a computer Description automatically generated" />

5.  Ejecute el siguiente comando:

> Import-Module ExchangeOnlineManagement
>
> <img src="media/image4.png" style="width:6.26806in;height:3.81944in" alt="A screenshot of a computer Description automatically generated" />

6.  Ahora ejecute el siguiente comando para conectarse a **Exchange Online**.

> Connect-IPPSSession
>
> <img src="media/image5.png" style="width:6.26806in;height:3.54236in" alt="A screenshot of a computer Description automatically generated" />

7.  Inicie sesión usando las credenciales de **MOD Administrator** proporcionadas en la página principal del entorno del laboratorio.

> **Nota**: En caso de que aparezca el cuadro de diálogo, **Automatically sign in to all desktop apps and websites on this device?** haga clic en **No, this app only**.
>
> <img src="media/image6.png" style="width:6.26806in;height:6.03542in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image7.png" style="width:6.26806in;height:3.54236in" alt="BrokenImage" />

8.  Ejecute los siguientes comandos uno por uno en **PowerShell** para crear la estructura de la organización.

> New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"
>
> <img src="media/image8.png" style="width:6.26806in;height:4.78472in" alt="BrokenImage" />
>
> New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"
>
> New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"
>
> New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"
>
> New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"

**Tarea 2 – Habilitar la búsqueda de directorio delimitada en Microsoft Teams**

Para activar la búsqueda por nombre:

1.  Vaya al **Microsoft Teams admin center** en https://admin.teams.microsoft.com, seleccione **Teams** \> **Teams settings**.

> <img src="media/image9.png" style="width:6.26806in;height:3.39514in" alt="A screenshot of a computer Description automatically generated" />

2.  En **Search by name**, junto a **Scope directory search using an Exchange address book policy**, active el interruptor (**On**). Seleccione **Save**.

> <img src="media/image10.png" style="width:6.26806in;height:3.39514in" alt="A screenshot of a computer Description automatically generated" />

3.  Si aparece el cuadro de diálogo **Changes might take some time to take effect**, haga clic en el botón **Confirm**.

> <img src="media/image11.png" style="width:6.26806in;height:3.75972in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Ejercicio 2 – Crear políticas de IB**

**Tarea 1 – Bloquear comunicaciones entre segmentos**

1.  En el portal de **Microsoft Purview**, haga clic en **Solutions \> Information barriers**.

> <img src="media/image12.png" style="width:6.26806in;height:3.62431in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  En el panel **Information Barriers**, haga clic en **Policies**, luego seleccione **Policies**. En la página **Policies**, seleccione **+ Create policy** para crear y configurar una nueva política de IB.

> <img src="media/image13.png" style="width:6.26806in;height:3.21042in" alt="A screenshot of a computer AI-generated content may be incorrect." />

3.  En la página **Provide a policy name**, en el campo **Name**, escriba el nombre de la política—Sales-Research. Luego, seleccione **Next**.

> <img src="media/image14.png" style="width:6.26806in;height:3.75208in" alt="A screenshot of a computer AI-generated content may be incorrect." />

4.  En la página **Add assigned segment details**, seleccione **Choose segment**. En el panel **Select assigned segment for this policy**, seleccione **Sales**. Ahora seleccione **Add** para agregar el segmento a la política. Solo puede seleccionar un segmento.

> <img src="media/image15.png" style="width:6.26806in;height:3.70903in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Seleccione **Next**.

> <img src="media/image16.png" style="width:6.26806in;height:3.73958in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  En la página **Configure Communication and collaboration details**, seleccione **Block**. Luego seleccione **Choose segment**, **Research** y **Add**.

> <img src="media/image17.png" style="width:6.26806in;height:3.69792in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image18.png" style="width:6.26806in;height:3.99931in" alt="A screenshot of a computer AI-generated content may be incorrect." />

7.  Luego, haga clic en el botón **Next**.

> <img src="media/image19.png" style="width:6.26806in;height:3.75069in" alt="A screenshot of a computer AI-generated content may be incorrect." />

8.  En la página **Configure Policy status**, active el estado de la política con el interruptor **On**. Seleccione **Next** para continuar.

> <img src="media/image20.png" style="width:6.26806in;height:3.71528in" alt="A screenshot of a computer AI-generated content may be incorrect." />

9.  En la página **Review your settings**, revise la configuración seleccionada para la política y cualquier sugerencia o advertencia. Seleccione **Submit** para crear la política.

> <img src="media/image21.png" style="width:6.26806in;height:3.78194in" alt="A screenshot of a computer AI-generated content may be incorrect." />

10. Una vez creada la política, seleccione **Done**.

> <img src="media/image22.png" style="width:6.26806in;height:3.75486in" alt="A screenshot of a computer AI-generated content may be incorrect." />

11. La política **Sales-Research IB Policy** se creó correctamente.

> <img src="media/image23.png" style="width:6.26806in;height:3.46181in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Tarea 2 – Crear políticas de IB mediante PowerShell**

1.  Regrese a **Administrator: Windows PowerShell** y ejecute el siguiente comando:

> Import-Module ExchangeOnlineManagement
>
> <img src="media/image24.png" style="width:6.26806in;height:2.22917in" alt="A screenshot of a computer AI-generated content may be incorrect." />

2.  Ahora ejecute el siguiente comando para conectarse a **Exchange Online**:

> Connect-IPPSSession
>
> <img src="media/image25.png" style="width:6.26806in;height:1.07917in" alt="A screen shot of a computer AI-generated content may be incorrect." />

3.  Inicie sesión usando las credenciales de **MOD Administrator** proporcionadas en la página principal del entorno del laboratorio.

> **Nota:** En caso de que aparezca el cuadro de diálogo **“Automatically sign in to all desktop apps and websites on this device?”,** haga clic en **No, this app only.**
>
> <img src="media/image6.png" style="width:6.26806in;height:6.03542in" alt="A screenshot of a computer AI-generated content may be incorrect." />
>
> <img src="media/image26.png" style="width:6.26806in;height:2.29306in" alt="A screenshot of a computer program AI-generated content may be incorrect." />

4.  Ejecute el siguiente comando para crear una política de IB llamada **Research-Sales**. Cuando esta política esté activa y aplicada, evitará que los usuarios del segmento **Research** se comuniquen con los usuarios del segmento **Sales**:

> New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive
>
> <img src="media/image27.png" style="width:6.26806in;height:4.13611in" />
>
> <img src="media/image28.png" style="width:6.26806in;height:4.10556in" alt="A screenshot of a computer AI-generated content may be incorrect." />

5.  Ejecute el siguiente comando para crear una política de IB llamada **Manufacturing-HRMarketing**. Cuando esta política esté activa y aplicada, **Manufacturing** podrá comunicarse solo con **HR** y **Marketing**. **HR** y **Marketing** no tienen restricciones para comunicarse con otros segmentos:

> New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive
>
> <img src="media/image29.png" style="width:6.26806in;height:4.14306in" alt="A computer screen shot of a blue screen AI-generated content may be incorrect." />
>
> <img src="media/image30.png" style="width:6.26806in;height:4.11111in" alt="A screenshot of a computer AI-generated content may be incorrect." />

6.  Regrese al portal de **Microsoft Purview**, actualice la página **Information Barriers – Policies**, y podrá ver las políticas creadas mediante PowerShell.

> <img src="media/image31.png" style="width:6.26806in;height:3.71944in" alt="A screenshot of a computer AI-generated content may be incorrect." />

**Resumen**

En este laboratorio, creó segmentos organizacionales (**HR**, **Sales**, **Marketing**, **Research** y **Manufacturing**) utilizando PowerShell y habilitó la búsqueda de directorio delimitada en **Microsoft Teams** para alinear la visibilidad de usuarios con las restricciones por segmentos. Luego configuró políticas de **Information Barriers** en **Microsoft Purview** para bloquear o permitir comunicaciones entre segmentos específicos (por ejemplo, bloquear la comunicación de **Sales** hacia **Research**). Estas políticas se crearon tanto desde el portal como mediante PowerShell para brindar práctica práctica en ambos métodos.
