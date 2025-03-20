### Fiche de Révision : Accès aux Bases de Données avec ADO.NET

#### 1. **Généralités sur les Bases de Données et les Pilotes**
   - **Bases de données** : Les bases de données sont des systèmes de stockage et de gestion de données. Sur Windows, il existe de nombreuses bases de données (comme SQL Server, Oracle, etc.).
   - **Pilotes (Drivers)** : Pour accéder à une base de données, les applications utilisent des **pilotes**. Ces pilotes agissent comme des intermédiaires entre l'application et la base de données.
     - **Interface I1** : Côté application, le pilote présente une interface normalisée (I1) qui permet à l'application de communiquer avec la base de données.
     - **Interface I2** : Côté base de données, l'interface (I2) est spécifique à la base de données utilisée (propriétaire).
   - **Normalisation** : L'interface I1 est normalisée, ce qui permet de changer de base de données sans modifier l'application. Par contre, l'interface I2 est propre à chaque base de données.

#### 2. **Types de Pilotes Normalisés**
   - **ODBC (Open DataBase Connectivity)** : Un pilote ODBC permet d'accéder uniquement aux bases de données. Il est largement utilisé pour les applications qui doivent interagir avec plusieurs types de bases de données.
   - **OLE DB (Object Linking and Embedding DataBase)** : Un pilote OLE DB permet d'accéder à différentes sources de données, pas seulement des bases de données (par exemple, des messageries, des annuaires, etc.).

#### 3. **Modes de Connexion**
   - **Mode Connecté** :
     - L'application ouvre une connexion avec la base de données.
     - Elle travaille directement avec la base de données en lecture/écriture.
     - Une fois le travail terminé, la connexion est fermée.
     - **Avantages** : Gestion simple des mises à jour simultanées par plusieurs utilisateurs.
     - **Inconvénients** : La connexion reste ouverte pendant toute la durée de l'interaction, ce qui peut consommer des ressources système.

   - **Mode Déconnecté** :
     - L'application ouvre une connexion, récupère une copie des données en mémoire, puis ferme la connexion.
     - L'application travaille avec la copie mémoire des données.
     - Une fois les modifications terminées, la connexion est rouverte pour mettre à jour la base de données.
     - **Avantages** : Réduit la durée des connexions, ce qui est utile pour les applications avec beaucoup d'utilisateurs simultanés.
     - **Inconvénients** : Gestion plus complexe des mises à jour simultanées.

#### 4. **Accès aux Bases de Données avec .NET**
   - **.NET** propose deux types de classes pour accéder aux données :
     - **SQL Server.NET** : Ces classes permettent un accès direct à SQL Server sans passer par un pilote intermédiaire.
     - **Ole Db.NET** : Ces classes permettent d'accéder à des sources de données via des pilotes OLE DB.

#### 5. **ADO.NET**
   - **ADO.NET** est la technologie d'accès aux bases de données dans le framework .NET. C'est une collection de classes, interfaces, et structures organisées dans des espaces de noms comme `System.Data`, `System.Data.OleDb`, `System.Data.SqlClient`, etc.
   - **Nouveautés d'ADO.NET** :
     - **Architecture optimisée** : ADO.NET utilise des fournisseurs de données natifs, ce qui supprime des couches intermédiaires et améliore les performances.
     - **Support du mode déconnecté** : ADO.NET encourage l'utilisation du mode déconnecté, notamment pour les applications web où les connexions doivent être courtes.
     - **Support de XML** : ADO.NET utilise XML comme format de transmission universel des données, ce qui facilite l'échange de données entre différents systèmes.

#### 6. **Fournisseurs de Données .NET**
   - Pour utiliser ADO.NET, il faut inclure une référence à l'espace de noms correspondant au fournisseur de données utilisé. Par exemple :
     - `System.Data.SqlClient` : Pour SQL Server.
     - `System.Data.OleDb` : Pour les sources de données OLE DB.
     - `System.Data.Odbc` : Pour les sources de données ODBC.
     - `System.Data.OracleClient` : Pour Oracle.

#### 7. **Modèle Objet ADO.NET**
   - **Connection** : Ouvre une connexion vers une source de données.
   - **Command** : Exécute des commandes SQL sur la base de données.
   - **DataReader** : Permet de lire un flux de données en mode connecté (lecture seule, curseur en avant seulement).
   - **DataSet** : Représente une copie mémoire des données en mode déconnecté. Il peut contenir plusieurs tables, relations, et contraintes.
   - **DataAdapter** : Remplit un DataSet avec des données et met à jour la base de données avec les modifications apportées au DataSet.

#### 8. **Exemples d'Utilisation**
   - **Connection** : Pour ouvrir une connexion à une base de données SQL Server, on utilise `SqlConnection`. Exemple :
     ```csharp
     SqlConnection connection = new SqlConnection("connectionString");
     connection.Open();
     ```
   - **Command** : Pour exécuter une commande SQL, on utilise `SqlCommand`. Exemple :
     ```csharp
     SqlCommand command = new SqlCommand("INSERT INTO Student VALUES (1, 'John', 'Doe')", connection);
     command.ExecuteNonQuery();
     ```
   - **DataReader** : Pour lire des données en mode connecté, on utilise `SqlDataReader`. Exemple :
     ```csharp
     SqlDataReader reader = command.ExecuteReader();
     while (reader.Read())
     {
         Console.WriteLine(reader["Name"]);
     }
     ```
   - **DataSet** : Pour travailler en mode déconnecté, on utilise `DataSet`. Exemple :
     ```csharp
     DataSet dataSet = new DataSet();
     SqlDataAdapter adapter = new SqlDataAdapter("SELECT * FROM Student", connection);
     adapter.Fill(dataSet, "Student");
     ```

#### 9. **DataAdapter**
   - **DataAdapter** sert de pont entre un `DataSet` et une source de données. Il permet de remplir un `DataSet` avec des données et de mettre à jour la base de données avec les modifications apportées au `DataSet`.
   - **Propriétés** :
     - `SelectCommand` : Récupère des données.
     - `InsertCommand` : Insère des données.
     - `UpdateCommand` : Met à jour des données.
     - `DeleteCommand` : Supprime des données.

#### 10. **Exemple Complet avec DataSet et DataAdapter**
   - **Remplissage d'un DataSet** :
     ```csharp
     SqlDataAdapter adapter = new SqlDataAdapter("SELECT * FROM Student", connection);
     DataSet dataSet = new DataSet();
     adapter.Fill(dataSet, "Student");
     ```
   - **Mise à jour de la base de données** :
     ```csharp
     adapter.Update(dataSet, "Student");
     ```

#### 11. **Affichage des Données dans un DataGridView**
   - Pour afficher les données d'un `DataSet` dans un `DataGridView`, on utilise la propriété `DataSource` :
     ```csharp
     dataGridView.DataSource = dataSet.Tables["Student"];
     ```

#### 12. **Gestion des Connexions**
   - Toujours fermer les connexions après utilisation pour libérer les ressources :
     ```csharp
     connection.Close();
     ```

---

### Conclusion
ADO.NET est une technologie puissante pour accéder aux bases de données en mode connecté ou déconnecté. Les principaux objets à retenir sont `Connection`, `Command`, `DataReader`, `DataSet`, et `DataAdapter`. Le mode déconnecté est particulièrement utile pour les applications web où les connexions doivent être courtes. En comprenant ces concepts, vous serez en mesure de manipuler des bases de données efficacement avec .NET.
