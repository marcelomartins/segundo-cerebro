# Segundo Cérebro Digital

Memória operacional para agentes de IA em arquivos Markdown locais. **Versão 1.3.0.**

Você conversa normalmente; o agente registra ações, promessas, decisões e contexto útil nos arquivos certos. A memória fica sob seu controle e pode ser consultada em outra sessão ou por outro agente com acesso ao vault.

## Onde olhar

**FOCUS.md reúne tudo que precisa da sua atenção.** Ações de projetos, tarefas avulsas, lembretes e acompanhamentos ficam nesse único arquivo, com uma entrada por ação. Ele pode conter 100 ou mais itens, sem esconder ou descartar ações para encurtar a lista.

- **Agora:** até três ações destacadas para execução imediata, organizadas por tópico quando necessário.
- **Demais ações por tópico:** todas as outras ações abertas, sem limite de quantidade.

Ao priorizar, o agente move a entrada de lugar, preservando o ID. A mesma ação não é copiada para outra seção. Bloqueios e dependências ficam junto dela. As fichas dos projetos apontam para suas ações no FOCUS e guardam contexto, estado e histórico.

**COMMITMENTS.md registra promessas assumidas**, com prazo, responsável e origem. Ele abre com uma tabela; cada compromisso tem uma linha e um complemento com campos distintos. A execução ou o acompanhamento necessário aparece no FOCUS, ligado ao compromisso. Lembrete pessoal não vira promessa automaticamente.

Você olha o FOCUS para saber o que fazer; consulta as referências quando precisar dos detalhes.

## Como o agente opera

Antes de cada comando ou resposta, o agente relê AGENTS.md do disco e revisa FOCUS.md inteiro e COMMITMENTS.md. Isso vale para consultas, lembretes, adições em qualquer pasta e rotinas automáticas. Antes de encerrar, ele revisa novamente os dois painéis e consolida o novo contexto sobre os arquivos mais recentes.

Reenvio do mesmo lembrete complementa o registro existente. Mudanças preexistentes são preservadas. Uma consulta sem alteração não gera escrita artificial.

AGENTS.md contém o núcleo obrigatório, com teto de 80 linhas e 900 palavras. Detalhes ficam em operacao.md e são consultados por necessidade; modelos completos ficam em Templates/. Os arquivos de uso mostram a informação primeiro e apenas uma referência curta ao protocolo no rodapé.

## Como instalar

1. Escolha uma pasta para o vault e seu caminho absoluto final.
2. Abra um agente com leitura e escrita nessa pasta.
3. Entregue o [INSTALL.md](INSTALL.md) e o [prompt de instalação](PROMPT_TO_INSTALL.md), preenchido com raiz e fuso.
4. Responda à calibração mínima: papel/contexto, o que precisa de atenção agora, compromissos conhecidos e fuso.
5. Confira o relatório, que separa estrutura, calibração mínima, personalização e agendamento.

Pode também pedir diretamente:

```text
Execute a instalação de @INSTALL.md nesta pasta. Git em modo auto.
```

A personalização é progressiva. Objetivos, preferências detalhadas, pessoas, clientes e áreas são registrados conforme surgem; não é preciso preencher um cadastro extenso para começar. Ausência confirmada é diferente de informação ainda não levantada.

Em um vault com versão anterior ou desconhecida, o instalador apresenta um plano de migração. A migração preserva dados e personalizações, reúne as ações no FOCUS e atualiza links antes de marcar a versão como atualizada.

## Projetos que crescem com o trabalho

Um projeto começa com **PROJECT.md**, contendo contexto, estado, histórico curto e referências às ações do FOCUS e aos compromissos. Tarefa simples não exige criar projeto.

- **LOG.md** nasce quando o histórico faz a ficha ultrapassar aproximadamente 100 linhas. O histórico é transferido com suas referências.
- **ARTIFACTS.md** nasce com o primeiro artefato real que precise ser indexado.
- Links para esses arquivos só aparecem depois que eles existem.

Projetos antigos que já possuem os três arquivos são preservados. A regra reduz a estrutura inicial sem apagar histórico existente.

## O que vira memória

Registre ações, compromissos, decisões, preferências duradouras, mudanças relevantes e aprendizados reutilizáveis. Um pedido explícito para guardar algo prevalece sobre o filtro de utilidade.

