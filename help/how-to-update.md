# Comment mettre à jour le carnet de compétences ?

> Au fur et à mesure de la formation de nouvelles compétences seront ajoutées au dépôt d'origine. Les commandes suivantes te permettront de mettre à jour ton dépôt tout en gardant tes modifictations

1. Configurer le remote

[source](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/configuring-a-remote-for-a-fork)

> à faire une fois dans ton dépôt local

Si tu te connectes à git en https:

```shell
git remote add upstream https://github.com/WildCodeSchool/worknstudy-skills.git
```

Si tu te connectes à git en ssh:

```shell
git remote add upstream git@github.com:WildCodeSchool/worknstudy-skills.git
```


2. Mettre à jour ton dépôt local

[source](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/syncing-a-fork)

> à faire à chaque début de semaine de formation (attention aux conflits possibles)

```shell
git fetch upstream
git merge upstream/main
```
