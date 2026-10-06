# PRD — Mystery Game

- **Versão:** 0.1
- **Status:** Draft inicial
- **Produto:** Nome a definir
- **Categoria:** Jogo social de mistério e dedução
- **Plataforma inicial:** Web responsiva
- **Modelo de desenvolvimento:** Spec-Based Development

## 1. Visão do Produto

O produto é um jogo de investigação baseado em mistérios narrativos nos quais os jogadores recebem apenas uma premissa incompleta e precisam reconstruir os acontecimentos reais através de perguntas.

Cada caso possui uma realidade própria, completa e coerente.

A principal proposta do produto não é possuir uma biblioteca fixa de histórias, mas utilizar um motor procedural de mistérios capaz de gerar novos casos mantendo consistência, causalidade, solucionabilidade e variedade.

O sistema deverá possuir dois modos principais:

* Jogar Solo
* Jogar com Amigos

Embora ambos utilizem o mesmo sistema de geração de casos, possuem experiências de jogo diferentes.

No modo Solo, a IA assume o papel de mestre.

No modo Jogar com Amigos, um jogador humano assume o papel de Host, recebe a história completa e conduz a investigação.

## 2. Proposta de Valor

O produto deve oferecer uma experiência em que:

* cada nova partida possa apresentar um caso diferente;
* o mistério possua uma solução lógica e consistente;
* os jogadores possam investigar através de perguntas;
* o jogo funcione tanto com quanto sem comunicação por voz;
* o modo multiplayer mantenha todos organizados;
* ninguém precise preparar previamente histórias;
* os jogadores alternem naturalmente entre investigar e conduzir casos;
* a IA seja utilizada como infraestrutura narrativa, e não como identidade visual ou protagonista do produto.

## 3. Princípio Central

Cada caso deve possuir uma verdade canônica.

Essa verdade define:

* quem está envolvido;
* o que aconteceu;
* onde aconteceu;
* quando aconteceu;
* por que aconteceu;
* quais eventos causaram outros eventos;
* causa da morte;
* fatos relevantes;
* fatos secundários;
* solução completa.

A premissa é apenas uma pequena representação dessa realidade.

A história completa é a explicação dessa realidade.

## 4. Objetivos do Produto

### 4.1 Objetivo principal

Criar um jogo social de investigação com alto potencial de rejogabilidade, baseado em mistérios proceduralmente gerados.

### 4.2 Objetivos secundários

* estimular raciocínio lógico;
* incentivar interação social;
* permitir partidas curtas ou longas;
* permitir partidas com grupos de tamanhos diferentes;
* evitar repetição excessiva de casos;
* oferecer experiência igualmente funcional com ou sem call;
* permitir expansão futura para diferentes gêneros de mistério.

## 5. Não Objetivos

Na primeira versão, o produto não pretende oferecer:

* chamadas de áudio entre jogadores;
* chamadas de vídeo;
* infraestrutura própria de comunicação por voz;
* transcrição automática de calls externas;
* IA moderando partidas multiplayer;
* IA respondendo perguntas no modo Amigos;
* ranking competitivo complexo;
* moedas virtuais;
* economia interna;
* sistema de XP;
* inventário;
* universo persistente entre histórias;
* personagens controlados pelo jogador;
* elementos de RPG.

## 6. Modos de Jogo

### 6.1 Modo Solo

No modo Solo:

```
Jogador → investiga
IA → atua como mestre
```

A IA:

* apresenta a premissa;
* interpreta perguntas;
* responde;
* acompanha fatos descobertos;
* recebe tentativas de solução;
* determina quando o caso foi solucionado;
* revela a história completa ao final.

As respostas oficiais são:

* SIM
* NÃO
* IRRELEVANTE

O jogador poderá tentar solucionar o caso a qualquer momento.

### 6.2 Modo Jogar com Amigos

No modo Amigos:

```
Jogadores → investigam
Host humano → conduz o caso
IA → somente gera a história
```

Após a geração do caso, a IA não participa mais da rodada.

O Host é responsável por:

* ler a história completa;
* responder perguntas;
* identificar perguntas já respondidas;
* determinar se o mistério foi solucionado;
* encerrar um caso sem solução.

## 7. Estrutura da Sala Multiplayer

Uma sala possui:

