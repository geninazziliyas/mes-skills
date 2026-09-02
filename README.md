# mes-skills

Bibliotheque de skills Claude Code : un catalogue inerte, et de quoi en activer
une selection dans n'importe quel projet.

## Le principe

Claude ne charge que les skills presents dans le `.claude/skills/` du projet ou
l'on travaille. Ce depot separe donc deux choses :

| Dossier | Role |
| --- | --- |
| `.claude/skills/` | Les skills actifs **ici meme**, quand on travaille dans ce depot |
| `catalog/` | La reserve. Rien ne se charge depuis la : c'est un stock, pas une installation |
| `bin/skills` | Copie du catalogue vers le `.claude/skills/` d'un projet |

Cette separation est deliberee. Tout mettre dans `.claude/skills/` chargerait
les 137 skills a chaque session ouverte ici : Claude devrait choisir parmi
autant d'entrees, dont beaucoup se ressemblent, et passerait plus facilement a
cote du bon.

## Utilisation

```bash
# Voir ce que contient le catalogue, ou filtrer
bin/skills list
bin/skills list security

# Lire un skill en entier avant de l'activer
bin/skills show security-audit

# Activer dans le projet courant
bin/skills add security-audit swarm-orchestration

# Ou dans un projet precis
bin/skills add sparc-methodology --to ~/projets/mon-app

# Voir ce qui est actif, retirer
bin/skills installed --to ~/projets/mon-app
bin/skills remove sparc-methodology --to ~/projets/mon-app
```

`add` copie le dossier du skill. Une fois copie, il vit sa vie dans le projet :
le modifier la-bas ne touche pas au catalogue, et inversement. Pour repercuter
une mise a jour du catalogue, relancer `add`, qui remplace la version presente.

## Catalogue

### ruflo (137 skills)

Importe de [ruvnet/ruflo](https://github.com/ruvnet/ruflo), commit
`db4991967c45c6f72133dff0bb80b0a492960fc1`, licence MIT. Details et perimetre
exact dans `catalog/ruflo/SOURCE.md`.

Orchestration multi-agents, memoire persistante, recherche vectorielle,
methodologie SPARC, audit de securite, automatisation GitHub. Les plus
substantiels : `swarm-orchestration`, `security-audit`, `memory-management`,
`sparc-methodology`, `agentdb-vector-search`, `github-automation`.

Une bonne moitie sont des `agent-*` a description minimale du type
« Agent skill for coder ». Ils servent surtout de reference aux 60+ types
d'agents de ruflo ; `bin/skills list` permet de faire le tri.

## Ajouter un skill au catalogue

Deposer le dossier sous `catalog/<fournisseur>/<nom>/`, avec un `SKILL.md`
portant un frontmatter `name:` et `description:`. `bin/skills` le detecte sans
configuration.

Pour un skill venu d'ailleurs, y joindre sa licence et une note de provenance,
comme dans `catalog/ruflo/`.

## Avant d'importer un skill tiers

Un skill est un jeu d'instructions que Claude suivra. Le lire, et verifier au
minimum : execution de code distant (`curl | bash` et variantes), tentative de
detournement des instructions, exfiltration de secrets vers une URL, commandes
destructrices.

Le catalogue ruflo a ete passe a ce crible avant import, sans resultat.
