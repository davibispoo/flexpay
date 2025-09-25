# 📊 Slides da Apresentação - FlexPay Commerce
## Trabalho de Arquitetura de Software

---

## SLIDE 1: Capa
```
┌─────────────────────────────────────────┐
│                                         │
│         FLEXPAY COMMERCE                │
│                                         │
│   Payment Facilitator para E-commerce   │
│                                         │
│   Trabalho de Arquitetura de Software   │
│         Prof. Leonardo Pinho            │
│                                         │
│              Grupo:                     │
│         [Nomes dos Alunos]             │
│                                         │
│            FIAP MBA                     │
└─────────────────────────────────────────┘
```

---

## SLIDE 2: Agenda
```
┌─────────────────────────────────────────┐
│              AGENDA                     │
│                                         │
│  1. O Problema (História da Marina)     │
│  2. Mercado Brasileiro                  │  
│  3. Nossa Solução                       │
│  4. Requisitos e Aprendizados          │
│  5. Arquitetura C4                     │
│  6. Decisões Técnicas                  │
│  7. Implementação e Métricas           │
│  8. Conclusão                          │
│                                         │
└─────────────────────────────────────────┘
```

---

## SLIDE 3: A História de Marina
```
┌─────────────────────────────────────────┐
│         A HISTÓRIA DE MARINA            │
│                                         │
│  [Imagem: Loja de artesanato]          │
│                                         │
│  • Loja física em BH                   │
│  • Migrou para online na pandemia      │
│  • Descobriu que vender online é caro: │
│                                         │
│    ⚠️ Taxas: 4,99% + R$0,40/transação  │
│    ⚠️ Recebimento: D+30                │
│    ⚠️ Abandono: 47% no checkout        │
│    ⚠️ Integração: 3 gateways          │
│    ⚠️ Suporte: Inexistente            │
│                                         │
│  87% dos e-commerces = mesmo problema   │
└─────────────────────────────────────────┘
```

---

## SLIDE 4: O Mercado Brasileiro
```
┌─────────────────────────────────────────┐
│      E-COMMERCE BRASILEIRO 2024         │
│                                         │
│         R$ 185 BILHÕES/ANO             │
│              📈                         │
│                                         │
│   Crescimento: +20% ao ano             │
│   E-commerces: 1,5 milhão              │
│   Dominância: 3 players = 70%          │
│                                         │
│   Problemas do Mercado:                │
│   • Oligopólio de processadores        │
│   • Taxas não competitivas             │
│   • Tecnologia defasada                │
│   • Foco apenas em grandes players     │
│                                         │
└─────────────────────────────────────────┘
```

---

## SLIDE 5: Nossa Solução
```
┌─────────────────────────────────────────┐
│         FLEXPAY COMMERCE                │
│                                         │
│    "Democratizando pagamentos online"   │
│                                         │
│  ✅ Taxa Justa: 0.99%                  │
│     (vs 4.99% do mercado)              │
│                                         │
│  ✅ Recebimento D+1                    │
│     (sem custo adicional)              │
│                                         │
│  ✅ Checkout Unificado                 │
│     (todos os métodos)                 │
│                                         │
│  ✅ Dashboard Único                    │
│     (gestão simplificada)              │
│                                         │
└─────────────────────────────────────────┘
```

---

## SLIDE 6: O que Esperamos Aprender
```
┌─────────────────────────────────────────┐
│       OBJETIVOS DE APRENDIZADO          │
│                                         │
│  1. COMPORTAMENTO DE COMPRA            │
│     • Por que 47% abandonam?           │
│     • Quais métodos convertem mais?    │
│                                         │
│  2. TECNOLOGIA DE PAGAMENTOS           │
│     • Como escalar para 100k TPS?      │
│     • Como garantir PCI compliance?    │
│                                         │
│  3. MODELO PAYFAC                      │
│     • Estrutura de custos real?        │
│     • Como ser lucrativo?              │
│                                         │
│  4. EXPERIÊNCIA DO USUÁRIO             │
│     • Como criar checkout que converte?│
│     • Como reduzir fricção?            │
└─────────────────────────────────────────┘
```

---

