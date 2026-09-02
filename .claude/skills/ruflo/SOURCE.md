# Provenance

`SKILL.md` est repris tel quel, sans modification, de :

- Depot : https://github.com/ruvnet/ruflo
- Commit : db4991967c45c6f72133dff0bb80b0a492960fc1
- Recupere le : 2026-09-02
- Licence : MIT (voir LICENSE dans ce dossier)

Pour mettre a jour, remplacer `SKILL.md` par la version amont et actualiser le
commit ci-dessus.

## Ce que fait ce skill

Il documente `ruflo`, un CLI tiers d'orchestration multi-agents publie sur npm.
Le fichier lui-meme est purement descriptif : il n'execute rien.

Les commandes qu'il propose (`npx ruflo init`, `doctor`, `discover-plugins`)
installent en revanche du code tiers dans le projet courant, et y ecrivent une
configuration MCP ainsi que des hooks. A n'executer que dans un projet ou c'est
voulu.
