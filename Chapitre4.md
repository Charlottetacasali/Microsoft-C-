### **Fiche de Révision : Accès aux Bases de Données avec ADO.NET**

---

#### **1. Généralités sur l'Accès aux Bases de Données**
- **Pilotes** : Programmes qui permettent aux applications de communiquer avec les bases de données.
  - **ODBC** : Pour les bases de données.
  - **OLE DB** : Pour les bases de données, messageries, annuaires, etc.
- **Mode Connecté** : Connexion ouverte pendant l'exécution des requêtes.
- **Mode Déconnecté** : Copie des données en mémoire, connexion fermée pendant le traitement.

---

#### **2. ADO.NET**
- **Définition** : Successeur de ADO, une norme d'accès aux bases de données dans .NET.
- **Namespaces** :
  - `System.Data` : Classes de base pour les données.
  - `System.Data.SqlClient` : Pour SQL Server.
  - `System.Data.OleDb` : Pour les sources de données OLE DB.
- **Nouveautés** :
  - Meilleur support du mode déconnecté.
  - Utilisation de XML pour la persistance des données.

---

#### **3. Les Objets Principaux d'ADO.NET**
- **Connection** : Gère la connexion à la base de données.
  - **SqlConnection** : Pour SQL Server.
  - **OleDbConnection** : Pour les sources OLE DB.
  - **Méthodes** : `Open()`, `Close()`.
- **Command** : Exécute des requêtes SQL.
  - **SqlCommand** : Pour SQL Server.
  - **Méthodes** : `ExecuteReader()`, `ExecuteScalar()`, `ExecuteNonQuery()`.
- **DataReader** : Lit les données en mode connecté (lecture seule, avant seulement).
  - **SqlDataReader** : Pour SQL Server.
  - **Méthodes** : `Read()`, `Close()`.
- **DataSet** : Copie des données en mémoire (mode déconnecté).
  - **DataTable** : Représente une table.
  - **DataRelation** : Représente les relations entre les tables.
- **DataAdapter** : Remplit un `DataSet` et met à jour la base de données.
  - **SqlDataAdapter** : Pour SQL Server.
  - **Méthodes** : `Fill()`, `Update()`.

---

#### **4. Mode Connecté vs Mode Déconnecté**
- **Mode Connecté** :
  - Connexion ouverte pendant l'exécution des requêtes.
  - Utilise `DataReader` pour lire les données.
  - Idéal pour les opérations rapides et les données volumineuses.
- **Mode Déconnecté** :
  - Copie des données en mémoire (`DataSet`).
  - Connexion fermée pendant le traitement.
  - Idéal pour les applications Web et les mises à jour complexes.

---

#### **5. Exemples de Code**
- **Connexion à une Base de Données** :
  ```csharp
  string strConnection = @"Data Source=(LocalDB)\MSSQLLocalDB;Initial Catalog=Students;Integrated Security=True";
  SqlConnection connection = new SqlConnection(strConnection);
  connection.Open();
  Console.WriteLine("Connexion ouverte");
  connection.Close();
  ```

- **Exécution d'une Requête avec Command** :
  ```csharp
  string query = "SELECT * FROM Student";
  SqlCommand command = new SqlCommand(query, connection);
  SqlDataReader reader = command.ExecuteReader();
  while (reader.Read()) {
      Console.WriteLine(reader["Name"].ToString());
  }
  reader.Close();
  ```

- **Remplissage d'un DataSet avec DataAdapter** :
  ```csharp
  SqlDataAdapter adapter = new SqlDataAdapter(query, connection);
  DataSet dataSet = new DataSet();
  adapter.Fill(dataSet, "Students");
  ```

---

#### **6. Utilisation de DataGridView**
- **Affichage des Données** : Relier un `DataGridView` à un `DataSet`.
  ```csharp
  dataGridView.DataSource = dataSet.Tables["Students"];
  ```
- **Mise à Jour des Données** : Utiliser `DataAdapter` pour mettre à jour la base de données après modification dans le `DataSet`.
  ```csharp
  adapter.Update(dataSet, "Students");
  ```

---

#### **7. Gestion des Événements**
- **Événements de Connexion** : `Open`, `Close`.
- **Événements de DataReader** : `Read`, `Close`.
- **Événements de DataSet** : `Fill`, `Update`.

---

#### **8. Points à Retenir**
- **Connection** : Gère la connexion à la base de données.
- **Command** : Exécute les requêtes SQL.
- **DataReader** : Lit les données en mode connecté.
- **DataSet** : Stocke les données en mode déconnecté.
- **DataAdapter** : Remplit et met à jour un `DataSet`.
