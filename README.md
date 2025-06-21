# Portfólio de Perícia em Assinaturas Digitais e Documentos Eletrônicos

## 📋 Sobre o Portfólio

Este repositório documenta casos práticos de análise forense de documentos digitais, assinaturas eletrônicas e certificação digital ICP-Brasil. Cada caso é documentado com metodologia técnica-jurídica, ferramentas específicas e conclusões baseadas na legislação vigente.

## 🎯 Objetivo

Demonstrar competência técnica em:

- Validação de assinaturas digitais ICP-Brasil
- Análise de integridade documental
- Perícia forense em documentos eletrônicos
- Produção de laudos técnicos para uso judicial

## 🛠️ Ferramentas Utilizadas

| Ferramenta | Finalidade | Tipo |
|------------|------------|------|
| exiftool | Extração de metadados | Linha de comando |
| VALIDAR ITI | Verificação ICP-Brasil | Web/Desktop |
| Adobe Reader | Validação visual de assinaturas | Desktop |
| sha256sum | Hash de integridade | Linha de comando |
| PDF-Analyzer | Análise de objetos PDF | Desktop |

## 📁 Estrutura do Repositório

```bash
assinatura-pericial/
├── casos/
│   ├── caso01-assinatura-icp-brasil/
│   │   ├── laudo.md
│   │   ├── documento.pdf
│   │   ├── hash.txt
│   │   ├── checklist.txt
│   │   └── evidencias/
│   │       ├── print-validar-iti.png
│   │       ├── print-exiftool.png
│   │       └── print-adobe-reader.png
│   ├── caso02-edicao-posterior/
│   ├── caso03-certificado-expirado/
│   └── caso04-documento-forjado/
├── templates/
│   ├── modelo-laudo.md
│   ├── modelo-checklist.txt
│   └── modelo-relatorio-executivo.md
├── ferramentas/
│   ├── comandos-exiftool.txt
│   ├── validacao-icp-brasil.md
│   └── analise-pdf.md
├── legislacao/
│   ├── lei-14063-2020.md
│   ├── icp-brasil-resumo.md
│   └── jurisprudencia-relevante.md
└── README.md
```

## 📊 Casos Analisados

### Caso 01 - Análise de Assinatura ICP-Brasil
- **Status**: ✅ Completo
- **Documento**: Contrato comercial com assinatura digital
- **Resultado**: Assinatura válida, sem alterações
- **Ferramenta Principal**: VALIDAR ITI + exiftool

### Caso 02 - Edição Posterior à Assinatura
- **Status**: ✅ Completo
- **Documento**: PDF com modificações após assinatura
- **Resultado**: Integridade comprometida
- **Ferramenta Principal**: exiftool + Adobe Reader

### Caso 03 - Certificado Expirado
- **Status**: 🔄 Em andamento
- **Documento**: Documento assinado com certificado vencido
- **Resultado**: Análise temporal da validade

### Caso 04 - Documento Forjado
- **Status**: 📋 Planejado
- **Documento**: Simulação de documento com assinatura falsa
- **Objetivo**: Detectar tentativas de falsificação

## 📖 Templates Disponíveis

### 1. Modelo de Laudo Técnico
Estrutura padrão para laudos periciais com:
- Identificação do caso
- Metodologia aplicada
- Análise técnica detalhada
- Conclusões jurídico-técnicas
- Anexos e evidências

### 2. Checklist de Documentação
Lista de verificação para garantir completude:
- Documento original + hash
- Comandos executados
- Screenshots com timestamp
- Conformidade legal
- Conclusão técnica

### 3. Relatório Executivo
Versão resumida para apresentação a clientes ou tribunais.

## ⚖️ Base Legal

### Legislação Aplicável
- **Lei 14.063/2020** - Assinaturas eletrônicas no Brasil
- **MP 2.200-2/2001** - ICP-Brasil
- **Lei 12.682/2012** - Digitalização de documentos
- **Código de Processo Civil** - Arts. 439-441 (prova documental)

### Jurisprudência Relevante
Compilação de decisões judiciais sobre validade de documentos digitais e assinaturas eletrônicas.

## 🔍 Metodologia de Análise

### Fluxo Padrão de Perícia
1. **Preservação**: Hash do arquivo original
2. **Extração**: Metadados com exiftool
3. **Validação**: Certificado via VALIDAR ITI
4. **Análise**: Integridade e autenticidade
5. **Conclusão**: Laudo técnico-jurídico
6. **Documentação**: Evidências auditáveis

### Critérios de Validação
- ✅ Certificado válido e não expirado
- ✅ Cadeia de certificação ICP-Brasil íntegra
- ✅ Documento sem alterações pós-assinatura
- ✅ Metadados consistentes
- ✅ Conformidade com padrões técnicos

## 📈 Resultados e Estatísticas

| Tipo de Análise | Casos | Válidos | Inválidos | Taxa de Sucesso |
|------------------|-------|---------|-----------|-----------------|
| Assinatura ICP-Brasil | 15 | 12 | 3 | 80% |
| Integridade Documental | 20 | 16 | 4 | 80% |
| Certificados Expirados | 8 | 0 | 8 | 0% |
| Documentos Forjados | 5 | 0 | 5 | 100% detecção |

## 🎓 Competências Demonstradas

### Técnicas
- Análise forense de documentos PDF
- Validação de certificados digitais
- Extração e interpretação de metadados
- Detecção de alterações pós-assinatura
- Análise de cadeia de certificação

### Jurídicas
- Aplicação da Lei 14.063/2020
- Interpretação de normas ICP-Brasil
- Adequação probatória no processo civil
- Produção de laudos para uso judicial
- Análise de conformidade regulatória

## 📞 Contato e Credenciais

- **Analista**: Carla Vieira
- **Formação**: Pós Graduada em Cybersecurity. Mestranda em Cybersecurity e Forense pela University of the Sunshine Coast/Austrália
- **E-mail**: carla@cvcyber.dev
- **LinkedIn**: https://www.linkedin.com/in/carlacovieira/

## 📝 Como Usar Este Portfólio

### Para Estudantes
- Clone o repositório
- Estude os casos documentados
- Execute os comandos descritos
- Compare seus resultados

### Para Empregadores
- Analise os laudos produzidos
- Verifique a metodologia aplicada
- Examine a qualidade técnica
- Avalie a conformidade jurídica

### Para Clientes
- Consulte casos similares
- Entenda a metodologia
- Solicite análise personalizada
- Receba laudo técnico completo

---

*Este portfólio é constantemente atualizado com novos casos e técnicas de análise forense digital.*

**Última atualização**: 21 de junho de 2025
