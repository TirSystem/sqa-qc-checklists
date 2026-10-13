# AI-promptskabelon

🌐 [English](AI-Prompt-Template) · **Dansk** · [Bahasa Melayu](AI-Prompt-Template-ms)

Prompts til review med en AI-agent. Kør reviewet i en **ny session**, hvis samme
agent skrev dokumentet: reviewer må ikke være forfatteren.

## Review et dokument

```text
Review <sti/til/dokument.md> mod tjeklisten <sti/til/qc-type.md>.
Giv for hvert nummereret kriterium Pass, Fail eller N-A med dokumentation
(citér linjen i dokumentet). List derefter de ikke-beståede Mandatory-kriterier
først, giv en dom (Go, Go-with-conditions, No-Go) og den mindste ændring, der
ville få hvert ikke-bestået kriterium til at bestå. Redigér ikke dokumentet.
```

## Review kode

```text
Review ændringerne i <sti eller diff> mod <sti/til/qc-programming-sprog.md>
og vores kodekonventioner i <sti>. Rapportér hvert kriterium som Pass, Fail
eller N-A med fil og linje. Ret intet; list fundene efter alvor.
```

## Review sprog og domæne

```text
Review <dokument> mod qc-language-domain.md. Product Ownerens sprog er
<sprog>, og domænet er <domæne>. Kontrollér at hver PO-term i dokumentet
findes i ordbogen <sti>, og at ingen IT-term sniger sig ind i et PO-rettet
afsnit. List hver uoverensstemmelse med linjen.
```

## Re-review efter rettelser

```text
Re-review kun de kriterier, der fejlede i <tidligere reviewpost>. For hvert:
sig om det nye <dokument> nu består, og citér dokumentationen.
```

## Tips

- Giv agenten **én** tjekliste pr. review.
- Bed om dokumentation pr. kriterium; et nøgent "Pass" er ikke et review.
- Betragt agentens dom som input. Reviewer beslutter.
