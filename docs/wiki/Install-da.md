# Installation

🌐 [English](Install) · **Dansk** · [Bahasa Melayu](Install-ms)

## Brug filerne direkte

Intet at installere. Klon og åbn den tjekliste, du skal bruge.

Repositoriet er offentligt, så HTTPS virker uden konto:

```bash
git clone https://git.tirsystem.com/TirSystem/sqa-qc-checklists.git
# eller det skrivebeskyttede GitHub-spejl
git clone https://github.com/TirSystem/sqa-qc-checklists.git
```

SSH virker også, hvis du har adgang til `git.tirsystem.com`:

```bash
git clone ssh://git@git.tirsystem.com:10022/TirSystem/sqa-qc-checklists.git
```

Det kanoniske repository ligger på `git.tirsystem.com`; GitHub-repositoriet er
et skrivebeskyttet spejl.

## Som submodul i dit projekt

```bash
git submodule add https://github.com/TirSystem/sqa-qc-checklists.git qc
git submodule update --init
```

Lås et commit eller tag, så dine reviews kan genskabes; opdatér det med en
bevidst commit.

## Med SQA and QC Framework

Du installerer ikke dette repository separat. Frameworket monterer det i
`framework/qc/` som et indlejret submodul:

```bash
git submodule update --init --recursive
```

Hvis `framework/qc/` er tom, kan intet review starte. Se
[Install-siden i framework-wikien](https://git.tirsystem.com/TirSystem/sqa-qc-framework/wiki/Install-da).

## Bidrag med en ændring

Et nyt eller ændret kriterium er et release-punkt. Ret tjeklisten, tilføj en
række i Version History, og behold hvert kriterium mærket med en ISO/IEC
25010-egenskab og et niveau.
