---

### **Fiche de Révision : Introduction au C#**

---

#### **1. Qu’est-ce que C# ?**
- **Langage orienté objet** : C# est un langage de programmation orienté objet, moderne et simple, similaire à C++ et Java.
- **Intégré à .NET** : C# est le langage principal de la plateforme .NET de Microsoft, utilisant le **CLR (Common Language Runtime)** pour exécuter les programmes.
- **Environnement de développement** : C# est inclus dans **Visual Studio**, un IDE puissant pour développer des applications en C#, VB.NET, C++.NET, etc.

---

#### **2. C# et le Framework .NET**
- **Avantages de C#** :
  - Types de données alignés avec le CLR, ce qui améliore les performances.
  - Syntaxe stricte et sécurisée, évitant le typage implicite.
  - Documentation XML intégrée.
  - Syntaxe familière pour les programmeurs C, C++, Java et Perl.

---

#### **3. Environnement Visual Studio**
- **Visual Studio** : IDE complet pour développer des projets en C#.
  - **Fonctionnalités** : Ouverture de projets, création de nouveaux projets, gestion de code source (GitHub, Azure DevOps).
  - **Types de projets** : Applications console, bibliothèques de classes, tests unitaires, etc.

---

#### **4. Structure de base d’un programme C#**
- **Méthode `Main()`** : Point d’entrée du programme. C’est ici que l’exécution commence.
  ```csharp
  static void Main(string[] args)
  {
      Console.WriteLine("Hello World!");
  }
  ```
- **Namespaces** : Utilisés pour organiser le code (ex : `namespace HelloWorld`).
- **Commentaires** :
  - `//` pour les commentaires sur une ligne.
  - `/* ... */` pour les commentaires multilignes.
  - `///` pour la documentation XML.

---

#### **5. Types de données en C#**
- **Types prédéfinis** :
  - **Référence** : `object`, `string`.
  - **Entiers signés** : `sbyte`, `short`, `int`, `long`.
  - **Entiers non signés** : `byte`, `ushort`, `uint`, `ulong`.
  - **Caractère** : `char`.
  - **Flottants** : `float`, `double`, `decimal`.
  - **Booléen** : `bool`.

- **Alias des types .NET** : Par exemple, `int` est un alias de `System.Int32`.

---

#### **6. Variables et constantes**
- **Déclaration de variables** :
  ```csharp
  int compteur;
  double taux = 150.59;
  ```
- **Constantes** : Déclarées avec `const`.
  ```csharp
  const int MAX_EMPLOYES = 3000;
  ```

---

#### **7. Conversions de types**
- **Conversions de chaînes en nombres** :
  ```csharp
  int.Parse("123"); // Convertit une chaîne en int
  double.Parse("123.45"); // Convertit une chaîne en double
  ```
- **Gestion des erreurs de conversion** : Utilisation de `try/catch` pour gérer les exceptions.
  ```csharp
  try {
      int num = int.Parse("abc");
  } catch (Exception e) {
      Console.WriteLine("Erreur de conversion : " + e.Message);
  }
  ```

---

#### **8. Tableaux**
- **Déclaration et initialisation** :
  ```csharp
  int[] entiers = new int[] {0, 10, 20, 30};
  ```
- **Tableaux multidimensionnels** :
  ```csharp
  double[,] réels = new double[,] { {0.5, 1.7}, {8.4, -6} };
  ```
- **Propriété `Length`** : Nombre d’éléments dans un tableau.

---

#### **9. Opérateurs**
- **Arithmétiques** : `+`, `-`, `*`, `/`, `%` (modulo).
- **Relationnels** : `<`, `<=`, `==`, `!=`, `>`, `>=`.
- **Booléens** : `&&` (AND), `||` (OR), `!` (NOT).
- **Ternaire** : `condition ? expr1 : expr2`.

---

#### **10. Structures de contrôle**
- **Conditions** :
  - `if/else` :
    ```csharp
    if (condition) { ... } else { ... }
    ```
  - `switch` :
    ```csharp
    switch (variable) {
        case 1: ... break;
        case 2: ... break;
        default: ... break;
    }
    ```
- **Boucles** :
  - `for` :
    ```csharp
    for (int i = 0; i < 10; i++) { ... }
    ```
  - `while` :
    ```csharp
    while (condition) { ... }
    ```
  - `foreach` :
    ```csharp
    foreach (var item in collection) { ... }
    ```

---

#### **11. Gestion des exceptions**
- **Bloc `try/catch/finally`** :
  ```csharp
  try {
      // Code susceptible de générer une exception
  } catch (Exception e) {
      Console.WriteLine("Erreur : " + e.Message);
  } finally {
      // Code exécuté quoi qu'il arrive
  }
  ```

---

### **Points à retenir**
- **C#** est un langage orienté objet intégré à la plateforme .NET.
- **Visual Studio** est l’IDE principal pour développer en C#.
- La **méthode `Main()`** est le point d’entrée d’un programme.
- Les **types de données** en C# sont alignés avec le CLR.
- Les **structures de contrôle** (`if`, `switch`, `for`, `while`, `foreach`) permettent de gérer le flux d’exécution.
- La **gestion des exceptions** se fait avec `try/catch/finally`.

---
