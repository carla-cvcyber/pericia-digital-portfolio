---
layout: default
title: "Caso 01: Verificação de Assinatura ICP-Brasil"
date: 2024-03-15
category: "Assinatura Digital"
tags: ["ICP-Brasil", "PDF", "Certificado Digital"]
---

# Caso 01: Verificação de Assinatura ICP-Brasil

## Resumo Executivo

**Objetivo:** Verificar a autenticidade e validade de assinatura digital ICP-Brasil em documento PDF

**Resultado:** Assinatura confirmada como válida e íntegra

**Data da Análise:** 15 de março de 2024

---

## 1. Contexto do Caso

### Situação
- Documento: Contrato comercial em formato PDF
- Questionamento: Validade da assinatura digital aplicada
- Solicitante: Tribunal de Justiça (processo anonimizado)

### Documentos Analisados
- `contrato_comercial_assinado.pdf` (2.3 MB)
- Metadados extraídos
- Certificado digital incorporado

---

## 2. Metodologia Aplicada

### Ferramentas Utilizadas
- **Adobe Acrobat Pro DC** - Verificação inicial
- **OpenSSL** - Análise do certificado
- **PDFtk** - Extração de metadados
- **ICP-Brasil Verificador** - Validação oficial

### Procedimentos Realizados

#### 2.1 Verificação Visual
- ✅ Painel de assinaturas visível no PDF
- ✅ Ícone de certificado válido presente
- ✅ Informações do signatário exibidas

#### 2.2 Análise Técnica do Certificado
```bash
# Extração do certificado
openssl pkcs7 -inform DER -in signature.p7s -print_certs -out cert.pem

# Verificação da cadeia de confiança
openssl verify -CAfile ica_chain.pem cert.pem
```

**Resultados:**
- Certificado emitido por AC válida ICP-Brasil
- Cadeia de confiança íntegra
- Certificado válido no momento da assinatura

#### 2.3 Verificação de Integridade
- **Hash SHA-256 do documento:** `a1b2c3d4e5f6...`
- **Status:** Documento íntegro, sem alterações
- **Timestamp:** 14/03/2024 14:32:15 UTC-3

---

## 3. Evidências Coletadas

### 3.1 Captura de Tela - Verificação Adobe
![Verificação Adobe](evidencias/prints/caso01_adobe_verificacao.png)
*Painel de assinaturas mostrando status válido*

### 3.2 Análise do Certificado
```
Subject: CN=João Silva:12345678901, OU=AC SOLUTI, O=ICP-Brasil
Issuer: CN=AC SOLUTI, O=ICP-Brasil, C=BR
Valid From: 15/01/2024 09:00:00 UTC
Valid To: 15/01/2025 09:00:00 UTC
Serial Number: 123456789ABCDEF
```

### 3.3 Verificação ICP-Brasil
- **Status LCR (Lista de Certificados Revogados):** Certificado não revogado
- **OCSP (Online Certificate Status Protocol) Response:** Good
- **Política de Assinatura:** AD-RB (Assinatura Digital com Referência Básica)

---

## 4. Análise dos Resultados

### 4.1 Autenticidade Confirmada
A assinatura digital foi aplicada utilizando certificado válido ICP-Brasil, emitido por Autoridade Certificadora credenciada.

### 4.2 Integridade Preservada
O documento não sofreu alterações após a aplicação da assinatura digital, conforme verificado pelo hash criptográfico.

### 4.3 Validade Temporal
A assinatura foi aplicada em 14/03/2024, quando o certificado estava dentro do prazo de validade (15/01/2024 a 15/01/2025).

---

## 5. Conclusões Técnicas

### Principais Achados
1. **Assinatura Válida:** Certificado ICP-Brasil genuíno e não revogado
2. **Documento Íntegro:** Sem evidências de alteração posterior
3. **Conformidade Legal:** Atende aos requisitos da MP 2.200-2/2001

### Limitações
- Análise baseada apenas no documento fornecido
- Não foi possível verificar a identidade física do signatário
- Análise técnica não substitui perícia grafotécnica quando necessária

---

## 6. Recomendações

1. **Para Futuras Verificações:**
   - Sempre verificar status de revogação online
   - Confirmar validade temporal do certificado
   - Documentar todo o processo de verificação

2. **Boas Práticas:**
   - Utilizar múltiplas ferramentas para confirmação
   - Preservar evidências digitais originais
   - Manter log detalhado das verificações

---

## 7. Anexos

### Documentação Técnica
- [Log completo da verificação](evidencias/documentos/caso01_log_verificacao.txt)
- [Certificado extraído](evidencias/documentos/caso01_certificado.pem)
- [Relatório OpenSSL](evidencias/documentos/caso01_openssl_report.txt)

### Referências Normativas
- MP 2.200-2/2001 - ICP-Brasil
- ITI-T 08 - Algoritmos e Parâmetros de Assinatura Digital
- RFC 3852 - Cryptographic Message Syntax

---

*Perícia realizada conforme metodologia padrão e melhores práticas forenses. Todas as evidências foram preservadas e estão disponíveis para auditoria.*
