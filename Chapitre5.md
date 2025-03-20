### **Fiche de révision détaillée sur LINQ**

---

## **Introduction à LINQ**
### **Qu’est-ce que LINQ ?**
- **LINQ (Language Integrated Query)** est un composant du .NET Framework permettant d’effectuer des requêtes sur diverses sources de données.
- Inspiré du **SQL**, LINQ permet de manipuler **des listes, des objets, des fichiers XML, des bases de données relationnelles, etc.**.
- LINQ propose deux syntaxes :
  1. **Query Syntax** (inspirée du SQL)
  2. **Method Syntax** (utilisant des **expressions lambda**)
- LINQ est **paresseux** : la requête n’est exécutée que lorsqu’on itère dessus (ex. dans un `foreach`).

---

## **Les bases de LINQ**
### **Étapes d'une requête LINQ**
1. **Définir la source de données** (tableau, liste, base SQL…).
2. **Créer l’expression de requête** (ex. `from num in numbers where num > 5 select num`).
3. **Exécuter la requête** (via un `foreach` ou une méthode comme `ToList()`).

### **Exemple Query Syntax**
```csharp
int[] numbers = { 1, 2, 3, 4, 5, 6, 7, 8 };
var numQuery = from num in numbers where (num % 2) == 0 select num;

foreach (int num in numQuery)
{
    Console.Write("{0} ", num);
}
// Affiche : 2 4 6 8
```

### **Exemple Method Syntax (Expression Lambda)**
```csharp
int[] numbers = { 1, 2, 3, 4, 5, 6, 7, 8 };
IEnumerable<int> numQuery = numbers.Where(elt => elt % 2 == 0);

foreach (int num in numQuery)
{
    Console.Write("{0} ", num);
}
// Affiche : 2 4 6 8
```
**Remarque :** On peut mélanger les deux syntaxes.

---

## **Les méthodes principales de LINQ**
### **1. Sélectionner des données**
| Méthode  | Description |
|----------|------------|
| **Where()**  | Filtrer les données selon une condition |
| **Select()**  | Transformer les données et retourner un autre type |
| **First()**  | Retourne le premier élément qui correspond à la condition (Erreur si aucun élément) |
| **FirstOrDefault()**  | Comme `First()`, mais retourne `0/null` si aucun élément |
| **Single()**  | Retourne l’unique élément qui correspond à la condition (Erreur si plusieurs ou zéro) |
| **SingleOrDefault()**  | Comme `Single()`, mais retourne `0/null` si aucun élément |

#### **Exemple avec FirstOrDefault**
```csharp
int[] numbers = { 1, 2, 3, 4, 5, 6, 7, 8 };
var numQuery = numbers.Where(num => num % 5 == 0);
Console.WriteLine(numQuery.FirstOrDefault()); // Affiche 0 (car aucun élément)
```

### **2. Trier les données**
| Méthode  | Description |
|----------|------------|
| **OrderBy()**  | Tri croissant |
| **OrderByDescending()**  | Tri décroissant |
| **ThenBy()**  | Tri secondaire en ordre croissant |
| **ThenByDescending()**  | Tri secondaire en ordre décroissant |

#### **Exemple**
```csharp
List<string> names = new List<string> { "Paul", "Anna", "Zoe", "John" };
var sortedNames = names.OrderBy(n => n);
foreach (var name in sortedNames)
{
    Console.WriteLine(name);
}
// Affiche : Anna, John, Paul, Zoe
```

### **3. Regrouper des données**
| Méthode  | Description |
|----------|------------|
| **GroupBy()**  | Regrouper par une clé |
| **ToDictionary()**  | Convertir en dictionnaire |

#### **Exemple**
```csharp
var students = new List<(string Name, string Class)>
{
    ("Alice", "Math"), ("Bob", "Math"), ("Charlie", "Physics"), ("David", "Physics")
};

var groupedStudents = students.GroupBy(s => s.Class);

foreach (var group in groupedStudents)
{
    Console.WriteLine($"Classe : {group.Key}");
    foreach (var student in group)
    {
        Console.WriteLine(student.Name);
    }
}
```

### **4. Manipulation d’ensembles**
| Méthode  | Description |
|----------|------------|
| **Union()**  | Union de deux listes (sans doublons) |
| **Intersect()**  | Intersection de deux listes |
| **Except()**  | Différence entre deux listes |

#### **Exemple**
```csharp
int[] set1 = { 1, 2, 3, 4, 5 };
int[] set2 = { 4, 5, 6, 7, 8 };

var union = set1.Union(set2); // {1, 2, 3, 4, 5, 6, 7, 8}
var intersection = set1.Intersect(set2); // {4, 5}
var except = set1.Except(set2); // {1, 2, 3}
```

### **5. Agrégation**
| Méthode  | Description |
|----------|------------|
| **Sum()**  | Calcul de la somme |
| **Average()**  | Calcul de la moyenne |
| **Count()**  | Nombre d’éléments |
| **Min() / Max()**  | Valeur minimale/maximale |

#### **Exemple**
```csharp
int[] numbers = { 1, 2, 3, 4, 5, 6, 7, 8 };
Console.WriteLine(numbers.Sum()); // 36
Console.WriteLine(numbers.Average()); // 4.5
```

---

## **LINQ To Objects, LINQ To SQL et LINQ To Entities**
| Type de LINQ  | Utilisation |
|--------------|------------|
| **LINQ to Objects** | Manipulation de collections en mémoire (`List<>`, `Array`, etc.) |
| **LINQ to SQL** | Requêtes sur une base de données SQL Server |
| **LINQ to Entities** | Utilisé avec Entity Framework pour interagir avec une base de données relationnelle |

#### **Exemple LINQ to SQL**
```csharp
DataClasses1DataContext db = new DataClasses1DataContext();
var personnes = from perso in db.Personne select perso;

foreach (var p in personnes)
{
    Console.WriteLine($"{p.Nom} {p.Prenom}");
}
```

---

## **Résumé des notions clés**
- **LINQ simplifie l'accès aux données** avec une syntaxe lisible et puissante.
- **Deux syntaxes disponibles** : `Query Syntax` et `Method Syntax`.
- **Différentes méthodes LINQ** permettent de **filtrer, trier, grouper, agréger et manipuler des ensembles**.
- **LINQ est utilisé avec différents types de sources** (`List<T>`, `SQL`, `Entity Framework`).
- **Pensez aux exceptions possibles** avec `First()`, `Single()`, `Intersect()` et autres méthodes.

---

Avec cette fiche, tu as tous les éléments essentiels pour ton partiel ! 🚀 N’hésite pas à tester les exemples en C# pour bien comprendre le fonctionnement de LINQ. 💡
