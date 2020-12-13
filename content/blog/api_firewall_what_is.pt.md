+++
title = "API Firewalls: Para que servem, onde vivem, o que comem? "
description = "Este post apresenta um pouco sobre o conceitos de API Firewall, e como é possível proteger de forma efetiva suas APIs"
author = "Edgar Silva"
date = "2020-12-11"
tags = ["api", "api-firewall",]
categories = ["api-firewall", ]
[[images]]
  src = "img/apifirewall.png"
  alt = "API Firewalls"
  stretch = "vertical"
[[images]]
  src = "img/apifirewall.png"
  alt = "API Firewalls"
[[images]]
  src = "img/apifirewall.png"
  alt = "API Firewalls"
  stretch = "horizontal"
+++

A transformação digital trouxe mais agilidade e novas experiências, e uma das maneiras de se obter isto foram através das APIs. :smiley:

Com APIs, é possível alcançar inúmeros canais, que geram negócios em diferentes indústrias e beneficiam um número considerável de pessoas e empresas em todo o mundo. Como toda a inovação, vários benefícios são obtidos, porém sempre existem os efeitos colaterais, e isso se observou em todas as revoluções industriais que passamos.

De acordo com a previsão do Gartner:

> “Até 2022, as APIs serão os maiores vetores de ataques “
> 
> Gartner-  [https://www.gartner.com/en/documents/3834704](https://www.gartner.com/en/documents/3834704)

Esta previsão tem coerência pois todas as organizações, vem cada vez mais expondo seus negócios através de APIs, gerando dessa maneira um novo alvo para ataque cibernéticos, uso indevido de dados, violação de regulações de privacidade dos dados (GDPR, LGPD etc), e vários outros fatores.

## Mas eu tenho um WAF, logo, estou protegido

Seria interessante que fosse tão simples assim, mas na prática não é. Construídos com foco em aplicações, quando falamos de APIs, os mecanismos que devem ser tratados são muito diferentes. Infelizmente, existem ameaças que um WAF não consegue tratar, entre elas:

**Vulnerabilidade**

**O que acontece?**

**Causas raíz**

**Exemplo de APIs afetadas**

Exposição de Dados Excessiva

Vazamento de Informações de APIs

Filtro de Dados de ClientesAPI não trata entrada de dados problemáticas

[Uber](https://appsecure.security/blog/how-i-could-have-hacked-your-uber-account)  
[PlentyOfFish](https://theappanalyst.com/plentyoffish.html)  
[Amazon Ring](https://gizmodo.com/ring-s-hidden-data-let-us-map-amazons-sprawling-home-su-1840312279)

Atribuição em Massa

  
O hacker pode passar informações extras que estão sendo usadas para atualizar dados de back-end

DTO global é usado para configurar dadosMesmo DTO é usado para leitura e escrita

[Harbour registry](https://42crunch.com/stopping_harbor_registry_attack/)  (admin escalation)[New Relic](https://hackerone.com/reports/267781)  (Free APIKey access)

Quebra de Autenticação

  
Tokens inválidos / expirados / hackeadosSem segurança aplicadaCredenciais fracasLimitação de taxa ruim

Falta de validação de credenciais (JWT) de acordo com  [BCP](https://datatracker.ietf.org/doc/rfc8725/)Ambientes de Dev/QA que permanecem abertos

[Siemens](https://cert-portal.siemens.com/productcert/pdf/ssa-451445.pdf)  
[SoundCloud](https://www.checkmarx.com/blog/checkmarx-research-soundcloud-api-security-advisory)

  
Exposição de nível de função quebrada

Endpoints administrativos que ficam abertos

  
A implementação combina a funcionalidade administrativa e de negócios

[Likud Voting App](https://www.zdnet.com/article/netanyahus-party-exposes-data-on-over-6-4-million-israelis/)

Pontos presentes na Top 10 OWASP API

Os pontos acima fazem parte da OWASP Top 10 riscos de segurança em APIs :

1.  [Injection](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A1-Injection)
2.  [Broken Authentication](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A2-Broken_Authentication)
3.  [Sensitive Data Exposure](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A2-Broken_Authentication)
4.  [XML Eternal Entities (or XXE)](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A4-XML_External_Entities_(XXE))
5.  [Broken Access Control](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A5-Broken_Access_Control)
6.  [Security Misconfiguration](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A6-Security_Misconfiguration)
7.  [Cross-Site Scripting (or XSS)](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A7-Cross-Site_Scripting_(XSS))
8.  [Insecure Deserialization](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A7-Cross-Site_Scripting_(XSS))
9.  [Using Components With known vulnerabilities](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A9-Using_Components_with_Known_Vulnerabilities)
10.  [Insufficient Logging And Monitoring](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A10-Insufficient_Logging%252526Monitoring)

O tratamento de informações, a segurança dos dados, vai além das capacidades de autenticação, autorização, tokens etc, que são alguns dos pontos, que API Gateways e API Managers tratam, portanto, estas soluções sozinhas, não deverão ser suficientes para tratarem todos os aspectos de invasões, mau-uso, além de impedir que APIs sejam hackeadas.

Você pode perguntar:  **Eu não poderia fazer isto no API Gateway?**  Tecnicamente, você tem que criar tais políticas em blocos – Porém:

-   Isto não escala! Para cada API, você precisará de políticas complexas para validar cada cabeçalho, todos os parâmetros, toda a peça de fluxo de dados através das requisições e respostas das APIs.
-   Em resumo: Dificilmente isto irá acontecer.

Para isto seria necessário manualmente consertar cada política a cada mudança da API :

-   As políticas se tornarão obsoletas

Times de segurança tem visibilidade zero sobre as políticas :

-   Como você auditora e reforça padrões de segurança corporativas de forma consistente em todas as APIs?

Algumas perguntas que seriam interessantes responder ao observar suas APIs e seus contratos:

-   O que acontece se eu passar um parâmetro com numeral negativo?
-   O que acontece se em um parâmetro que eu aceito uma lista de strings eu passar qualquer valor de maneira ordinária.
-   Se eu descobrir os Headers que eu tenho que passar, se eu informar outros valores ao invés do esperado, quais serão os comportamentos?

Entra em cena então um novo tipo de solução, tão nova como um segmento de indústria tecnológica:  **API Firewalls**.

## Sobre API Firewalls

Esses componentes de software, são incubidos de tratarem aspectos de segurança de APIs que nem um WAF ou API Gateway conseguem, basicamente estes aspectos são:

-   Validação de aspectos de segurança dos contratos das APIs: Swaggers
-   Validação Automática de Conteúdo das mensagens
-   Proteção de Endpoints e bloqueio de mensagens suspeitas, impedindo-as que cheguem até o API Gateway ou Microsserviço.
-   “Scan” contínuo de potenciais ataques, ou requisições suspeitas.
-   Rastreamento de toda a cadeia de requisição e respostas
-   Mascaramento/Ocultação de dados que podem comprometer ou expor dados sensíveis
-   Etc.

Todas as features acima, são executadas de forma automática, e são pontos preocupantes dos times de DevOps, e mais ainda dos Dev**Sec**Ops.

![](https://apifirewall.files.wordpress.com/2020/12/image.png?w=1024)

Jornada digital vs Times de Desenvolvimento/Produtos e Segurança (CISO)

Atire a primeira pedra, aquele que nunca deixou aspectos de segurança para as fases finais do projeto, e que as vezes, por atrasos, prazos apertados, e a necessidade de lançamento, vários produtos foram para produção mesmo assim?

E se a jornada começasse a inserir aspectos de validações dos Swagger da sua API, deste a fase de desenho dos mesmos (API First)? E que estes componentes pudessem ser plugins do Visual Studio Code, Eclipse ou do InteliJ Idea?

![Details for specific issues](https://github.com/42Crunch/vscode-openapi/blob/master/images/Details%20for%20specific%20issues.gif?raw=true)

Plugin de API Auditing para MS Visual Studio Code

-   Visual Studio Code:  [https://marketplace.visualstudio.com/items?itemName=42Crunch.vscode-openapi](https://marketplace.visualstudio.com/items?itemName=42Crunch.vscode-openapi)
-   InteliJ Idea:  [https://plugins.jetbrains.com/plugin/14837-openapi-swagger-editor](https://plugins.jetbrains.com/plugin/14837-openapi-swagger-editor)
-   Eclipse: [https://marketplace.eclipse.org/content/openapi-swagger-editor#group-details](https://marketplace.eclipse.org/content/openapi-swagger-editor#group-details)

E se todo o processo de desenvolvimento, pudesse de forma automática passar por um processo de auditoria usando as práticas de CI/CD, com suporte a Jenkins, Azure DevOps, GitHub Actions etc?

Por último, imagine um ambiente de proteção, que você pode ter qualquer solução de API Manager/Gateway, protegida continuamente, com suporte ainda a proteção até mesmo a Arquiteturas mais sofisticadas, que usem Kubernetes, com ServiceMeshes (Sidecars), ou qualquer modelo de implantação que lhe seja melhor conveniente.

![](https://apifirewall.files.wordpress.com/2020/12/image-1.png?w=1024)

Como já disse, é uma indústria totalmente nova, que estou aprendendo e a medida que tiver conteúdos interessantes, estarei compartilhando por aqui sobre o uso de API Firewalls, e como trazer esta realidade para diferentes etapas do desenvolvimento de APIs, desde a sua concepção, testes, deploy e produção.

“Vamos lá, proteger APIs” com  **API Firewalls**.

#### **LEITURAS RECOMENDADAS:**

-   [https://dzone.com/articles/owasp-top-10-api-security](https://dzone.com/articles/owasp-top-10-api-security)
-   [https://dzone.com/articles/api12019-broken-object-level-authorization](https://dzone.com/articles/api12019-broken-object-level-authorization)