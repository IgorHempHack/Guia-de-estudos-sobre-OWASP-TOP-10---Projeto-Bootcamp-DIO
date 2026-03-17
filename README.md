# Guia-de-estudos-sobre-OWASP-TOP-10---Projeto-Bootcamp-DIO
Projeto criado como exercicio pertencente ao bootcamp de cibersegurança da Riachuelo na plataforma da DIO. O NotebookLM criado foi no intuito de ajudar a estudar sobre um tema extremamente relevante na cibersegurança, o OWASP Top 10

Este NotebookLM foi criado para ser utilizado como ferramenta de estudos sobre o tema de OWASP Top 10, sendo este tema algo cobrado e exigido a todos os profissionais que trabalham na área de cibersegurança, tendo como a necessidade de saber todos os 10 riscos de segurança mais criticos sob a aplicação web.

Principais fontes utilizadas:
https://owasp.org/Top10/2025/0x00_2025-Introduction/
https://www.cloudflare.com/pt-br/learning/security/threats/owasp-top-10/
https://www.azion.com/en/learning/websec/what-is-the-owasp-top-10-list-of-web-application-security-threats/
https://about.gitlab.com/blog/2025-owasp-top-10-whats-changed-and-why-it-matters/
https://blog.intelligencex.org/owasp-top-10-2025-vulnerabilities-complete-beginner-guide

Perguntas relizadas ao NotebookLM:

*O que é o OWASP Top 10?*

O **OWASP Top 10** é uma lista reconhecida globalmente que identifica os **dez riscos de segurança mais críticos** para aplicações web. É produzida e mantida pelo **Open Web Application Security Project (OWASP)**, uma organização internacional sem fins lucrativos focada na melhoria da segurança de software. O principal objetivo deste relatório é atuar como um **documento de consciencialização**, educando desenvolvedores, profissionais de segurança e organizações sobre as fraquezas mais comuns e perigosas.

A lista é atualizada periodicamente, geralmente a cada três ou quatro anos, com base na análise de dados de ataques reais de milhares de organizações e no estudo de milhões de aplicações. Na sua versão mais recente (como a edição de 2025/2026), o OWASP Top 10 reflete mudanças no panorama de ameaças, introduzindo novas categorias como **Software Supply Chain Failures** (Falhas na Cadeia de Abastecimento de Software) e **Mishandling of Exceptional Conditions** (Manuseamento Incorreto de Condições Excecionais). Atualmente, falhas como **Broken Access Control** (Falha no Controlo de Acesso) e **Security Misconfiguration** (Configuração Incorreta de Segurança) ocupam o topo da lista devido à sua elevada prevalência e impacto.

Este projeto é considerado um **padrão da indústria**, servindo de base para testes de penetração, formação em desenvolvimento seguro e marcos de conformidade, como o PCI DSS, SOC 2 e ISO 27001. Ao compreender estes riscos, as equipas podem adotar uma abordagem proativa para mitigar vulnerabilidades antes que sejam exploradas por atacantes. Além da lista principal para aplicações web, a OWASP também publica listas especializadas para áreas emergentes, como **APIs, Mobile e Large Language Models (LLM)**.

*Quais são estas 10 vulnerabilidades? Mê dê em topicos, explicando cada vulnerabilidade e como ela pode ser explorada por hackers, exemplificando com alguma situação possivel de ocorrer*

Com base na edição mais recente de 2025, o OWASP Top 10 apresenta as seguintes vulnerabilidades críticas, detalhadas com seus mecanismos de exploração e exemplos práticos:

*   **A01:2025 – Falha no Controlo de Acesso (Broken Access Control):** Ocorre quando o sistema não verifica adequadamente se um utilizador tem permissão para realizar uma ação ou aceder a um dado. Hackers exploram isto **alterando IDs em URLs** ou parâmetros para aceder a dados de terceiros ou funções de administrador.
    *   **Exemplo:** Um utilizador logado vê o seu saldo em `banco.com/conta?id=1234` e altera manualmente para `id=5678`, conseguindo visualizar as informações bancárias de outra pessoa porque o sistema não validou a permissão de acesso.

*   **A02:2025 – Configuração Incorreta de Segurança (Security Misconfiguration):** Esta falha acontece quando a aplicação ou o servidor são configurados de forma insegura, deixando "portas abertas". Atacantes aproveitam-se de **credenciais padrão (como admin/admin)**, modos de depuração ativos ou ficheiros de amostra deixados no servidor.
    *   **Exemplo:** Uma empresa instala um novo software e esquece-se de alterar a palavra-passe padrão do administrador, permitindo que um hacker ganhe controlo total do sistema apenas testando os dados de login de fábrica.