## SLIDE 7: Requisitos Funcionais TOP 5
```
┌─────────────────────────────────────────┐
│      REQUISITOS FUNCIONAIS (RF)         │
│                                         │
│  RF001: Checkout em 1 Passo            │
│  └─ Reduz abandono de 47% para 15%     │
│                                         │
│  RF002: Tokenização Universal          │
│  └─ Compra com 1 clique = +35% conv.   │
│                                         │
│  RF003: Split Automático               │
│  └─ Marketplaces com N vendedores      │
│                                         │
│  RF004: Antifraude ML Adaptativo       │
│  └─ Padrões específicos por nicho      │
│                                         │
│  RF005: Reconciliação Inteligente      │
│  └─ Zero erro manual em fechamento     │
│                                         │
└─────────────────────────────────────────┘
```

---

## SLIDE 8: Requisitos Não-Funcionais (ASRs)
```
┌─────────────────────────────────────────┐
│    ATRIBUTOS DE QUALIDADE (RNF)        │
│                                         │
│  📊 PERFORMANCE                        │
│     Latência < 200ms (P95)             │
│     100ms delay = -1% conversão        │
│                                         │
│  ⚡ DISPONIBILIDADE                    │
│     99.99% = 52 min/ano downtime       │
│     1h fora = R$ 1M perdido            │
│                                         │
│  📈 ESCALABILIDADE                     │
│     100k TPS (Black Friday)            │
│     50x volume normal                   │
│                                         │
│  🔒 SEGURANÇA                          │
│     PCI-DSS Level 1                    │
│     Tokenização + Criptografia          │
└─────────────────────────────────────────┘
```

---

## SLIDE 9: Matriz de Riscos
```
┌─────────────────────────────────────────┐
│          MATRIZ DE RISCOS               │
│                                         │
│  TÉCNICOS              IMPACTO   PROB.  │
│  Vazamento dados       🔴 Alto   Baixa  │
│  Falha Black Friday    🔴 Alto   Média  │
│  Fraudes > 1%          🟡 Médio  Alta   │
│                                         │
│  NEGÓCIO                                │
│  Mudança BACEN         🔴 Alto   Média  │
│  Competição preços     🟡 Médio  Alta   │
│  Capital para float    🔴 Alto   Baixa  │
│                                         │
│  OPERACIONAL                            │
│  Onboarding complexo   🟡 Médio  Alta   │
│  Suporte não escala    🟡 Médio  Média  │
│                                         │
└─────────────────────────────────────────┘
```

---

## SLIDE 10: C4 - Diagrama de Contexto
```
┌─────────────────────────────────────────┐
│      C4 NÍVEL 1 - CONTEXTO              │
│                                         │
│         [Lojista]    [Comprador]       │
│             ↓            ↓              │
│      ┌─────────────────────────┐       │
│      │   FLEXPAY COMMERCE      │       │
│      │  Payment Facilitator     │       │
│      └───────────┬─────────────┘       │
│                  ↓                      │
│    ┌──────────────────────────┐        │
│    │ Akua.la │ E-commerce │ Bureaus│   │
│    │ Bancos  │ Banco Central      │    │
│    └──────────────────────────┘        │
│                                         │
│  Integrações: REST, GraphQL, SOAP      │
│                                         │
└─────────────────────────────────────────┘
```

---

## SLIDE 11: C4 - Diagrama de Container
```
┌─────────────────────────────────────────┐
│      C4 NÍVEL 2 - CONTAINER             │
│                                         │
│  FRONTEND          API GATEWAY          │
│  • Checkout Widget    Kong              │
│  • Dashboard       ↓  ↓  ↓  ↓          │
│  • Mobile App                           │
│                                         │
│  MICROSERVIÇOS                          │
│  ┌─────────────────────────────┐       │
│  │Checkout│Payment│Risk│Merchant│       │
│  │Service │Service│Svc │Service │       │
│  └─────────────────────────────┘       │
│                                         │
│  DADOS                                  │
│  PostgreSQL | Redis | S3 | Kafka        │
│                                         │
└─────────────────────────────────────────┘
```

---

## SLIDE 12: C4 - Payment Service
```
┌─────────────────────────────────────────┐
│    C4 NÍVEL 3 - PAYMENT SERVICE         │
│                                         │
│     Payment Controller (REST API)       │
│              ↓                          │
│        Payment Manager                  │
│         ↙        ↘                      │
│   Method         Tokenization           │
│   Selector       Engine                 │
│      ↓              ↓                   │
│   Gateway        Risk                   │
│   Adapter        Checker                │
│      ↓              ↓                   │
│        Repository Layer                 │
│              ↓                          │
│     [PostgreSQL] [Akua.la API]         │
│                                         │
└─────────────────────────────────────────┘
```

