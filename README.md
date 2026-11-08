# outillage

Scripts et alias personnels pour Git et GitHub. Génériques : ils agissent sur le dépôt courant.

## Installation

Prérequis : `git`, `gh` connecté (`gh auth status`).

```bash
cd ~/projets
gh repo clone missclumsy81/outillage
echo 'export PATH="$PATH:$HOME/projets/outillage/bin"' >> ~/.bashrc
git config --global include.path '~/projets/outillage/git/aliases.gitconfig'
```

Ouvrir un nouveau terminal pour que le `PATH` soit pris en compte.

## Alias Git

| Alias | Rôle |
|---|---|
| `git cc` | Commit avec `Co-authored-by: Claude`. Seulement si l'agent a produit le contenu. |
| `git hist` | Historique une ligne par PR (`--first-parent`), sans lecteur. Accepte les options de `log` (`git hist -10`). |

## Scripts (`bin/`)

| Script | Rôle |
|---|---|
| `pr-fusion <n> [branche]` | Après confirmation, fusionne la PR `n` par merge commit, resynchronise la branche par défaut, supprime la branche fusionnée, crée la branche suivante si un nom est donné, puis affiche un contrôle. |
| `pr-prete "<titre>"` | Vérifie le titre (Conventional Commits), affiche les commits de la branche avec leurs fichiers, ouvre le rebase interactif s'il y a des `fixup!` (contenu vérifié identique ensuite), pousse après confirmation et ouvre la PR. |

## Contribuer

- Push direct sur `main`, messages au format Conventional Commits.
- Avant chaque commit touchant `bin/` : `shellcheck bin/*`.
