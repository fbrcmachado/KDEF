---
name: kdef
description: KDEF (Kumulus Documentation Engineering Framework) para produzir documentos de projetos de dados a partir de fontes rastreáveis e de um modelo fiel. Use quando o usuário disser "Ativar KDEF", "Ativar Modo Escriba", invocar $kdef ou solicitar explicitamente este fluxo documental.
---

# KDEF — Modo Escriba

O `manifest.json` da revisão Git **instalada** é a fonte oficial de versão, edição e capacidades. Ao ativar KDEF ou Modo Escriba, leia o manifesto local e apresente **uma vez por ativação**, antes da interação de trabalho:

```text
===========================================
KDEF v<version> | <edition>
Capacidades desta versão:
• <cada capability.label do manifest.json, na ordem registrada>
===========================================
```

Substitua os campos por valores do manifesto; a lista é dinâmica. Se o manifesto estiver ausente ou inválido, informe que não foi possível verificar a versão e não a invente. A revisão instalada é a versão em uso; não consulte a ponta remota a cada ativação.

Depois, execute a solicitação. Se os inputs de conhecimento ainda não foram fornecidos, peça as fontes do projeto (kickoff, requisitos, arquitetura, decisões, POE, handover, Solution Design, planilhas, notebooks, scripts e evidências pertinentes). Aceite os arquivos já enviados. Analise as fontes **antes** de solicitar o modelo a preencher; se o modelo também já veio, prossiga sem pedir novamente. Peça objetivo, escopo e destinatário somente se não forem claros.

Leia e siga `references/kdef_framework.md` integralmente para o fluxo, os registros, o contrato documental, a fidelidade ao modelo, os testes e o relatório. As regras obrigatórias incluem:

- Não inventar fatos, configurações, validações, decisões nem versões. Documentação oficial explica a tecnologia, mas não comprova sua adoção no projeto.
- Registrar fontes e afirmações atômicas, conflitos e lacunas, com rastreabilidade `SRC → FACT/REQ/DECISION → SECTION → TEST`; separar `AS-IS`, `TO-BE` e recomendações.
- Tratar o modelo como especificação de estrutura e apresentação, nunca como prova de fatos do novo projeto. Preencher **uma cópia** fiel, sem alterar o original.
- Manter campos sem evidência explicitamente pendentes. Não harmonizar conflitos silenciosamente.
- Validar o artefato gerado quanto a estrutura, conteúdo, evidência e visual; entregar relatório de validação com cobertura, rastreabilidade, conflitos, lacunas, testes e limites. Declarar somente testes realmente executados.
- Usar capacidades apropriadas ao formato do arquivo e renderizar para verificar o resultado visual quando aplicável.
