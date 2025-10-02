1. Qual a diferença entre programa e processo?

Um programa é só um arquivo com código, algo estático que está salvo no disco. Já um processo é esse programa em execução. Ele está "vivo", usa CPU, memória e interage com o sistema. Então, processo é o programa em ação.

2. Quais são os estados de um processo e quando ocorrem as transições?

Os principais estados são:

Novo: quando o processo está sendo criado.

Pronto: esperando a vez para usar a CPU.

Executando: quando está rodando de fato.

Esperando: quando está aguardando algo (como leitura de disco).

Finalizado: terminou a execução.

As transições acontecem, por exemplo, quando um processo começa a rodar, é interrompido, finaliza ou precisa esperar por algo.

3. O que contém um Process Control Block (PCB)?

O PCB guarda todas as informações importantes sobre um processo, tipo:

O ID do processo (PID),

Em que estado ele está,

Registradores da CPU,

Info de memória,

Arquivos abertos,

Informações de segurança.

É basicamente o que o sistema usa pra "lembrar" de cada processo.

4. O que acontece com os recursos de um processo quando ele termina?

Quando um processo finaliza, o sistema libera os recursos que ele estava usando, como memória, arquivos abertos, etc. Isso é importante pra evitar vazamentos de memória e deixar esses recursos disponíveis pra outros processos.

5. Qual a diferença entre fork() e exec() no UNIX?

O fork() cria um novo processo copiando o processo atual (pai). Já o exec() serve pra trocar o código que está rodando no processo por outro programa. Normalmente se usa os dois juntos: fork() cria o filho, e o exec() faz esse filho rodar outra coisa.

6. Como funciona a hierarquia de processos em UNIX?

No UNIX, os processos formam uma espécie de árvore. Tem um processo inicial (geralmente o init ou systemd) que é o pai de todos os outros. Quando um processo usa fork() pra criar outro, ele vira o pai daquele novo processo.

7. Compare memória compartilhada e troca de mensagens (IPC).

Memória compartilhada: os processos usam uma área comum da memória pra se comunicar. É rápido, mas tem que cuidar com sincronização (pra não dar conflito).

Troca de mensagens: os processos enviam e recebem mensagens entre si. É mais simples e seguro, mas mais lento que a memória compartilhada.

8. Cite exemplos de chamadas de sistema usadas em IPC.

Algumas chamadas usadas são:

pipe()

shmget(), shmat() (pra memória compartilhada)

msgget(), msgsnd(), msgrcv() (pra filas de mensagens)

socket(), send(), recv() (pra comunicação em rede)

10. Por que é importante que o sistema operacional faça gerenciamento de processos?

Porque sem isso seria um caos. O SO precisa controlar quem está rodando, quem espera, evitar que dois processos usem o mesmo recurso ao mesmo tempo, etc. É isso que garante que o sistema funcione bem e que vários programas possam rodar ao mesmo tempo.

11. Explique a diferença entre processos independentes e processos cooperativos.

Independentes: não se comunicam nem compartilham nada entre si.

Cooperativos: trocam dados, compartilham recursos e precisam se sincronizar.

Processos cooperativos geralmente são mais eficientes, mas também mais difíceis de controlar.

12. O que é um processo zumbi em UNIX/Linux?

É um processo que já terminou, mas ainda está na tabela de processos porque o pai ainda não leu seu status (com wait(), por exemplo). Ele fica "preso" ali até o pai pegar essa informação. Não consome CPU, mas ocupa espaço na tabela.

13. Explique a diferença entre chamadas bloqueantes e não bloqueantes em IPC.

Bloqueante: o processo espera até que a operação termine (por exemplo, esperar uma mensagem chegar).

Não bloqueante: o processo tenta fazer a operação e, se não der, segue em frente sem esperar.

Chamadas não bloqueantes são boas pra não travar o programa, mas podem ser mais difíceis de lidar.

14. Qual a diferença entre processo pesado (process) e thread (processo leve)?

Um processo tem seu próprio espaço de memória, recursos, etc. Já uma thread compartilha esses recursos com outras threads do mesmo processo. Threads são mais leves e rápidas, ideais pra tarefas simultâneas dentro do mesmo programa.

15. Por que sistemas operacionais multiprogramados precisam de troca de contexto (context switch)?

Porque vários processos dividem a CPU. O SO precisa salvar o estado de um processo e carregar o de outro pra que eles possam se revezar usando a CPU. Isso é a troca de contexto.

16. Cite vantagens e desvantagens da comunicação via memória compartilhada.

Vantagens:

Muito rápida

Boa pra grande volume de dados

Desvantagens:

Precisa de controle de concorrência (como semáforos)

Pode ser mais difícil de implementar corretamente
