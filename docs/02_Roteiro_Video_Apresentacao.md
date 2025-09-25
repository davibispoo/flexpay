# 🎬 Roteiro Completo para Vídeo de Apresentação
## FlexPay Commerce - Trabalho de Arquitetura de Software

**Duração Total:** 15-20 minutos  
**Equipe:** 4 pessoas  
**Professor:** Leonardo Carneiro Pinho  

---

## 📋 DIVISÃO POR PESSOA E CRONÔMETRO

### 👤 **PESSOA 1: Introdução e Problema** (4 minutos)
**Tempo:** 0:00 - 4:00

#### **[0:00 - 0:30] Abertura**
- "Olá professor Leonardo e colegas! Somos o grupo FlexPay Commerce"
- "Hoje vamos apresentar nossa solução de Payment Facilitator para e-commerce"
- "Eu sou [NOME] e começo contando a história que inspirou nosso projeto"

#### **[0:30 - 2:00] Story Telling - A História de Marina**
- "Marina tem uma loja de artesanatos em BH..."
- Mostrar SLIDE com foto ilustrativa
- "Durante a pandemia, ela migrou para o online mas..."
- Listar os 5 problemas principais:
  - Taxas de 4,99% + R$0,40
  - Recebimento D+30
  - 47% abandono no checkout
  - 3 gateways diferentes
  - Suporte inexistente
- "E Marina não está sozinha - 87% dos e-commerces sofrem com isso"

#### **[2:00 - 3:00] O Mercado Brasileiro**
- Mostrar SLIDE com dados do mercado:
  - R$ 185 bilhões/ano
  - Crescimento 20% a.a.
  - 1,5 milhão de e-commerces
- "Mas apenas 3 players dominam 70% do mercado"
- "Com taxas abusivas e serviço ruim"

#### **[3:00 - 4:00] Nossa Solução**
- "Por isso criamos o FlexPay Commerce"
- Mostrar SLIDE com os 4 pilares:
  1. Taxa justa: 0.99%
  2. Recebimento D+1 grátis
  3. Checkout unificado
  4. Dashboard único
- "Agora passo para [NOME] explicar os requisitos"

---

### 👤 **PESSOA 2: Requisitos e Aprendizados** (4 minutos)
**Tempo:** 4:00 - 8:00

#### **[4:00 - 4:30] Transição e Contexto**
- "Obrigado [NOME]. Para resolver esses problemas, precisamos entender profundamente o mercado"
- "Nosso projeto tem 4 objetivos de aprendizado principais"

#### **[4:30 - 5:30] O que Esperamos Aprender**
Mostrar SLIDE com os 4 aprendizados:
1. **Comportamento de compra**: Por que 47% abandonam?
2. **Tecnologia de pagamentos**: Como escalar para 100k TPS?
3. **Modelo PayFac**: Como ser lucrativo com taxa baixa?
4. **UX de checkout**: Como converter mais?

#### **[5:30 - 6:30] Requisitos Funcionais Principais**
Mostrar SLIDE com RF top 5:
- **RF001**: Checkout em 1 passo (reduz abandono)
- **RF002**: Tokenização universal (compra com 1 clique)
- **RF003**: Split automático (marketplaces)
- **RF004**: Antifraude ML adaptativo
- **RF005**: Reconciliação inteligente

#### **[6:30 - 7:30] Requisitos Não-Funcionais (ASRs)**
Mostrar SLIDE com métricas:
- **Performance**: < 200ms (P95)
- **Disponibilidade**: 99.99% (52min/ano downtime)
- **Escala**: 100k TPS na Black Friday
- **Segurança**: PCI-DSS Level 1
- **Recovery**: RTO < 5 min, RPO < 1 min

#### **[7:30 - 8:00] Riscos Principais**
- "Identificamos 3 categorias de riscos críticos"
- Mostrar SLIDE com matriz de riscos:
  - **Técnicos**: Vazamento de dados, falha Black Friday
  - **Negócio**: Mudança regulatória BACEN
  - **Operacional**: Fraudes, chargebacks > 1%
- "Agora [NOME] vai mostrar nossa arquitetura"

---

### 👤 **PESSOA 3: Arquitetura Técnica** (5 minutos)
**Tempo:** 8:00 - 13:00

#### **[8:00 - 8:30] Transição e Visão Geral**
- "Obrigado [NOME]. Vou apresentar como arquitetamos a solução"
- "Seguimos o C4 Model com 3 níveis de detalhamento"
- "Aplicamos padrões modernos e decisões baseadas em trade-offs claros"

#### **[8:30 - 9:30] C4 Nível 1 - Contexto**
Mostrar DIAGRAMA Contexto:
- "No centro temos o FlexPay Commerce"
- "Integramos com 5 sistemas externos principais:"
  - Akua.la (processamento)
  - E-commerces (Shopify, Woo)
  - Bureaus (Serasa, SPC)
  - Bancos (liquidação)
  - BACEN (regulação)
- "Servimos 2 personas: Lojista e Comprador"

#### **[9:30 - 10:30] C4 Nível 2 - Container**
Mostrar DIAGRAMA Container:
- **Frontend**: 4 aplicações (Widget, Dashboard, Admin, Mobile)
- **API Gateway**: Kong para rate limiting e auth
- **8 Microserviços**: Cada um com responsabilidade única
- **5 Databases**: PostgreSQL, Redis, S3, Elastic, Kafka
- "Note a separação clara de responsabilidades"

