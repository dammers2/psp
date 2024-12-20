git
    clone <url-repositorio> → copia un repositorio remoto en tu máquina.

    init → inicializa un nuevo repositorio de Git en el directorio actual.

    pull <remoto> <rama> → recupera y fusiona los cambios desde el repositorio remoto a tu rama actual.

    fetch origin <nombre-rama:nombre-rama> → descarga una rama remota específica y la crea localmente con el mismo nombre.

    checkout 
        <nombre-rama> → cambia a la rama especificada.
        -b <nombre-nueva-rama> → crea y cambia a una nueva rama.

    branch → lista las ramas locales o crea una nueva rama.

    merge <nombre-rama-origen> → fusiona la rama especificada en la rama actual.

    branch -d <nombre-rama> → elimina una rama local.

    add 
        <archivo> → añade el archivo especificado al área de preparación.
        <nombre> <url> → añade un nuevo repositorio remoto.

    commit -m "mensaje" → confirma los cambios en el área de preparación con un mensaje descriptivo.

    push 
        origin <rama> → sube los cambios locales a la rama especificada del repositorio remoto.
        -u origin <nombre-nueva-rama> → sube una nueva rama al remoto y configura el seguimiento.
        origin --delete <nombre-rama> → elimina una rama remota.

    rebase <rama> → aplica los cambios de una rama sobre otra, actualizando la base de la rama actual.

    reset <modo> <archivo> → deshace cambios en el área de preparación o el historial.
        - --soft: mantiene los cambios en el área de preparación.
        - --mixed: mantiene los cambios en el directorio de trabajo, pero los elimina del área de preparación.
        - --hard: elimina todos los cambios en el área de preparación y el directorio de trabajo.

    status → muestra el estado de los cambios en tu repositorio.

    log → muestra el historial de commits.