---

## SLIDE 13: Padrões Arquiteturais
```
┌─────────────────────────────────────────┐
│       PADRÕES ARQUITETURAIS             │
│                                         │
│  🏗️ MICROSERVIÇOS                      │
│     • Deploy independente               │
│     • Escala granular                   │
│                                         │
│  📬 EVENT-DRIVEN (Kafka)               │
│     • Comunicação assíncrona            │
│     • Menor acoplamento                 │
│                                         │
│  🔄 SAGA PATTERN                       │
│     • Transações distribuídas           │
│     • Compensação automática            │
│                                         │
│  🚦 CIRCUIT BREAKER                    │
│     • Proteção contra cascata           │
│     • Fallback automático               │
│                                         │
└─────────────────────────────────────────┘
```

---

## SLIDE 14: Stack Tecnológica
```
┌─────────────────────────────────────────┐
│         STACK TECNOLÓGICA               │
│                                         │
│  FRONTEND                               │
│  • React + TypeScript                   │
│  • Tailwind CSS                         │
│  • React Native (mobile)                │
│                                         │
│  BACKEND                                │
│  • Node.js + Express (maioria)          │
│  • Python + FastAPI (ML/Risk)           │
│  • Go (webhook service)                 │
│                                         │
│  INFRA & DADOS                          │
│  • AWS ECS + Kubernetes                 │
│  • PostgreSQL + Redis                   │
│  • Apache Kafka + ElasticSearch         │
│                                         │
└─────────────────────────────────────────┘
```

---

## SLIDE 15: Decisões Difíceis
```
┌─────────────────────────────────────────┐
│        DECISÕES DIFÍCEIS                │
│                                         │
│  1. SER PAYFAC vs SUB-MERCHANT         │
│     Escolha: PayFac                     │
│     Por quê: Controle total da UX       │
│     Trade-off: R$ 1M investimento       │
│                                         │
│  2. AKUA.LA vs CONSTRUIR DO ZERO       │
│     Escolha: Parceria Akua.la           │
│     Por quê: Time-to-market 3 meses     │
│     Trade-off: Revenue share            │
│                                         │
│  3. MONOLITO vs MICROSERVIÇOS          │
│     Escolha: Micro desde início         │
│     Por quê: Previsão 100k TPS          │
│     Trade-off: Complexidade inicial     │
│                                         │
└─────────────────────────────────────────┘
```

---

## SLIDE 16: Decisões Sem Retorno
```
┌─────────────────────────────────────────┐
│     ONE-WAY DOORS (Irreversível)       │
│                                         │
│  🚪 ARQUITETURA CORE                   │
│     Quando: 10k merchants               │
│     Custo mudança: R$ 5M                │
│                                         │
│  🚪 MODELO DE DADOS                    │
│     Quando: 1M transações               │
│     Custo mudança: 6 meses parado       │
│                                         │
│  🚪 API PÚBLICA                        │
│     Quando: 1000 integrações            │
│     Custo mudança: Suporte paralelo     │
│                                         │
│  🚪 SEGURANÇA PCI-DSS                  │
│     Quando: Certificação obtida         │
│     Custo mudança: 18 meses             │
└─────────────────────────────────────────┘
```

---

## SLIDE 17: Roadmap de Implementação
```
┌─────────────────────────────────────────┐
│       ROADMAP DE IMPLEMENTAÇÃO          │
│                                         │
│  FASE 1: MVP (3 meses)                 │
│  ├─ 20 merchants piloto                 │
│  ├─ Checkout + Dashboard básico         │
│  └─ R$ 100k processados                 │
│                                         │
│  FASE 2: ESCALA (6 meses)              │
│  ├─ 100 merchants                       │
│  ├─ Todos os features core              │
│  └─ R$ 1M processados/mês               │
│                                         │
│  FASE 3: EXPANSÃO (12 meses)           │
│  ├─ 1000+ merchants                     │
│  ├─ R$ 100M GMV anual                   │
│  └─ Break-even alcançado                │
│                                         │
└─────────────────────────────────────────┘
```

---