* código único;
* criador;
* jogadores;
* ordem de Hosts;
* Host atual;
* caso atual;
* rodada atual;
* chat;
* perguntas;
* respostas;
* histórico da investigação;
* estado atual da partida.

Exemplo:

```
SALA K7PX2

Lucas
Pedro
Ana
Marina
```

## 8. Definição do Host

Cada caso possui exatamente um Host.

O Host:

* conhece a história completa;
* não participa da investigação daquela rodada;
* responde às perguntas;
* possui controles exclusivos.

No chat e na interface, o Host deverá estar permanentemente identificado.

Exemplo:

```
Lucas · HOST
```

ou equivalente visual.

O Host nunca deverá ser confundido com um investigador.

## 9. Sorteio dos Hosts

Quando a partida multiplayer for iniciada, o sistema sorteará aleatoriamente uma ordem entre todos os jogadores.

Exemplo:

```
1. Lucas
2. Marina
3. Ana
4. Pedro
```

Essa ordem será utilizada durante a sessão.

Caso todas as pessoas já tenham sido Host e o grupo continue jogando, a ordem poderá reiniciar.

Não deverá ocorrer um novo sorteio a cada rodada.

## 10. Preparação do Caso

Quando um jogador se torna Host:

1. o sistema gera um novo caso;
2. somente o Host recebe a história completa;
3. os outros jogadores aguardam;
4. o Host lê o caso;
5. o Host confirma que está pronto;
6. a premissa é liberada para todos;
7. a investigação começa.

## 11. Visibilidade do Caso

### Investigadores

Visualizam somente:

* título;
* premissa;
* pergunta central;
* histórico da investigação.

### Host

Pode alternar entre:

**PREMISSA**

e

**HISTÓRIA COMPLETA**

A história completa deverá permanecer inacessível aos demais jogadores durante a investigação.

## 12. Premissa

A premissa deverá permanecer acessível durante toda a investigação.

Exemplo:

> Um homem entra em um apartamento que nunca havia visitado.
>
> Ao olhar pela janela, percebe algo e imediatamente liga para a polícia.
>
> Horas depois, está morto.
>
> O que aconteceu?

Ela não deverá desaparecer ao avançar entre rodadas.

## 13. Estrutura de Investigação por Rodadas

A investigação multiplayer ocorrerá através de Rodadas de Perguntas.

Cada rodada possui duas fases principais:

```
FASE DE PERGUNTAS

↓

FASE DE RESPOSTAS
```

## 14. Fase de Perguntas

Durante essa fase, cada investigador poderá enviar:

**uma pergunta oficial**

por rodada.

Exemplo com quatro investigadores:

```
Ana → 1 pergunta
Pedro → 1 pergunta
Marina → 1 pergunta
João → 1 pergunta
```

O Host não envia pergunta.

## 15. Envio de Perguntas

Cada jogador terá um campo específico:

```
Sua pergunta desta rodada:

[                              ]

[ ENVIAR ]
```

Após enviar:

```
✓ Pergunta enviada
```

O jogador não poderá enviar uma segunda pergunta na mesma rodada.

## 16. Alteração de Pergunta

Enquanto a fase de perguntas permanecer aberta, poderá ser permitido editar a pergunta enviada.

Assim que todos enviarem ou passarem:

```
QUESTÕES BLOQUEADAS
```

Nenhuma alteração adicional poderá ocorrer.

## 17. Passar a Rodada

Um jogador poderá selecionar:

**PASSAR**

caso não tenha pergunta naquela rodada.

Isso evita que uma partida fique bloqueada.

O sistema registra:

```
Pedro
PASSOU
```

Passar conta como participação concluída naquela rodada.

## 18. Status dos Jogadores

Durante a coleta:

```
Ana      ✓
Pedro    ✓
Marina   ○
João     ✓
```

O status deverá indicar somente se cada jogador terminou sua ação.

Não deverá revelar antecipadamente sua pergunta aos demais caso decidamos utilizar submissão fechada por rodada.

## 19. Encerramento da Fase de Perguntas

Quando todos os investigadores:

* enviarem uma pergunta;
* ou passarem;

o estado passa automaticamente para:

```
HOST_RESPONDING
```

As perguntas ficam bloqueadas.

## 20. Fase de Respostas

O Host recebe todas as perguntas da rodada.

Exemplo:

```
RODADA 4

Ana
A vítima conhecia o homem?

[ SIM ]
[ NÃO ]
[ IRRELEVANTE ]
[ JÁ RESPONDIDA ]
```

