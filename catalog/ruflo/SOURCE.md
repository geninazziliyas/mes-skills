# Skills importes de ruvnet/ruflo

- Depot : https://github.com/ruvnet/ruflo
- Commit : db4991967c45c6f72133dff0bb80b0a492960fc1
- Licence : MIT (voir .claude/skills/ruflo/LICENSE)

## Ce qui a ete importe

135 skills repris de `.agents/skills` (le catalogue canonique du depot) plus
`browser`, seul skill supplementaire de `.claude/skills`. Les 37 skills presents
dans les deux dossiers ont ete pris depuis `.agents/skills` ; les ecarts entre
les deux versions etaient d'une ligne au plus.

`dual-mode` a ete ecarte : il ne contient pas de SKILL.md, ce n'est pas un skill
mais un jeu de notes, et Claude ne l'aurait jamais charge.

## Ce qui n'a pas ete importe

Les skills internes aux plugins (`plugins/*/skills`) et a l'implementation
(`v3/@claude-flow/*`) restent chez eux : ils sont installes par leur plugin
respectif, pas isolement.

## Controle effectue avant import

Les 136 SKILL.md ont ete passes au crible : execution de code distant
(`curl | bash` et variantes), tentatives d'injection d'instructions, exfiltration
de secrets vers une URL, commandes destructrices. Aucun resultat. Le seul
signalement, dans `agent-production-validator`, etait une assertion de test sur
`FORCE_HTTPS`.

Ce controle porte sur les fichiers de skills, pas sur le CLI `ruflo` lui-meme :
lancer `npx ruflo init` installe du code tiers et ecrit une configuration MCP et
des hooks dans le projet courant.