*   **A03:2025 – Falhas na Cadeia de Abastecimento de Software (Software Supply Chain Failures):** Refere-se a vulnerabilidades em bibliotecas, ferramentas ou processos de terceiros que a sua aplicação utiliza. Hackers comprometem bibliotecas populares ou criam versões falsas com nomes parecidos para **injetar código malicioso** em milhares de aplicações simultaneamente.
    *   **Exemplo:** O ataque à SolarWinds, onde 18.000 organizações instalaram atualizações legítimas que continham código malicioso injetado por atacantes na fonte.

*   **A04:2025 – Falhas Criptográficas (Cryptographic Failures):** Surge quando dados sensíveis não são protegidos ou usam métodos de encriptação fracos e desatualizados. Hackers exploram isto intercetando dados em redes Wi-Fi públicas (se o site usar HTTP em vez de HTTPS) ou **quebrando senhas armazenadas com algoritmos antigos**.
    *   **Exemplo:** Um site armazena senhas usando um método dos anos 90; um hacker invade a base de dados e consegue decifrar todas as senhas em minutos usando um computador moderno.

*   **A05:2025 – Injeção (Injection):** Acontece quando a aplicação recebe dados do utilizador e os executa como se fossem comandos legítimos. Hackers inserem **código SQL ou comandos de sistema** em campos de formulário para manipular a base de dados ou assumir o controlo do servidor.
    *   **Exemplo:** Num formulário de login, um hacker digita `admin' --` no campo de utilizador, o que faz com que a base de dados ignore a verificação da senha e permita o acesso como administrador.

*   **A06:2025 – Design Inseguro (Insecure Design):** Trata-se de uma falha na arquitetura ou na lógica de negócio, e não apenas um erro de programação. Os atacantes exploram **lacunas em fluxos de trabalho**, como mecanismos fracos de recuperação de senha ou falta de validação de preços.
    *   **Exemplo:** Num site de e-commerce, um atacante altera o preço de um item de 500€ para 0,01€ no seu próprio navegador antes de finalizar a compra, e o sistema aceita o pagamento por não validar o preço no servidor.

*   **A07:2025 – Falhas de Autenticação (Authentication Failures):** Ocorre quando a confirmação da identidade do utilizador é fraca. Hackers utilizam **ataques de força bruta** (tentar milhares de senhas), roubo de sessões ou aproveitam a falta de autenticação de dois fatores (2FA).
    *   **Exemplo:** Um site permite que um utilizador tente a senha infinitas vezes sem bloquear a conta, permitindo que um hacker use um script para testar as palavras-passe mais comuns até conseguir entrar.

*   **A08:2025 – Falhas de Integridade de Software ou Dados (Software or Data Integrity Failures):** Relaciona-se com a falta de verificação de que o código ou dados são legítimos e não foram alterados. Hackers podem **substituir atualizações de software por versões maliciosas** ou manipular dados serializados para executar código remoto.
    *   **Exemplo:** Uma aplicação instala plugins sem verificar a sua assinatura digital; um hacker interceta a ligação e envia um plugin falso que rouba todos os dados inseridos na aplicação.

*   **A09:2025 – Falhas de Monitorização e Registo de Segurança (Security Logging and Monitoring Failures):** Acontece quando eventos críticos não são registados ou ninguém vigia os logs para detetar atividades suspeitas. Isto permite que hackers operem **sem deixar rasto** ou permaneçam dentro de um sistema durante meses sem serem detetados.
    *   **Exemplo:** Um invasor acede à base de dados todas as noites durante um mês, mas como a empresa não monitoriza os logs de acesso, ninguém percebe que os dados estão a ser roubados até que apareçam na internet.

*   **A10:2025 – Manuseamento Incorreto de Condições Excecionais (Mishandling of Exceptional Conditions):** Uma categoria nova que foca em como a aplicação reage a erros ou situações inesperadas. Hackers forçam erros para **obter informações sensíveis em mensagens de erro detalhadas** ou para causar o colapso do serviço (DoS).
    *   **Exemplo:** Um atacante envia dados propositadamente errados que fazem a aplicação crashar, revelando no ecrã de erro a estrutura da base de dados e até senhas de ligação ao sistema.

*Quais ferramentas ajudam a detetar estas vulnerabilidades automaticamente?*

Existem diversas categorias de ferramentas automáticas que ajudam a identificar as vulnerabilidades do OWASP Top 10 2025 ao longo de todo o ciclo de desenvolvimento de software. As principais abordagens e ferramentas mencionadas nas fontes incluem:

