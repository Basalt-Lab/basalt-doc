# **Contribuer à Basalt Logger**

## **Introduction**

Les contributions sont ce qui fait de la communauté open source un endroit incroyable pour apprendre, s'inspirer, et créer.  
Toute contribution que vous apportez est grandement appréciée.

Que vous aidiez à corriger des bugs, à proposer de nouvelles fonctionnalités, à mettre à jour la documentation ou à améliorer les styles de code, vous aidez à rendre notre projet plus puissant et bénéfique pour la communauté.

Suivez les étapes ci-dessous pour contribuer.

## **Processus de contribution**

```mermaid
gitGraph:
options
{
"nodeSpacing": 150,
"nodeRadius": 10
}
end
commit
branch stage
checkout stage
commit
branch feature
checkout feature
commit
commit
checkout stage
merge feature
checkout main
merge stage
```

1. **Fork** le projet  
   Commencez par créer un fork du dépôt sur GitHub. Cela vous aidera à créer votre propre copie du projet sur votre compte, vous permettant d'y apporter des modifications librement.
2. **Créez** votre branche de fonctionnalité (`git checkout -b feature/AmazingFeature`)  
    Créez une nouvelle branche pour travailler sur votre fonctionnalité.
3. **Committez** vos changements (`git commit -m 'Add some AmazingFeature'`)  
    Une fois que vous avez terminé vos modifications, vous pouvez les commiter et les préparer pour le push.
4. **Push** vers la branche (`git push origin feature/AmazingFeature`)  
    Une fois que vous avez terminé vos modifications, vous pouvez les pousser vers votre fork.
5. Ouvrez une **Pull Request** vers la branche `stage`  
    Une fois que vous avez poussé vos modifications vers votre fork, vous pouvez ouvrir une Pull Request vers la branche `stage` du dépôt principal.
6. Après la validation de votre Pull Request, votre branche sera **fusionnée** dans `stage` et supprimée.  
    Une fois que votre Pull Request a été validée, votre branche sera fusionnée dans `stage` et supprimée.


!!! warning "Note"
    Assurez-vous de toujours mettre à jour votre branche locale avec la branche `stage` avant de commencer à travailler sur une nouvelle fonctionnalité pour vous assurer que vous travaillez avec la dernière version du projet.

## **Notes supplémentaires**

Assurez-vous de tester toutes vos modifications et d'ajouter des tests lorsque cela est possible.  
Les projets avec une suite de tests complète comptent sur les contributions pour maintenir la couverture des tests.

Consultez les directives de style de code et les guides de contribution spécifiques au projet (s'ils existent) pour vous assurer que votre contribution est en ligne avec les attentes du projet.

N'oubliez pas de mettre à jour la documentation si nécessaire pour refléter vos changements, en particulier si vous ajoutez ou modifiez des fonctionnalités.

Soyez ouvert aux commentaires et activement engagé dans la discussion sur votre pull request si les membres de la communauté ou les mainteneurs ont des questions ou des préoccupations.

## **Conclusion**

Votre temps et vos compétences peuvent grandement bénéficier au projet et à la communauté dans son ensemble.

Nous sommes impatients de voir vos contributions et sommes prêts à collaborer pour intégrer de nouvelles idées ou améliorations.

Merci de contribuer à rendre **Basalt Logger** encore meilleur !