## 21. Respostas Oficiais

As únicas respostas oficiais sobre o mistério são:

### SIM

A proposição apresentada pelo jogador é verdadeira.

### NÃO

A proposição é falsa.

### IRRELEVANTE

A informação não contribui de maneira relevante para desvendar o caso.

O Host não deve adicionar explicações complementares à resposta oficial.

## 22. Já Respondida

Além das respostas do mistério, o Host possui:

**JÁ RESPONDIDA**

Essa opção não representa uma resposta sobre o caso.

Representa uma relação entre a nova pergunta e uma pergunta anterior.

Exemplo:

```
Rodada 5

Pedro:
Ele já estava ferido quando entrou no carro?

JÁ RESPONDIDA

↳ Rodada 2 — Ana
O ferimento ocorreu antes de ele entrar no carro?

SIM
```

## 23. Regra de Uso de “Já Respondida”

O Host só deverá utilizar essa opção quando tiver 100% de certeza de que uma pergunta anterior já estabelece integralmente a resposta.

Não basta que sejam perguntas semelhantes.

Exemplo:

```
"O carro é importante?"
```

não equivale necessariamente a:

```
"O carro causou a morte?"
```

## 24. Vinculação Obrigatória

Ao selecionar Já Respondida, o Host deverá indicar qual pergunta anterior corresponde àquela informação.

O sistema não permitirá:

```
status = ALREADY_ANSWERED
reference = null
```

Deve obrigatoriamente existir uma referência.

## 25. Publicação das Respostas

O Host deverá responder todas as perguntas da rodada antes da publicação.

Exemplo:

```
4 / 4 respondidas

[ PUBLICAR RESPOSTAS ]
```

As respostas são então disponibilizadas simultaneamente aos jogadores.

Isso impede que uma resposta influencie uma pergunta ainda não finalizada dentro da mesma rodada.

## 26. Histórico da Investigação

Todas as respostas deverão permanecer disponíveis.

Exemplo:

Rodada 1

```
A vítima conhecia o homem?
SIM

O dinheiro era importante?
IRRELEVANTE

Ela morreu dentro da casa?
NÃO
```

Rodada 2

```
O carro teve participação?
SIM

A vítima já estava ferida?
SIM

O ferimento aconteceu dentro do carro?
NÃO
```

Esse histórico representa a memória coletiva da investigação.

## 27. Objetivo do Histórico

Permitir que os jogadores saibam:

* o que já descobriram;
* o que já descartaram;
* quais informações são irrelevantes;
* quais caminhos já foram investigados;
* quais perguntas não devem ser repetidas.

O sistema não precisa interpretar automaticamente o progresso no modo Amigos.

## 28. Chat da Sala

O modo Amigos poderá possuir um chat de discussão.

O chat será separado logicamente do sistema oficial de perguntas.

### Chat

Serve para:

* discutir;
* formular teorias;
* sugerir perguntas;
* conversar.

### Campo oficial da rodada

Serve exclusivamente para:

* enviar a pergunta que será respondida pelo Host.

## 29. Comunicação por Voz

O produto não terá chat de voz próprio no modo Amigos.

Jogadores poderão utilizar:

* Discord;
* WhatsApp;
* Google Meet;
* outras plataformas;
* comunicação presencial.

Isso é externo ao jogo.

## 30. Regra Fundamental de Consistência

A utilização de uma call externa não pode alterar nenhuma regra do jogo.

Com voz ou sem voz, o fluxo é sempre:

```
Premissa
↓
Discussão
↓
Pergunta da rodada
↓
Todos enviam
↓
Host responde
↓
Respostas são publicadas
↓
Nova rodada
```

A call é apenas uma forma alternativa de discussão.

## 31. Tentativa de Solução

Durante a investigação, um jogador poderá utilizar:

**DESVENDAR MISTÉRIO**

Essa ação é diferente de uma pergunta.

O jogador apresenta sua hipótese completa.

## 32. Avaliação da Solução — Amigos

A avaliação é feita exclusivamente pelo Host humano.

O Host possui:

```
CONTINUAR INVESTIGAÇÃO

ou

MISTÉRIO SOLUCIONADO
```

Caso a hipótese esteja incorreta, a investigação continua.

Caso esteja correta, a rodada termina.

## 33. Mistério Solucionado

