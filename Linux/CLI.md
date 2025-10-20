Tags: #Linux #Tips

# Introdução

CLI esta presente em praticamente todos software, e nele é possível fazer coisas de formar mais eficaz que por interface gráfica. Um site que com vir a ser útil é o [explainshell.com](https://explainshell.com/), ele oferece uma explicação detalhada sobre cada parte do comando que esta sendo realizado. 

Comumente a CLI vai apresentar a seguinte composição de elementos:
<p style="text-align:center;">[<span style="color:rgb(255, 0, 0)"> usuario</span>@<span style="color:rgb(0, 176, 240)">sistema</span> <span style="color:rgb(255, 192, 0)"><span style="color:rgb(255, 192, 0)"><span style="color:rgb(0, 176, 80)">~</span></span></span>] <span style="color:rgb(255, 192, 0)">$</span></p>
<span style="color:rgb(255, 0, 0)">Se refere ao nome do usuário em que esta logado.</span>

<span style="color:rgb(0, 176, 240)">Sistema em que esta logado.</span>

<span style="color:rgb(0, 176, 80)">Já esse campo representa o diretório em que esta sendo acessado, o símbolo ~ se refere a o home do usuário.</span>

<span style="color:rgb(255, 192, 0)">Esse campo pode mudar entre $ e #, sendo que quando aparece o símbolo # significa que o usuário esta com privilégios, já o $ significa que é um usuário "padrão".</span>

Na hora de realizar comandos na CLI a seguinte sintaxe deve ser seguida:
<p style="text-align:center;"><span style="color:rgb(255, 0, 0)"> comando</span> [<span style="color:rgb(0, 176, 240)">opção(ou opções)</span>] [<span style="color:rgb(0, 176, 80)">argumentos</span>]</p>
<span style="color:rgb(255, 0, 0)">O comando pode ter ou não os campos opção e argumentos, isso varia conforme a o resultado desejado.</span> 

<span style="color:rgb(0, 176, 240)">Logo em seguida vem as opções que podem ser mais que uma, quando vamos usar uma opção ela vem antecedida com um - ou dois --, quando usado com somente um - significa que estamos usando a abreviação de um palavra, já quando contem dois -- tudo é tratado como uma palavra.</span> 

# Monitoring Processes on the Command Line

On the command line, you can list all active processes by using the `top` command.

The `top` command launches an interactive application that runs in the terminal, so there is no command prompt after starting it. Instead, the Terminal window displays a list of processes by PID, CPU percentage, RAM usage, name, and other attributes.

top - 22:09:52 up  3:16,  1 user,  load average: 0.00, 0.00, 0.00
Tasks: 125 total,   1 running, 124 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.2 sy,  0.0 ni, 99.7 id,  0.0 wa,  0.0 hi,  0.2 si,  0.0 st
MiB Mem :   1770.8 total,   1232.2 free,    411.8 used,    280.7 buff/cache
MiB Swap:      0.0 total,      0.0 free,      0.0 used.   1359.0 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
      1 root      20   0  106300  15896  10360 S   0.0   0.9   0:01.83 systemd
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.01 kthreadd
      3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_par_gp
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 netns
      7 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/0:0H-events_highpri
      9 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 mm_percpu_wq
     11 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_kthre
     12 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_rude
[...]

The list updates regularly, depending on how it is sorted. By default, the process list is sorted by CPU percentage. To make the sort column bold, press **x** on your keyboard. To change the designated sort column, press the less than symbol (`<`) or the greater than symbol (`>`) on your keyboard. Press **R** to reverse the sort order.

To exit the `top` command and return to a command prompt, press **q**.

#### Stopping a Process on the Command Line

You can use the `top` interface to stop a process, but first you must determine the ID for the process that you intend to stop.

In the `top` interface, press **L** on your keyboard. Interactive prompts in the `top` interface appear above the column labels.

top - 22:09:52 up  3:16,  1 user,  load average: 0.00, 0.00, 0.00
Tasks: 125 total,   1 running, 124 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.2 sy,  0.0 ni, 99.7 id,  0.0 wa,  0.0 hi,  0.2 si,  0.0 st
MiB Mem :   1770.8 total,   1232.2 free,    411.8 used,    280.7 buff/cache
MiB Swap:      0.0 total,      0.0 free,      0.0 used.   1359.0 avail Mem
**`Locate string`**
    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND

Type the name of the process that you want to stop after the `Locate string` prompt, and then press **Enter**. The `top` interface is updated to display any matches for your search term. Review the list of matches for the process that you want to stop, and take note of its PID.

To stop the process, press **k** on your keyboard. Enter the PID of the process into the `top` prompt and then press **Enter**.


Press **Enter** again when the `top` command prompts you for the signal to send.

You can also use the `kill` command to terminate a process. The `kill` command is not an interactive utility so you must provide the ID of the process to terminate. In the following example you terminate the process with the ID of 7460.

[user@host ~]$ **`kill 7460`**

#### Finding a Process ID on the Command Line

You can retrieve a PID without launching the `top` command by using the `pgrep` command.

[user@host ~]$ **`pgrep gedit`**
3680

You can view processes noninteractively by using the `ps` command with the `-e` option to include every running process, and the `-f` option to mimic the layout of the `top` interface. Because there are hundreds of lines of output, you can pipe the output to the `less` command so that you can scroll through it. To exit the `less` command before the end of the list, press **q** on your keyboard.

[user@host ~]$ **`ps -ef | less`**
UID   PID  PPID  C STIME TTY       TIME CMD
root    1     0  0 18:53 ?     00:00:01 /usr/lib/systemd/systemd...
root    2     0  0 18:53 ?     00:00:00 [kthreadd]
root    3     2  0 18:53 ?     00:00:00 [rcu_gp]
root    4     2  0 18:53 ?     00:00:00 [rcu_par_gp]
root    5     2  0 18:53 ?     00:00:00 [netns]
root    7     2  0 18:53 ?     00:00:00 [kworker/0:0H-events_highpri]
root    9     2  0 18:53 ?     00:00:00 [mm_percpu_wq]
root   11     2  0 18:53 ?     00:00:00 [rcu_tasks_kthre]
root   12     2  0 18:53 ?     00:00:00 [rcu_tasks_rude_]
root   13     2  0 18:53 ?     00:00:00 [rcu_tasks_trace]
[...]
# Comandos 
#Comandos 
###### find  - falar sobre 
###### timedatectl - 
###### pwd - **P**rint **W**orking **D**irectory mostra o<span style="color:rgb(255, 255, 0)"> caminho de pastas</span> e arquivos ate chegar onde o usuário esta trabalhando.
###### ps aux - 
###### top - 
###### htop - 