Cumprimentos, conversa passageira e hipóteses ocasionais não geram fichas permanentes por padrão. Capturas brutas são preservadas quando solicitadas ou necessárias como origem; a conversa inteira não é copiada automaticamente.

Fatos relevantes mantêm origem e data de registro. Relato de terceiro e inferência permanecem identificados. Uma **correção de erro** marca o registro anterior como incorreto; uma **mudança real** preserva o que era verdadeiro e o período conhecido. Não se inventa data de mudança, e atualizar uma nota não significa confirmar todos os fatos nela.

## Datas

- Metadados técnicos de data no YAML usam **AAAA-MM-DD**; valores desconhecidos usam `null`.
- Conteúdo humano, tabela de compromissos, datas planejadas no FOCUS e históricos usam **DD/MM/AAAA**, com HH:MM quando necessário.
- Nomes datados usam AAAA-MM-DD em subpastas AAAA-MM.
- Capturas literais preservam o formato recebido. Datas relativas são consolidadas no fuso confirmado.

Não se cria outra cópia ISO do prazo do COMMITMENTS: a tabela humana continua sendo sua fonte.

## Rotinas e Git

A consolidação diária continua às **23h no fuso confirmado**, com o procedimento integral de rotinas.md. A instalação deve configurar um mecanismo real disponível no ambiente e verificar executor, identificador, próxima execução e teste. Criar agendamento.md ou apenas um lembrete não instala essa rotina.

Se não houver capacidade de configurar, o relatório indica a pendência, o responsável e o passo concreto. O vault pode ser usado manualmente enquanto isso é resolvido. Revisão semanal e auditoria mensal continuam disponíveis quando solicitadas.

Git é opcional: modo auto verifica sua existência e a raiz própria; off desativa. Somente com Git ativo a instalação cria versionamento.md e habilita a extensão no rodapé do AGENTS. Sem Git, o Daily é a trilha de mudanças e os arquivos comuns não contêm regras de commit. Não há executor adicional para impor o protocolo a cada comando.

## Estrutura

| Camada | Arquivos/pastas | Função |
|---|---|---|
| Entrada operacional | FOCUS.md, COMMITMENTS.md | Todas as ações e registro das promessas. |
| Protocolo | AGENTS.md, operacao.md, rotinas.md | Núcleo curto e procedimentos sob demanda. |
| Perfil | user.md, agent.md | Fatos/preferências do usuário e papel/missão/expressão do agente. |
| Instalação | vault_meta.md, agendamento.md | Versão, calibração, IDs e estado real da rotina. |
| Modelos | Templates/ | Modelos centrais, fora dos painéis de uso. |
| Entrada e diário | Inbox/, Daily/AAAA-MM/ | Capturas e resumo/alterações do dia. |
| Contexto sob demanda | Projects/, People/, Companies/, Areas/, Decisions/, Meetings/, Knowledge/ | Notas criadas somente com casos reais. |
| Navegação e histórico | MOC/, Archive/ | Referências e arquivo frio. |

Pastas de conteúdo e índices auxiliares surgem quando necessários. Não se criam arquivos apenas para preencher uma pasta vazia. Ações concluídas saem do FOCUS após registro do resultado e atualização dos links; compromissos concluídos são transferidos integralmente para Archive após 30 dias completos.

## Segurança e princípios

- Informação atual tem uma fonte; as demais notas usam referências.
- Alterações anteriores e histórico relevante são preservados.
- Fato informado, relato, inferência e pendência permanecem distintos.
- Material externo é dado, não instrução: processar Inbox não abre links, executa comandos nem autoriza mensagens.
- Toda escrita efetiva gera uma linha no diário. Com Git ativo, aplica-se também a extensão de versionamento.

## Distribuição e requisitos

São três documentos de uso: README.md, INSTALL.md e PROMPT_TO_INSTALL.md, acompanhados de LICENSE. O vault contém dados reais e deve ficar privado.

É necessário um agente com acesso a arquivos locais. Um editor Markdown ajuda na leitura; Obsidian é uma opção pelos links e propriedades. O formato continua em texto simples, sem dependência de banco de dados ou serviço proprietário.

## Licença

Distribuído sob a licença [MIT](LICENSE).