Quando alguém desvendar:

o Host seleciona:

**MISTÉRIO SOLUCIONADO**

Opcionalmente poderá identificar:

* jogador responsável;
* grupo inteiro.

O caso entra no estado:

```
SOLVED
```

## 34. Caso sem Solução

Se o grupo decidir desistir, o Host poderá selecionar:

**ENCERRAR SEM SOLUÇÃO**

Será apresentada uma confirmação antes da finalização.

Exemplo:

```
Encerrar este caso?

Os jogadores não poderão mais
enviar perguntas.

A solução será revelada.

[ VOLTAR ]

[ ENCERRAR ]
```

O caso entra no estado:

```
UNSOLVED
```

## 35. Revelação

Independentemente do motivo:

```
SOLVED
```

ou

```
UNSOLVED
```

a história completa deverá ser revelada para todos.

## 36. Tela de Revelação

Deverá mostrar:

* título;
* premissa;
* história completa;
* explicação;
* resultado;
* número de rodadas;
* quantidade de perguntas;
* jogador que solucionou, quando aplicável.

## 37. Próximo Host

Depois da revelação:

```
PRÓXIMO HOST

Marina
```

O sistema avança para o próximo jogador da ordem previamente sorteada.

Um novo caso é gerado.

## 38. Máquina de Estados — Amigos

```
LOBBY
  ↓
HOST_SELECTION
  ↓
GENERATING_CASE
  ↓
HOST_READING
  ↓
QUESTION_COLLECTION
  ↓
HOST_ANSWERING
  ↓
ROUND_RESULTS
  ↓
QUESTION_COLLECTION
  ↓
...
  ↓
SOLVED / UNSOLVED
  ↓
REVEALED
  ↓
NEXT_HOST
```

## 39. Máquina de Estados — Rodada

```
OPEN
 ↓
COLLECTING_QUESTIONS
 ↓
LOCKED
 ↓
HOST_ANSWERING
 ↓
ANSWERS_READY
 ↓
PUBLISHED
 ↓
FINISHED
```

## 40. Modo Solo

O modo Solo utiliza o mesmo gerador de casos, porém elimina o Host humano.

Fluxo:

```
Gerar caso
↓
Mostrar premissa
↓
Jogador pergunta
↓
IA interpreta
↓
SIM / NÃO / IRRELEVANTE
↓
Jogador continua investigando
↓
Tentativa de solução
↓
IA avalia
↓
Caso solucionado ou investigação continua
```

## 41. Histórico Solo

As perguntas anteriores devem permanecer disponíveis.

Exemplo:

```
Ele conhecia a vítima?
SIM

O carro causou a morte?
NÃO

A cor da roupa importa?
IRRELEVANTE
```

## 42. Fact Discovery — Solo

Internamente, o sistema poderá acompanhar fatos do Canon descobertos pelo jogador.

Esse mecanismo não precisa ser visível diretamente.

Ele servirá para:

* avaliar progresso;
* identificar solução;
* evitar inconsistências;
* gerar pistas futuramente.

## 43. Tentativa de Solução — Solo

O jogador poderá enviar uma explicação completa.

A IA deverá avaliar contra os fatos críticos do Canon.

Resultados possíveis:

```
INCORRETO
PARCIAL
QUASE COMPLETO
RESOLVIDO
```

A interface não precisa mostrar percentuais.

## 44. Canon

Todo caso deverá possuir uma representação estruturada.

Exemplo conceitual:

```json
{
  "title": "",
  "premise": "",
  "victim": {},
  "characters": [],
  "location": {},
  "objects": [],
  "timeline": [],
  "causal_chain": [],
  "critical_facts": [],
  "supporting_facts": [],
  "solution": {},
  "full_story": ""
}
```

## 45. Regra de Imutabilidade do Canon

Depois que o caso entrar em jogo:

nenhum componente poderá alterar fatos do Canon.

No modo Solo, a IA interpreta o Canon.

Ela não pode inventar fatos adicionais durante a investigação.

## 46. Gerador Procedural

O gerador deverá criar:

* contexto;
* personagens;
* ambiente;
* eventos;
* relações;
* objetos;
* cadeia causal;
* causa da morte;
* twist;
* solução;
* premissa.

O sistema deve preferencialmente gerar primeiro uma estrutura lógica e depois produzir a narrativa.

## 47. Cadeia Causal