*   **SAST (Static Application Security Testing):** Estas ferramentas analisam o **código-fonte** sem o executar para detetar padrões de design inseguros, como armazenamento de senhas em texto simples, falta de criptografia ou falhas de injeção. São essenciais para identificar vulnerabilidades logo no início do desenvolvimento.
*   **DAST (Dynamic Application Security Testing):** Ao contrário do SAST, o DAST analisa a **aplicação em execução**, simulando vetores de ataque para encontrar falhas de controlo de acesso (A01), problemas de autenticação (A07) e injeções.
*   **Scanning de Dependências (Dependency Scanning):** Foca-se na **Cadeia de Abastecimento de Software (A03)**, verificando se as bibliotecas de terceiros utilizadas possuem vulnerabilidades conhecidas (CVEs). O uso de um **SBOM (Software Bill of Materials)** é recomendado para ter visibilidade total sobre estas dependências.
*   **Scanning de Infraestrutura como Código (IaC Scanning):** Ajuda a detetar **Configurações Incorretas de Segurança (A02)** em definições de nuvem e ficheiros de implantação antes de serem aplicados em produção.
*   **Deteção de Segredos (Secret Detection):** Identifica automaticamente credenciais, chaves de API ou passwords esquecidas em ficheiros de configuração e variáveis de ambiente.
*   **Fuzz Testing de API:** Esta técnica gera inputs inesperados para a aplicação de modo a descobrir como esta lida com erros, sendo uma ferramenta direta para mitigar o **Manuseamento Incorreto de Condições Excecionais (A10)**.
*   **Agentes de Inteligência Artificial:** Soluções modernas como o **Security Analyst Agent** utilizam IA para analisar vulnerabilidades detetadas, avaliar o risco com base no modelo de ameaça da aplicação e sugerir estratégias de correção.

Plataformas integradas, como o **GitLab Ultimate**, consolidam estas várias ferramentas (SAST, DAST, IaC, Secret Detection) num único fluxo de trabalho (CI/CD), permitindo que os programadores resolvam falhas antes que o código chegue à produção. Outras referências mencionam o **React2Shell Ultimate** como um scanner autónomo para tipos específicos de vulnerabilidades.

Miniguia de Estudos:

Resumo sobre o assunto: 

O **OWASP Top 10** é uma lista reconhecida mundialmente que destaca os **dez riscos de segurança mais críticos** para aplicações web. Pense nela como uma lista dos "mais procurados", identificando as fraquezas que os atacantes mais tentam explorar. Mantida pela organização sem fins lucrativos Open Web Application Security Project (OWASP), a lista é atualizada periodicamente (a versão mais recente é a de 2025) com base na análise de milhares de vulnerabilidades reais.

Abaixo, apresento um resumo das vulnerabilidades de 2025, como são exploradas e as ferramentas utilizadas para as detetar:

### As 10 Vulnerabilidades e a Exploração por Hackers

1.  **A01: Falha no Controlo de Acesso:** O sistema não verifica se o utilizador tem permissão para o que está a tentar fazer.
    *   **Exploração:** Hackers **alteram IDs em URLs** (ex: mudar `user_id=123` para `456`) para aceder a dados de outros utilizadores ou funções de administrador.
2.  **A02: Configuração Incorreta de Segurança:** Ocorre quando a aplicação ou o servidor são configurados de forma insegura.
    *   **Exploração:** Atacantes usam **credenciais padrão** (como admin/admin) ou leem mensagens de erro detalhadas que revelam segredos do sistema.
3.  **A03: Falhas na Cadeia de Abastecimento de Software:** Refere-se a problemas em bibliotecas ou ferramentas de terceiros usadas na aplicação.
    *   **Exploração:** Hackers **injetam código malicioso em bibliotecas populares** de código aberto, comprometendo todas as aplicações que as utilizam.
4.  **A04: Falhas Criptográficas:** Falta de proteção adequada para dados sensíveis como senhas e cartões.
    *   **Exploração:** Atacantes **intercetam dados em redes Wi-Fi** não protegidas ou quebram encriptações antigas e fracas usando computadores modernos.
5.  **A05: Injeção:** A aplicação aceita dados do utilizador e executa-os como se fossem comandos.
    *   **Exploração:** Hackers inserem **comandos SQL em formulários de login** para entrar no sistema sem senha ou apagar bases de dados.
6.  **A06: Design Inseguro:** Falhas na arquitetura básica ou na lógica de negócio.
    *   **Exploração:** Atacantes aproveitam **fluxos de trabalho mal desenhados**, como conseguir alterar o preço de um produto no navegador antes de pagar.
