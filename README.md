# Desafio DIO: Infraestrutura como Código com AWS CloudFormation e Stacks de Firewall


Este repositório documenta meus estudos e práticas sobre **AWS CloudFormation** e a implementação de **Stacks de Firewall**, realizados durante a jornada na [Digital Innovation One (DIO)](https://www.dio.me/). O foco deste laboratório é entender como provisionar, gerenciar e proteger recursos na nuvem utilizando o conceito de Infraestrutura como Código (IaC).

---

## O que é o AWS CloudFormation?

O AWS CloudFormation permite modelar, provisionar e gerenciar recursos da AWS e de terceiros usando código (arquivos YAML ou JSON). Isso significa que uma infraestrutura inteira pode ser versionada, testada e replicada em minutos, eliminando configurações manuais propensas a erros.

**Conceitos-chave que consolidei:**
* **Templates:** O arquivo de texto declarativo onde a infraestrutura é descrita.
* **Stacks (Pilhas):** Uma unidade única de recursos provisionados a partir de um template. Se você deleta a Stack, todos os recursos atrelados a ela são removidos juntos.
* **Change Sets:** Uma pré-visualização das alterações que o CloudFormation fará na infraestrutura antes de executá-las de fato.

---

## 🛡️ Stacks de Firewall no CloudFormation

A segurança na AWS funciona em camadas. Utilizar Stacks de Firewall significa criar templates específicos que definem as regras de tráfego de rede e proteção contra ataques, separando a lógica de segurança da lógica da aplicação (usando *Nested Stacks* ou pilhas aninhadas).

Durante os estudos, estruturei o conhecimento sobre as seguintes proteções provisionáveis:

1. **Security Groups (SGs):** Atuam como firewalls virtuais no nível da instância (ex: liberando a porta 8080 para uma API em Spring Boot ou a porta 3306 apenas para conexões internas no banco de dados).
2. **Network ACLs (NACLs):** Firewalls no nível da sub-rede. Funcionam como uma fronteira sem estado (stateless) para bloquear ou permitir tráfego em uma rede inteira.
3. **AWS WAF (Web Application Firewall):** Proteção na camada de aplicação (Camada 7). Essencial para bloquear padrões de ataques comuns, como injeção de SQL ou *Cross-Site Scripting* (XSS).

---

## 🚀 Aplicações Práticas (Casos de Uso)

Entender Infraestrutura como Código abre portas para arquiteturas corporativas complexas. Alguns cenários de aplicação das Stacks de Firewall:

* **Sistemas de Gestão Seguros:** Automatizar a infraestrutura de soluções digitais para o setor de hotelaria (como provisionar servidores e bancos de dados para a plataforma da Atlas Tec), garantindo que regras de firewall rigorosas protejam os dados dos hóspedes desde o primeiro deploy da aplicação.
* **Ambientes de Teste Descartáveis:** Subir uma réplica exata da infraestrutura de produção com todas as regras de segurança aplicadas para validar uma nova funcionalidade no backend e, em seguida, destruir a stack inteira para economizar custos.
* **Resposta a Incidentes:** Implementar rapidamente uma regra no AWS WAF via CloudFormation para bloquear tráfego malicioso originado de IPs específicos durante um ataque de negação de serviço (DDoS).