Todo caso deverá possuir algum formato de causalidade:

```
CONDIÇÃO
↓
EVENTO
↓
DECISÃO
↓
CONSEQUÊNCIA
↓
MORTE
```

A solução precisa explicar essa cadeia.

## 48. Validação dos Casos

Antes de um caso ser liberado, deverá ser possível verificar:

* existe solução;
* existe causa coerente;
* não há contradições;
* fatos críticos são suficientes;
* premissa não entrega a resposta;
* premissa contém informação suficiente;
* solução corresponde ao Canon;
* caso não é excessivamente parecido com outro recente.

## 49. Originalidade dos Casos

O sistema deverá tentar evitar casos estruturalmente repetidos.

A comparação poderá considerar:

* causa da morte;
* cenário;
* mecanismo;
* objeto central;
* twist;
* estrutura causal;
* similaridade semântica da solução.

## 50. UX — Princípios

A interface não deverá possuir estética genérica associada a produtos de IA.

Evitar:

* gradientes roxo/azul clichês;
* estrelas de IA;
* elementos excessivamente futuristas;
* glassmorphism genérico;
* dashboards corporativos;
* aparência de chatbot;
* excesso de cards sem hierarquia.

## 51. Direção de Experiência

A interface deverá transmitir:

* investigação
* mistério
* documentação
* descoberta
* tensão

Sem cair necessariamente em clichês policiais.

Direção conceitual:

```
Editorial investigativo
+
Dossiê contemporâneo
+
Jogo social
```

## 52. Princípio de UX Fundamental

A dificuldade deve estar no mistério, e não no uso do aplicativo.

O jogador nunca deve precisar gastar esforço entendendo como operar a interface enquanto tenta solucionar o caso.

## 53. Hierarquia da Tela de Investigação

A tela deverá priorizar:

1. premissa;
2. rodada atual;
3. ação do jogador;
4. histórico;
5. discussão.

O chat não deverá superar visualmente o próprio mistério.

## 54. Host — UX

O Host deverá possuir identidade visual clara.

Ele deve perceber imediatamente:

```
VOCÊ É O HOST
```

Sua interface deverá conter:

* premissa;
* história completa;
* perguntas;
* respostas;
* histórico;
* controles de encerramento.

## 55. Segurança da História Completa

A história completa não deverá simplesmente ser escondida visualmente no frontend.

Jogadores que não forem Host não deverão receber esse conteúdo enquanto o caso estiver ativo.

## 56. Stack Inicial Recomendada

### Frontend

* Next.js
* React
* TypeScript
* Tailwind CSS
* shadcn/ui ou componentes próprios

### Backend e dados

* Supabase
* PostgreSQL
* Supabase Auth
* Supabase Realtime
* Row Level Security

### IA

* OpenAI API
* Structured Outputs
* JSON Schema

### Similaridade

* pgvector

### Testes

* Vitest
* Playwright

### Deploy

* Vercel
* Supabase

## 57. Regra Arquitetural

PostgreSQL deverá ser a fonte oficial do estado.

Realtime apenas distribui alterações.

```
AÇÃO
↓
VALIDAÇÃO
↓
BANCO
↓
TRANSAÇÃO
↓
REALTIME
↓
CLIENTES
```

Nenhuma regra crítica da partida poderá existir exclusivamente no frontend.

## 58. Entidades Principais

Inicialmente:

```
users
profiles

rooms
room_players
host_orders

cases
case_private_data

game_sessions
game_rounds

round_questions
round_answers

chat_messages

game_results
```

## 59. Restrições Importantes

O backend deverá garantir:

* uma pergunta por jogador por rodada;
* Host não envia pergunta;
* apenas Host responde;
* apenas Host encerra o caso;
* somente jogadores da sala recebem atualizações;
* somente Host acessa a história completa;
* “Já respondida” exige referência anterior;
* rodada não pode publicar respostas incompletas;
* respostas publicadas não podem ser alteradas livremente;
* próximo Host segue a ordem definida.

## 60. Telas Principais

### Geral

1. Splash
2. Login
3. Cadastro
4. Perfil inicial
5. Home

### Amigos