7.  **A07: Falhas de Autenticação:** Problemas ao confirmar a identidade de quem acede ao sistema.
    *   **Exploração:** Uso de **ataques de força bruta** (tentar milhares de senhas) ou roubo de sessões ativas.
8.  **A08: Falhas de Integridade de Software e Dados:** Falta de verificação se o código ou dado é legítimo e não foi alterado.
    *   **Exploração:** Hackers substituem uma **atualização de software legítima por uma maliciosa** sem que o sistema perceba a troca.
9.  **A09: Falhas de Monitorização e Registo:** Não registar ou não vigiar atividades suspeitas.
    *   **Exploração:** Atacantes operam durante meses sem serem detetados porque **não há logs** das suas ações criminosas.
10. **A10: Manuseamento Incorreto de Condições Excecionais:** A aplicação lida mal com erros ou situações inesperadas.
    *   **Exploração:** Hackers forçam o sistema a falhar para causar uma **paragem do serviço (DoS)** ou para que mensagens de erro revelem senhas.

### Ferramentas de Deteção e Como Trabalham

As ferramentas modernas automatizam a descoberta destas falhas integrando-se no processo de desenvolvimento. As principais são:

*   **SAST (Testes Estáticos):** Analisa o **código-fonte** sem o executar, procurando padrões perigosos como senhas gravadas no código ou falta de encriptação.
*   **DAST (Testes Dinâmicos):** Ataca a aplicação **enquanto ela está a correr**, simulando as ações de um hacker para encontrar falhas de injeção ou controlo de acesso.
*   **Scanning de Dependências:** Verifica se as bibliotecas de terceiros usadas têm vulnerabilidades conhecidas, gerando um **SBOM (Software Bill of Materials)**, que é uma lista completa de todos os componentes.
*   **Fuzz Testing:** Envia **dados aleatórios e inesperados** para a aplicação para ver se ela falha ou revela informações sensíveis (especialmente útil para a nova categoria A10).
*   **IA e Agentes de Segurança:** Ferramentas de Inteligência Artificial analisam as falhas encontradas e sugerem **estratégias de correção** específicas para o código do programador.

Glossario:

Abaixo apresenta-se um glossário detalhado com os conceitos fundamentais para compreender o **OWASP Top 10 2025**, com base nas fontes fornecidas:

### Conceitos Organizacionais e Fundamentais
*   **OWASP (Open Web Application Security Project):** Uma organização sem fins lucrativos dedicada a melhorar a segurança de software em todo o mundo.
*   **OWASP Top 10:** Uma lista dos 10 riscos de segurança mais críticos para aplicações web, servindo como um guia de consciencialização para programadores e profissionais de segurança.
*   **CVE (Common Vulnerabilities and Exposures):** Registos públicos de vulnerabilidades e exposições de segurança conhecidas; a edição de 2025 analisou mais de **175.000** destes registos.
*   **CWE (Common Weakness Enumeration):** Uma lista de tipos de fraquezas de software; a metodologia de 2025 expandiu a sua análise para abranger **589 CWEs** diferentes.
*   **Causa Raiz vs. Sintoma:** A versão de 2025 foca-se nas causas que permitem os ataques (ex: Falhas Criptográficas) em vez de apenas listar os sintomas (ex: Exposição de Dados Sensíveis).

### Categorias de Vulnerabilidades (2025)
*   **A01: Broken Access Control (Falha no Controlo de Acesso):** Quando um sistema não verifica corretamente se um utilizador tem permissão para aceder a dados ou realizar ações específicas. Inclui o conceito de **IDOR** (Insecure Direct Object Reference).
*   **A02: Security Misconfiguration (Configuração Incorreta de Segurança):** Falhas decorrentes de sistemas, aplicações ou serviços de nuvem configurados de forma insegura, como o uso de credenciais padrão.
*   **A03: Software Supply Chain Failures (Falhas na Cadeia de Abastecimento de Software):** Vulnerabilidades que surgem através de bibliotecas de terceiros, ferramentas ou processos de build comprometidos.
*   **A04: Cryptographic Failures (Falhas Criptográficas):** Falta de proteção ou uso de criptografia fraca para dados sensíveis em trânsito ou em repouso.
*   **A05: Injection (Injeção):** Inserção de comandos ou código malicioso (SQL, NoSQL, OS) através de entradas do utilizador que a aplicação executa indevidamente.
*   **A06: Insecure Design (Design Inseguro):** Falhas na arquitetura básica e na lógica de negócio que ocorrem antes mesmo do código ser escrito, como fluxos de recuperação de senha fracos.
*   **A07: Authentication Failures (Falhas de Autenticação):** Fraquezas na confirmação da identidade do utilizador, permitindo ataques de força bruta ou roubo de sessões.
*   **A08: Software or Data Integrity Failures (Falhas de Integridade de Software ou Dados):** Falta de verificação de que o código ou os dados são legítimos e não foram alterados por terceiros.
*   **A09: Security Logging and Monitoring Failures (Falhas de Monitorização e Registo):** Insuficiência no registo de eventos críticos ou na vigilância desses registos para detetar ataques em tempo real.
*   **A10: Mishandling of Exceptional Conditions (Manuseamento Incorreto de Condições Excecionais):** Nova categoria em 2025 que foca na incapacidade de a aplicação lidar com erros ou situações inesperadas de forma segura.

