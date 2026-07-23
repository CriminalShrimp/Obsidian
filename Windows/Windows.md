**Sumário**
	**Tags:** #Windows
	**Conteúdo:**
	
----


# HIDS

Os logs de host do Microsoft Windows são visíveis localmente pelo Visualizador de Eventos. O Visualizador de Eventos mantém cinco tipos de logs:

- **Logs de aplicativos** — Eles contêm eventos registrados por vários aplicativos.
- **Registros do sistema** — Isso inclui eventos relacionados à operação de drivers, processos e hardware.
- **Registros de instalação** — Estes registram informações sobre a instalação de software, incluindo atualizações do Windows.
- **Registros de segurança** — Esses eventos registram relacionados à segurança, como tentativas de logon e operações relacionadas ao gerenciamento e acesso de arquivos ou objetos.
- **Logs da linha de comando** - Os invasores que obtiveram acesso a um sistema e alguns tipos de malware executam comandos via CLI em vez de uma GUI. A execução da linha de comando em log fornecerá visibilidade para esse tipo de incidente.

Vários logs podem ter diferentes tipos de eventos. Os logs de segurança consistem apenas em mensagens de falha ou êxito de auditoria. Em computadores Windows, o log de segurança é realizado pelo Local Security Authority Subsystem Service (LSASS), que também é responsável por impor diretivas de segurança em um host Windows. O LSASS é executado como lsass.exe. Ele é frequentemente falsificado por malware. Ele deve estar sendo executado a partir do diretório System32 do Windows. Se um arquivo com esse nome, ou um nome camuflado, como 1sass.exe, estiver em execução ou em execução a partir de outro diretório, ele pode ser malware.

Os Eventos do Windows são identificados por números de ID e descrições breves. Uma enciclopédia de IDs de eventos de segurança, algumas com detalhes adicionais, está disponível no Ultimate Windows Security na Web. A tabela explica o significado dos cinco tipos de eventos de log de host do Windows.

|Tipo de evento|Descrição|
|---|---|
|Erro|Um erro é um evento que indica um problema significativo, como perda de dados ou perda de funcionalidade. Por exemplo, se um serviço falhar ao carregar durante a inicialização, um evento de erro será registrado.|
|Aviso|Um aviso é um evento que não é necessariamente significativo, mas pode indicar um possível problema futuro. Por exemplo, quando o espaço em disco é baixo, um evento de aviso é registrado. Se um aplicativo pode se recuperar de um evento sem perda de funcionalidade ou dados, ele geralmente pode classificar o evento como um evento de aviso.|
|Informações|Um evento informativo descreve a operação bem-sucedida de um aplicativo, driver ou serviço. Por exemplo, quando um driver de rede é carregado com êxito, pode ser apropriado registrar um evento de informações. Observe que geralmente é inapropriado para um aplicativo de área de trabalho registrar um evento cada vez que ele é iniciado.|
|Sucesso na Auditoria|Uma auditoria bem-sucedida é um evento que registra uma tentativa de acesso de segurança auditada com êxito. For example, a user's successful attempt to log on to the system is logged as a success audit event.|
|Falha ne Auditoria|Uma auditoria de falha é um evento que registra uma tentativa de acesso de segurança auditada que falha. Por exemplo, se um usuário tentar acessar uma unidade de rede e falhar, a tentativa é registrada como um evento de auditoria de falha.|