6. Criar/entrar em sala
7. Configurar sala
8. Lobby
9. Ordem dos Hosts
10. Host lendo caso
11. Jogadores aguardando
12. Investigação — jogador
13. Investigação — Host
14. Envio de pergunta
15. Espera das perguntas
16. Host respondendo
17. “Já respondida”
18. Resultado da rodada
19. Histórico
20. Chat
21. Tentativa de solução
22. Solução confirmada
23. Caso sem solução
24. Revelação
25. Próximo Host
26. Resultado da sessão

### Solo

27. Configuração Solo
28. Gerando mistério
29. Investigação
30. Histórico
31. Tentativa de solução
32. Solução parcial
33. Mistério resolvido
34. Desistência
35. Revelação

### Conta

36. Perfil
37. Histórico de partidas
38. Configurações

## 61. MVP

O MVP deverá priorizar o modo Amigos.

### MVP 1

* autenticação;
* criação de sala;
* entrada por código;
* lobby;
* sorteio de Host;
* geração de um caso;
* premissa;
* história completa exclusiva do Host;
* sistema de rodadas;
* uma pergunta por jogador;
* respostas SIM/NÃO/IRRELEVANTE;
* Já respondida;
* histórico;
* chat;
* Mistério Solucionado;
* Caso sem Solução;
* revelação;
* rotação do Host.

## 62. Pós-MVP

Depois do modo Amigos estabilizado:

* modo Solo;
* Fact Discovery Engine;
* avaliação automática de solução;
* dificuldade automática;
* mecanismos avançados de geração;
* embeddings;
* controle de similaridade;
* pistas;
* categorias;
* temas;
* estatísticas avançadas;
* personalização.

## 63. Métricas de Produto

Métricas iniciais importantes:

* partidas criadas;
* salas efetivamente iniciadas;
* casos jogados por sessão;
* número médio de jogadores;
* número médio de rodadas;
* perguntas por caso;
* percentual de casos solucionados;
* percentual de desistência;
* tempo médio por caso;
* quantidade de novos casos iniciados após uma revelação;
* retorno de jogadores.

A principal métrica qualitativa deverá ser:

> “Depois que um caso termina, o grupo quer jogar outro?”

## 64. Critérios de Sucesso do MVP

O MVP será considerado funcional quando um grupo conseguir:

1. criar uma sala;
2. entrar na sala;
3. iniciar uma sessão;
4. receber um Host;
5. gerar um mistério;
6. liberar a premissa;
7. realizar várias rodadas;
8. registrar perguntas;
9. receber respostas;
10. consultar o histórico;
11. discutir pelo chat ou externamente;
12. solucionar ou desistir;
13. revelar a história;
14. trocar de Host;
15. iniciar outro caso;

sem necessidade de intervenção externa.

## 65. Princípios Não Negociáveis

### P01 — Canon é verdade

O Canon é a fonte definitiva do caso.

### P02 — IA não improvisa realidade

A IA não pode alterar fatos depois da geração.

### P03 — Multiplayer é humano

No modo Amigos, a IA gera o caso e sai da investigação.

### P04 — Mesmo jogo com ou sem call

Comunicação externa nunca altera o fluxo.

### P05 — Investigação estruturada

Uma pergunta por investigador a cada rodada.

### P06 — Respostas persistentes

Tudo que foi oficialmente respondido permanece acessível.

### P07 — Host é autoridade da rodada

O Host decide respostas e conclusão.

### P08 — Solução sempre revelada

Todo caso encerrado termina com a história completa.

### P09 — Segurança real

Informação secreta não deve chegar a quem não possui autorização.

### P10 — Identidade própria

A experiência visual não deverá parecer um produto genérico de IA.

## 66. Visão de Longo Prazo

O mesmo motor poderá futuramente suportar diferentes categorias:

* mortes misteriosas;
* crimes;
* acontecimentos inexplicáveis;
* situações absurdas;
* suspense;
* ficção científica;
* sobrenatural;
* mistérios históricos;
* humor;
* ambientes corporativos.

O objetivo de longo prazo não é construir uma coleção de enigmas.

É construir um Mystery Engine capaz de produzir mundos investigáveis de forma procedural, coerente e reutilizável.

## 67. Definição Resumida do Produto

Um jogo social de investigação no qual cada caso nasce com uma realidade própria. Os jogadores recebem apenas uma premissa e precisam reconstruir os acontecimentos através de perguntas. No modo Amigos, um Host humano conduz cada caso em rodadas estruturadas. No modo Solo, uma IA assume o papel de mestre. Ao final, a realidade completa do mistério é revelada.
