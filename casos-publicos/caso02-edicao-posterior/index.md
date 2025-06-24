---
layout: default
title: "Caso 02: Detecção de Edição Posterior"
permalink: /casos-publicos/caso02-edicao-posterior/
date: 2024-04-22
category: "Integridade Documental"
tags: ["Adulteração", "PDF", "Análise Forense"]
---

# Caso 02: Detecção de Edição Posterior à Assinatura Digital

## Resumo Executivo

**Objetivo:** Verificar se houve alterações em documento PDF após aplicação de assinatura digital  
**Resultado:** Confirmada edição posterior que comprometeu a integridade do documento  
**Data da Análise:** 22 de abril de 2024

---

## 1. Contexto do Caso

### Situação
- Documento: Proposta comercial com valor questionado
- Questionamento: Suspeita de alteração no valor após assinatura
- Origem: Processo de arbitragem comercial (anonimizado)

### Histórico
O documento em questão foi assinado digitalmente por ambas as partes, porém uma das partes alega que o valor foi alterado posteriormente à assinatura, invalidando o acordo.

### Documentos Analisados
- `proposta_comercial_v1.pdf` (arquivo original alegado) - 1.8 MB
- `proposta_comercial_v2.pdf` (arquivo questionado) - 1.9 MB
- Metadados e logs de sistema fornecidos

---

## 2. Metodologia Aplicada

### Ferramentas Utilizadas
- **Adobe Acrobat Pro DC** - Análise de estrutura PDF
- **PDFtk** - Extração de metadados detalhados
- **ExifTool** - Análise de propriedades do arquivo
- **HxD** - Análise hexadecimal da estrutura
- **OpenSSL** - Verificação criptográfica

### Hipóteses Investigadas
1. **H1:** Documento foi editado após assinatura digital
2. **H2:** Assinatura foi aplicada em documento já alterado
3. **H3:** Documento permaneceu íntegro desde a assinatura

---

## 3. Análise Técnica Detalhada

### 3.1 Comparação de Estrutura dos Arquivos

#### Análise de Tamanhos

proposta_comercial_v1.pdf: 1.847.392 bytes  
proposta_comercial_v2.pdf: 1.923.744 bytes  
Diferença: +76.352 bytes (+4.1%)

#### Hashes de Verificação
```bash
# Arquivo V1
MD5: f3e2a1b9c8d7e6f5a4b3c2d1e0f9e8d7
SHA-256: 1a2b3c4d5e6f7890abcdef1234567890abcdef1234567890abcdef1234567890

# Arquivo V2  
MD5: a9b8c7d6e5f4a3b2c1d0e9f8e7d6c5b4
SHA-256: 9876543210fedcba9876543210fedcba9876543210fedcba9876543210fedcba

Resultado: Hashes completamente diferentes confirmam alterações significativas.
```

### 3.2 Análise de Metadados

**Propriedades do Documento V1**  
Creator: Microsoft Word  
Producer: Microsoft Print to PDF  
CreationDate: 2024-04-15 10:30:22 UTC-3  
ModDate: 2024-04-15 10:30:22 UTC-3  

**Propriedades do Documento V2**  
Creator: Microsoft Word  
Producer: Microsoft Print to PDF  
CreationDate: 2024-04-15 10:30:22 UTC-3  
ModDate: 2024-04-18 16:45:33 UTC-3  

**Achado Crítico:** Data de modificação posterior em 3 dias, indicando edição após criação original.

### 3.3 Análise da Assinatura Digital

**Status da Assinatura no V1**
- ✅ Assinatura válida e íntegra
- ✅ Certificado válido no momento da assinatura
- ✅ Documento não modificado após assinatura

**Status da Assinatura no V2**
- ❌ Assinatura INVÁLIDA
- ❌ Mensagem: "O documento foi modificado após a assinatura"
- ❌ Integridade comprometida

### 3.4 Análise Estrutural do PDF

**Estrutura Interna - Comparação**
- V2 possui objetos PDF adicionais (incrementos 15-18)
- Novos streams de conteúdo inseridos
- Referências cruzadas modificadas

### 3.5 Análise do Conteúdo Alterado

**Localização da Alteração**  
Página 3, Seção "Valores Comerciais":  
- V1: "Valor total: R$ 50.000,00"  
- V2: "Valor total: R$ 85.000,00"  

**Evidência Técnica**
- Objeto PDF 247 (página 3) foi modificado
- Stream de conteúdo alterado com novo valor
- Fonte e formatação mantidas para disfarçar alteração

---

## 4. Evidências Coletadas

### 4.1 Análise Visual Comparativa

- Comparação lado a lado mostrando alteração no valor

### 4.2 Análise de Integridade

- Documento V1 com assinatura válida
- Documento V2 com assinatura comprometida

### 4.3 Análise de Metadados

**Comparação de Metadados**

