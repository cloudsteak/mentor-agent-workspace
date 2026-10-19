# BLOCKERS

## PR #1: a `the1bit` jóváhagyása nem lehetséges

- A `gh` CLI a `the1bit` GitHub fiókkal van hitelesítve (`GH_TOKEN` nincs beállítva,
  a `~/.config/gh/hosts.yml`-ben lévő token a `the1bit`-é), ezért a PR #1 szerzője `the1bit`.
- A `gh pr create --reviewer the1bit` lefutott, de a reviewer nem került fel
  (`reviewRequests: []`), mert a GitHub nem enged review-t kérni a PR szerzőjétől.
- A GitHub azt sem engedi, hogy a szerző jóváhagyja a saját PR-jét, így
  `reviewDecision == APPROVED` a `the1bit`-től soha nem jöhet létre. A 90 perces várakozás értelmetlen,
  ezért nem indítottam el. A feladat szabálya szerint jóváhagyás nélkül nem merge-eltem.

## Megoldás

Állítsd be a `GH_TOKEN`-t egy másik (agent/bot) fiók tokenjére, amelynek van push joga
a `cloudsteak/mentor-agent-workspace` repóra, aztán futtasd újra a folyamatot (vagy nyisd meg
újra a PR-t azzal a fiókkal), hogy a `the1bit` reviewer lehessen és jóváhagyhassa.