### Ferramentas e Estratégias de Mitigação
*   **SAST (Static Application Security Testing):** Testes de segurança que analisam o **código-fonte** sem o executar para encontrar padrões inseguros.
*   **DAST (Dynamic Application Security Testing):** Testes que atacam a **aplicação em execução**, simulando vetores de ataque reais.
*   **SBOM (Software Bill of Materials):** Uma lista detalhada e inventariada de todas as bibliotecas e dependências utilizadas numa aplicação, essencial para gerir riscos na cadeia de abastecimento.
*   **IaC Scanning:** Verificação de ficheiros de **Infraestrutura como Código** para detetar configurações incorretas de segurança antes da implementação.
*   **Web API Fuzz Testing:** Geração de inputs inesperados para descobrir falhas de lógica ou erros que outros testes podem ignorar.
*   **Deteção de Segredos (Secret Detection):** Ferramentas para identificar credenciais ou chaves de API expostas em código ou ficheiros de configuração.

Conjunto de prompts reutilizáveis que possam apoiar futuras revisões sobre o tema:

Para rever e consolidar os conhecimentos presentes nas fontes sobre o **OWASP Top 10 2025**, pode utilizar as seguintes perguntas estruturadas por temas:

### Sobre a Metodologia e Evolução
*   **Quais foram os dados base para a criação da lista de 2025?** Considere o número de CVEs (Common Vulnerabilities and Exposures) e CWEs (Common Weakness Enumerations) analisados.
*   **Qual é a diferença fundamental na abordagem da lista de 2025 em relação a "sintomas" vs "causas raiz"?** Use o exemplo da transição de "Exposição de Dados Sensíveis" para "Falhas Criptográficas".
*   **Por que a OWASP utiliza inquéritos à comunidade além da análise de dados estatísticos?** Foque na limitação dos dados de teste que "olham para o passado".

### Sobre as Novas Categorias e Mudanças de Ranking
*   **Quais são as duas categorias inteiramente novas introduzidas em 2025 e o que cada uma foca?** (A03 e A10).
*   **Por que a "Configuração Incorreta de Segurança (A02)" subiu do 5º para o 2º lugar no ranking?**.
*   **Qual categoria de 2021 foi consolidada na "Falha no Controlo de Acesso (A01)" em 2025?**.

### Sobre as Vulnerabilidades Específicas
*   **Qual é a diferença entre um erro de codificação e o "Design Inseguro (A06)"?**.
*   **Como um ataque de IDOR (Insecure Direct Object Reference) exemplifica uma "Falha no Controlo de Acesso"?**.
*   **No contexto de "Falhas na Cadeia de Abastecimento (A03)", qual é a importância de um SBOM (Software Bill of Materials)?**.
*   **O que significa um sistema "falhar aberto" no contexto de "Manuseamento Incorreto de Condições Excecionais (A10)"?**.
*   **Quanto tempo, no mínimo, devem ser guardados os registos (logs) para evitar falhas de monitorização?**.

### Sobre Ferramentas e Mitigação
*   **Qual a diferença entre o funcionamento do SAST e do DAST na deteção de vulnerabilidades?**.
*   **Como o "Web API Fuzz Testing" ajuda especificamente a mitigar riscos da categoria A10?**.
*   **De que forma o "IaC Scanning" (Infraestrutura como Código) ajuda a prevenir a categoria A02?**.
*   **Qual o papel da Inteligência Artificial (como o Security Analyst Agent) na gestão destas vulnerabilidades?**.

### Exercícios Práticos de Revisão
*   **Dê um exemplo real de como uma injeção de SQL (A05) pode ser realizada num formulário de login.**.
*   **Se um atacante interceptar dados num Wi-Fi público, que categoria do OWASP Top 10 falhou?**.
*   **Crie um cenário onde uma falha na integridade de dados (A08) comprometa uma atualização de software.**.