## SLIDE 18: Métricas de Sucesso
```
┌─────────────────────────────────────────┐
│        MÉTRICAS DE SUCESSO              │
│                                         │
│  📊 NEGÓCIO                            │
│  • Redução custos: 40%                 │
│  • Aumento conversão: 25%              │
│  • GMV: R$ 100M (24 meses)             │
│  • Break-even: 18 meses                │
│                                         │
│  🎯 PRODUTO                            │
│  • NPS Lojistas: > 70                  │
│  • Onboarding: < 24h                   │
│  • Chargeback: < 0.5%                  │
│                                         │
│  ⚡ TÉCNICAS                           │
│  • Uptime: 99.99%                      │
│  • Latência: < 200ms P95               │
│  • Throughput: 100k TPS                │
│                                         │
└─────────────────────────────────────────┘
```

---

## SLIDE 19: Aplicação dos Conceitos
```
┌─────────────────────────────────────────┐
│    CONCEITOS DA DISCIPLINA APLICADOS    │
│                                         │
│  ✅ TOGAF ADM                          │
│     8 fases implementadas               │
│     Vision → Architecture → Migration   │
│                                         │
│  ✅ C4 MODEL                           │
│     3 níveis de documentação            │
│     Contexto → Container → Componente   │
│                                         │
│  ✅ PERGUNTAS PODEROSAS                │
│     10/10 questões validadas            │
│     Trade-offs documentados             │
│                                         │
│  ✅ DESIGN THINKING                    │
│     Problema real → Solução viável      │
│     Story telling → Impacto             │
│                                         │
└─────────────────────────────────────────┘
```

---

## SLIDE 20: Conclusão
```
┌─────────────────────────────────────────┐
│             CONCLUSÃO                   │
│                                         │
│    FLEXPAY COMMERCE DEMOCRATIZA         │
│      PAGAMENTOS NO BRASIL              │
│                                         │
│  ✨ Impacto para Lojistas:            │
│     • Economia de 40% em taxas         │
│     • Aumento de 25% em vendas         │
│     • Gestão simplificada              │
│                                         │
│  🏗️ Arquitetura Preparada:            │
│     • Escala de 1k → 100k TPS          │
│     • Resiliência 99.99%               │
│     • Segurança PCI-DSS                │
│                                         │
│  "A melhor arquitetura é aquela que    │
│   resolve o problema do negócio de      │
│   forma sustentável" - Prof. Leonardo   │
│                                         │
└─────────────────────────────────────────┘
```

---

## SLIDE 21: Obrigado
```
┌─────────────────────────────────────────┐
│                                         │
│                                         │
│           MUITO OBRIGADO!               │
│                                         │
│         FLEXPAY COMMERCE                │
│                                         │
│              Perguntas?                 │
│                                         │
│                                         │
│         [Contatos do Grupo]             │
│                                         │
│                                         │
└─────────────────────────────────────────┘
```

---

## 📝 NOTAS PARA CRIAÇÃO DOS SLIDES

### Ferramentas Recomendadas
1. **Google Slides** - Colaborativo e gratuito
2. **PowerPoint** - Mais recursos visuais
3. **Canva** - Templates profissionais
4. **Figma** - Para os diagramas

### Paleta de Cores Sugerida
- **Primária**: #1168BD (Azul FlexPay)
- **Secundária**: #FF9800 (Laranja vibrante)
- **Sucesso**: #4CAF50 (Verde)
- **Alerta**: #FFC107 (Amarelo)
- **Erro**: #F44336 (Vermelho)
- **Texto**: #212121 (Cinza escuro)
- **Fundo**: #FFFFFF (Branco)

### Fontes Recomendadas
- **Títulos**: Montserrat Bold 32pt
- **Subtítulos**: Open Sans Semibold 24pt
- **Corpo**: Open Sans Regular 18pt
- **Dados**: Roboto Mono 16pt

### Dicas de Design
1. **Minimalista**: Máximo 6 linhas por slide
2. **Visual**: Use ícones e gráficos
3. **Consistente**: Mesma estrutura em todos
4. **Legível**: Contraste alto
5. **Hierarquia**: Destaque o importante

### Animações (se permitido)
- **Entrada**: Fade in suave
- **Transição**: Slide da direita
- **Ênfase**: Zoom sutil em números
- **Saída**: Fade out rápido

---

**IMPORTANTE**: Estes slides são um guia. Adapte conforme necessário, mas mantenha todos os pontos essenciais dos 23 itens obrigatórios!