| Propriedade    | Versão 1             | Versão 2             |
|----------------|----------------------|----------------------|
| CreationDate   | 2024-04-15 10:30     | 2024-04-15 10:30     |
| ModDate        | 2024-04-15 10:30     | 2024-04-18 16:45 ⚠️  |
| Pages          | 5                    | 5                    |
| Size           | 1.8 MB               | 1.9 MB               |
| Producer       | MS Print to PDF      | MS Print to PDF      |

### 4.4 Análise Hexadecimal

**Comparação dos bytes nas posições onde ocorreu a alteração:**

| Offset   | V1 (Original)   | V2 (Modificado) |
|----------|-----------------|-----------------|
| 0x1A350  | 35 30 2E 30 30  | 38 35 2E 30 30  |
|          | "50.00"         | "85.00" ⚠️     |

---

## 5. Cronologia dos Eventos

**Timeline Reconstituída**

- **2024-04-15**: Criação do documento original, aplicação da assinatura digital, documento V1 íntegro
- **2024-04-18**: Alteração detectada, valor modificado de R$ 50k para R$ 85k, geração do documento V2, assinatura invalidada

**Evidências Temporais**
- 15/04/2024 10:30 - Criação e assinatura original
- 18/04/2024 16:45 - Modificação detectada nos metadados
- 22/04/2024 - Data da análise pericial

---

## 6. Análise dos Resultados

### 6.1 Confirmação de Adulteração

Evidências Conclusivas:
- Hashes Diferentes: Confirmam alteração do conteúdo
- Metadados Alterados: ModDate posterior à criação
- Assinatura Inválida: Sistema detecta comprometimento
- Análise Estrutural: Novos objetos PDF inseridos
- Comparação Visual: Valor claramente modificado

### 6.2 Método de Alteração

Técnica Identificada:
- Edição direta do conteúdo PDF
- Modificação do stream do objeto de texto
- Tentativa de manter aparência original
- Não houve reaplicação de assinatura

### 6.3 Impacto na Validade Jurídica

Consequências:
- Documento V2 não possui validade jurídica
- Assinatura digital invalidada pela alteração
- Versão V1 permanece íntegra e válida
- Evidência clara de má-fé na alteração

---

## 7. Conclusões Técnicas

**Principais Achados**
- Alteração Confirmada: O documento foi inequivocamente modificado após a assinatura digital
- Método Identificado: Edição direta do conteúdo com alteração do valor comercial
- Invalidação da Assinatura: A modificação tornou a assinatura digital inválida
- Preservação do Original: A versão V1 mantém integridade e validade

**Grau de Certeza**
- Alteração detectada: 100% de certeza
- Local da alteração: Página 3, campo "Valor total"
- Período da alteração: Entre 15/04 e 18/04/2024
- Impacto jurídico: Invalidade completa do documento V2

**Limitações**
- Análise baseada nos arquivos fornecidos
- Não foi possível identificar o autor da alteração
- Não se pode determinar a ferramenta específica utilizada
- Análise não inclui aspectos de autoria da modificação

---

## 8. Recomendações

### Para Prevenção Futura

- Uso de Timestamps:
  - Aplicar carimbos de tempo confiáveis
  - Utilizar autoridades de timestamp credenciadas
  - Documentar momento exato da assinatura
- Armazenamento Seguro:
  - Manter originais em repositório íntegro
  - Usar sistemas com controle de versão
  - Implementar logs de acesso e modificação
- Verificação Contínua:
  - Validar assinaturas periodicamente
  - Monitorar integridade dos documentos
  - Manter backups seguros e verificáveis

### Para o Caso Específico

- Documento V1: Aceitar como válido e íntegro
- Documento V2: Rejeitar por alteração posterior
- Processo Legal: Considerar implicações de má-fé
- Auditoria: Investigar outros documentos do mesmo processo

---

## 9. Anexos Técnicos

**Documentação Completa**
- Análise ExifTool Comparativa
- Análise Hexadecimal
- Checklist de Conformidade
- Hashes
- Log de Auditoria Completo
- Log OpenSSL - Verificação
- Relatório PDFtk - V1
- Relatório PDFtk - V2
- Relatório de Validação Cruzada
- Script de Análise Python
- Timeline Forense

**Evidências Visuais**
- Comparação Visual dos Documentos
- Status das Assinaturas
- Análise de Metadados

**Referências Normativas**
- MP 2.200-2/2001 - Validade jurídica de documentos eletrônicos
- ITI-T 08 - Padrões de assinatura digital
- ISO 32000-1 - Especificação PDF

---

## 10. Declaração Pericial

Baseado na análise técnica realizada, confirmo categoricamente que o documento proposta_comercial_v2.pdf foi alterado após a aplicação da assinatura digital, comprometendo sua integridade e validade jurídica.

A alteração foi realizada de forma dolosa, modificando especificamente o valor comercial de R$ 50.000,00 para R$ 85.000,00, invalidando completamente a assinatura digital e tornando o documento juridicamente inválido.

Análise realizada conforme metodologia científica e normas técnicas aplicáveis. Todas as evidências foram preservadas e estão disponíveis para contraprova e auditoria independente.