#### **[10:30 - 11:30] C4 Nível 3 - Payment Service**
Mostrar DIAGRAMA Componente:
- "Zoom no Payment Service - nosso core"
- Explicar fluxo: Controller → Manager → Gateway Adapter
- "Tokenization Engine garante PCI compliance"
- "Risk Checker integrado para análise real-time"

#### **[11:30 - 12:30] Padrões e Decisões Arquiteturais**
Mostrar SLIDE com decisões:
1. **Microserviços**: Escala independente (decidimos early)
2. **Event-Driven**: Kafka para resiliência
3. **SAGA Pattern**: Transações distribuídas
4. **Circuit Breaker**: Proteção contra cascata
5. **CQRS**: Otimização leitura/escrita

#### **[12:30 - 13:00] Stack Tecnológica**
- **Frontend**: React, TypeScript, Tailwind
- **Backend**: Node.js (maioria), Python (ML), Go (performance)
- **Infra**: AWS ECS, Kubernetes, CloudFront
- **Dados**: PostgreSQL, Redis, Elasticsearch
- "Passo para [NOME] falar das decisões de negócio"

---

### 👤 **PESSOA 4: Decisões e Conclusão** (3-4 minutos)
**Tempo:** 13:00 - 16:00/17:00

#### **[13:00 - 13:30] Decisões Difíceis**
- "Obrigado [NOME]. Tomamos 3 decisões muito difíceis:"

**1. Ser PayFac vs Sub-merchant**
- "PayFac = controle total mas R$1M investimento"
- "Decidimos: PayFac para diferenciação"

**2. Akua.la vs Construir do Zero**
- "Speed vs Controle"
- "Decidimos: Parceria para MVP, migrar depois se necessário"

**3. Monolito vs Microserviços**
- "Simplicidade vs Escalabilidade"
- "Decidimos: Micro desde início por previsão de crescimento"

#### **[13:30 - 14:30] Decisões sem Retorno**
Mostrar SLIDE "One-Way Doors":
1. **Arquitetura core**: Após 10k merchants = R$5M mudar
2. **Modelo de dados**: 1M transações = impossível migrar
3. **API pública**: Breaking changes afetam todos
4. **Segurança PCI**: Certificação é commitment

#### **[14:30 - 15:30] Plano de Implementação**
Mostrar SLIDE com roadmap:
- **Fase 1 (3 meses)**: MVP com 20 merchants
- **Fase 2 (6 meses)**: Escalar para 100 merchants
- **Fase 3 (12 meses)**: 1000+ merchants, R$100M GMV
- **Métricas de sucesso**: NPS > 70, Churn < 5%

#### **[15:30 - 16:00/17:00] Conclusão e Impacto**
- "O FlexPay Commerce democratiza pagamentos no Brasil"
- "Com arquitetura preparada para escala"
- "Aplicando todos os conceitos da disciplina:"
  - TOGAF para estruturação
  - C4 Model para documentação
  - Perguntas Poderosas para decisões
  - Trade-offs conscientes
- "Reduzindo custos em 40% para os lojistas"
- "Aumentando conversão em 25%"
- "Obrigado pela atenção! Perguntas?"

---

## 🎯 DICAS PARA GRAVAÇÃO

### Preparação
1. **Ensaiar 2x** antes de gravar
2. **Slides prontos** na ordem correta
3. **Cronômetro visível** para todos
4. **Cenário limpo** e boa iluminação
5. **Testar áudio** antes de começar

### Durante a Apresentação
- **Olhar para câmera** (não para tela)
- **Falar pausadamente** e com clareza
- **Entusiasmo** com o projeto
- **Transições suaves** entre pessoas
- **Mostrar diagramas** por tempo adequado

### Elementos Visuais Essenciais
1. Slide com história da Marina
2. Dados do mercado brasileiro
3. Matriz de riscos
4. 3 Diagramas C4 (em tela cheia)
5. Decisões arquiteturais
6. Roadmap de implementação
7. Métricas de sucesso

### Erros Comuns a Evitar
- ❌ Ler slides
- ❌ Falar muito rápido
- ❌ Pular detalhes técnicos importantes
- ❌ Esquecer de explicar "por quê" das decisões
- ❌ Ultrapassar muito o tempo

---

## 📝 CHECKLIST FINAL

Antes de gravar, confirme:
- [ ] Todos sabem sua parte
- [ ] Slides estão na ordem
- [ ] Diagramas são legíveis
- [ ] Demos preparadas (se houver)
- [ ] Backup do material
- [ ] Bateria dos devices carregada
- [ ] Ambiente silencioso
- [ ] Roupa apropriada

---

## 🎬 SCRIPT DE ABERTURA E FECHAMENTO

### Abertura (Pessoa 1)
"Boa [tarde/noite], Professor Leonardo e colegas. Somos o grupo FlexPay Commerce e hoje apresentamos nosso trabalho de arquitetura de software para a disciplina de Arquitetura da Escolha. Nosso projeto resolve um problema real do mercado brasileiro de e-commerce através de uma solução de Payment Facilitator. Eu sou [NOME] e começo nossa apresentação..."

### Fechamento (Pessoa 4)
"...Com isso concluímos nossa apresentação do FlexPay Commerce. Aplicamos todos os conceitos aprendidos na disciplina para criar uma arquitetura robusta, escalável e alinhada com as necessidades reais do mercado. Agradecemos a atenção de todos e estamos à disposição para perguntas. Muito obrigado!"

---

**BOA APRESENTAÇÃO! 🚀**