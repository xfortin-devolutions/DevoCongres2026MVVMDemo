# DevoCongres2026MVVMDemo

Démos pour la présentation MVVM du Devo Congrès 2026

## 🎯 Objectif de la présentation

Aider les développeurs habitués au pattern event-driven de WinForms à :
- Comprendre les différences fondamentales avec le pattern MVVM
- Voir comment les mêmes fonctionnalités sont implémentées dans chaque approche
- Découvrir les avantages du MVVM pour la séparation des responsabilités
- Explorer Avalonia comme alternative moderne et cross-platform à WinForms

## 🏗️ Structure du projet

### **WinForms.Demos** (.NET 10.0)
Application Windows Forms utilisant le **pattern Event-Driven** :
- Logique métier couplée aux contrôles UI
- Gestion d'événements (Click, SelectedIndexChanged, etc.)
- Manipulation directe des contrôles
- Approche impérative de la construction d'interface

### **Avalonia.Demos** (.NET 10.0)
Application cross-platform utilisant le **pattern MVVM** :
- Séparation claire entre UI (View) et logique (ViewModel)
- Data binding bidirectionnel
- CommunityToolkit.Mvvm avec source generators
- Approche déclarative avec XAML

## 🎯 Les trois démos comparatives

Chaque démo implémente exactement la même fonctionnalité dans les deux frameworks pour illustrer les différences d'approche :

### **Demo 1 : Master-Detail Pattern**
Gestion de produits avec affichage maître-détails.

**WinForms (Event-Driven)** :
- Événement `ListBox.SelectedIndexChanged` pour détecter la sélection
- Création manuelle de panels spécifiques selon le type de produit
- Mise à jour impérative des contrôles (TextBox, Label, etc.)
- Logique de présentation dans le code-behind

**Avalonia (MVVM)** :
- Propriété `SelectedProduct` avec `[ObservableProperty]`
- ViewLocator pour résolution automatique des vues
- Data binding déclaratif dans le XAML
- Logique isolée dans les ViewModels

**Concepts clés** : Liaison de données vs manipulation directe, ViewModels vs code-behind

### **Demo 2 : Multiple Views**
Visualisation des mêmes données sous différents modes (Grid, Tile, Card).

**WinForms (Event-Driven)** :
- ComboBox avec événement `SelectedIndexChanged`
- Clear/Add manuel des contrôles selon le mode sélectionné
- Re-création complète de du UI à chaque changement via `switch/case`
- Chaque panel de vue est instancié et ajouté manuellement

**Avalonia (MVVM)** :
- Enum `ViewMode` avec binding sur ComboBox
- Vues séparées (GridView, TileView, CardView) avec visibilité conditionnelle
- UI mise à jour automatiquement via binding `IsVisible` avec converter
- Aucun code-behind pour la gestion des vues

**Concepts clés** : Binding avec converters vs manipulation manuelle, visibilité déclarative vs impérative

### **Demo 3 : Dynamic Form Composition**
Génération dynamique de formulaires à partir d'une collection d'items.

**WinForms (Event-Driven)** :
- Création manuelle de panels pour chaque type d'item
- Factory pattern pour instancier les bons contrôles
- Abonnement aux événements de chaque contrôle créé
- Synchronisation manuelle des valeurs

**Avalonia (MVVM)** :
- Collection observable de `FormItemViewModel`
- ItemsControl lié à la collection
- ViewLocator pour résolution automatique des vues par type
- Binding automatique sur les propriétés des items

**Concepts clés** : UI data-driven vs code-driven, ViewLocator vs factory pattern

## 🔄 Comparaison des approches

| Aspect | WinForms (Event-Driven) | Avalonia (MVVM) |
|--------|-------------------------|-----------------|
| **Couplage** | UI et logique fortement couplées | Séparation stricte View/ViewModel |
| **Mise à jour UI** | Impérative (set des propriétés) | Déclarative (binding automatique) |
| **Testabilité** | Difficile (nécessite les contrôles) | Facile (ViewModels indépendants) |
| **Code** | Code-behind volumineux | XAML + ViewModels légers |
| **Réutilisation** | Limitée | Élevée (ViewModels réutilisables) |
| **Courbe d'apprentissage** | Facile (impératif) | Plus complexe (déclaratif) |

## 🛠️ Technologies utilisées

### WinForms.Demos
- **.NET 10.0 Windows Forms**
- Pattern Event-Driven classique
- Création dynamique de contrôles
- Gestion manuelle de l'état

### Avalonia.Demos
- **Avalonia UI 11.3.2** (cross-platform)
- **CommunityToolkit.Mvvm 8.2.1** (source generators)
- Compiled bindings (performance et sécurité de type)
- ViewLocator pattern

## 🚀 Démarrage

### Prérequis
- **.NET 10.0 SDK** ou plus récent
- **Visual Studio 2022** / **JetBrains Rider**

### Exécution des démos

**Application WinForms :**
```bash
cd WinForms.Demos
dotnet run
```

**Application Avalonia :**
```bash
cd Avalonia.Demos
dotnet run
```

## 📚 Avantages du MVVM pour les développeurs WinForms

**Séparation des responsabilités** : Logique business séparé du UI

**Réutilisabilité** : Un ViewModel peut alimenter plusieurs vues différentes

**Maintenance** : Modifications UI sans toucher à la logique métier

**Cross-platform** : Avec Avalonia, même code pour Windows/Linux/macOS

**Testabilité** : Les ViewModels peuvent être testés sans UI

## 📝 Notes

- Les deux projets utilisent **.NET 10.0** avec les fonctionnalités C# modernes
- Le projet Avalonia utilise les **compiled bindings** pour de meilleures performances
- Le projet WinForms montre délibérément l'approche traditionnelle sans frameworks MVVM