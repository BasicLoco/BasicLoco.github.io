---
layout: post
title: "Résolutions matinales"
date: 2024-11-12
---

# Réveil

Encore un petit matin, « il fait pas chaud », comme le chante si bien cette chère Brigitte.
La cafetière est déjà finie, et j'aurais dû manger avant de faire autre chose.
Mais TDAH est évidemment là, et avec la petite ritournelle « faut faire ci, faut faire ça, et surtout, « bien entendu », il y a un ordre logique.
Peut-être même bien que ces conseils avisés ne sont qu'un rappel de la pyramide de Maslow.

La base.
Enfin, normalement. C'est ce qui est immédiatement accessible à la réflexion, et à la - je suppose - logique.
Est-ce que ça signifie que TDAH est synonyme d'absence de logique, de bon sens ?
Je ne pense pas.

Malgré tout, est-ce suffisant pour nous faire avancer que de nous rappeler les conséquences du TDAH sur notre quotidien ?
Est-ce la seule attitude efficace pour que l'on puisse améliorer notre confiance en nous ?
Bref, oui on galère dans une organisation standard de nos journées, tout en le sachant, et en ressentant les conséquences de nos difficultés.

Mais, si on se retrouve à 17h00, sans avoir encore mangé de la journée et à peine bu un verre d'eau, alors que le repas est prêt et que le verre d'eau est servi, est-ce une volonté délibérée de ne pas boire ni manger (tout en ayant le ventre super vide, avec les douleurs que ça signifie) ?
Si cette situation est constante dans le temps, ne faut-il pas chercher ailleurs ?
Y voir un signe de TDAH, et agir dessus ?

Comment ?
Chaque diabétique connait-il parfaitement la solution idéale à ses soucis ?
Pourquoi en serait-il différemment pour le TDAH, le TSA et d'autres affections ?
Ce n'est pas parce qu'on constate des difficultés que l'on sait les résoudre, ni même à quoi et/ou à qui faire appel.

# Tant pis pour Maslow, mais j'ai réussi !

- Linux Mint avec i3wm en gestionnaire de fenêtres
- Disposition US-intl sur un clavier HHKB

## Saisie du 'ç' dans les applications Terminal (linux Mint, i3wm)

- Subitement, je n'ai plus pu taper le caractère c avec une cédille (**ç**, habituellement avec ','+'c'), cette dernière apparaissant au-dessus du 'c' et non plus en dessous.
- Problème n'existant **QUE** pour les applications sous Terminal, dommage ce sont celles que j'utilise le plus.
- Déjà apparu auparavant mais n'était présent que dans la messagerie de Facebook sous Firefox (jamais trouvé la cause, ni beaucoup cherché/compris)

### Ce qui a fonctionné pour moi

- [Forum Linux.org](https://www.linux.org/threads/solved-deleted-the-compose-file-at-usr-share-x11-locale-en_us-utf-8.37594/)

  - réinstaller le service :

  ```bash
  sudo apt --reinstall install libx11-data
  reboot
  ```

  - message de gabriel.ipc, le 9 novembre 2021 :
    - créer un fichier **.XCompose** à la racine (`$HOME/.XCompose`)
    - y insérer ces lignes :

  ```bash
  include "%S/en_US.UTF-8/Compose"
  <dead_acute> <C>: "Ç"
  <dead_acute> <c>: "ç"
  ```

  - redémarrer (`reboot`)

## Problème d'installation de MarkdownPreview

- Neovim avec LazyVim en tant que gestionnaire de plugins, erreur lors de l'installation avec Lazy : `Vim:E117: Unknow function: mkdp#util#install`
- Déclaration du plugin avec LazyVim, fichier **markdown-preview-nvim.lua** situé dans `$HOME/.config/nvim/lua/plugins`

```vim
  {
    'iamcco/markdown-preview.nvim',
    cmd = { 'MarkdownPreviewToggle', 'MarkdownPreview', 'MarkdownPreviewStop' },
    ft = { 'markdown' },
    build = function()
      vim.fn['mkdp#util#install']()
    end,
  },
```

- **solution** : installer MarkdownPreview avec la commande `:Lazy build markdown-preview.nvim`
