### Fiche de Révision : Interfaces Graphiques avec C# et WinForms

#### 1. **Introduction à WinForms**
   - **WinForms** est une technologie de Microsoft pour créer des interfaces graphiques (GUI) en C#.
   - Les interfaces sont construites à l'aide de **Forms** (fenêtres) et de **Controls** (composants comme les boutons, les zones de texte, etc.).
   - Les interactions entre l'utilisateur et l'interface sont gérées via des **événements** (comme un clic sur un bouton).

#### 2. **Création d'un Projet WinForms**
   - Pour créer une application WinForms, on utilise Visual Studio.
   - **Étape 1** : Créer un nouveau projet de type **Application Windows Forms**.
   - **Étape 2** : Une fois le projet créé, Visual Studio génère automatiquement une fenêtre principale (`Form1`) sur laquelle vous pouvez glisser des composants depuis la **Toolbox** (boîte à outils).

#### 3. **Structure d'une Application WinForms**
   - **Form** : La fenêtre principale de l'application. C'est sur cette fenêtre que vous placez les composants.
   - **Controls** : Les éléments visuels comme les boutons (`Button`), les zones de texte (`TextBox`), les étiquettes (`Label`), etc.
   - **Événements** : Les actions de l'utilisateur (comme un clic) déclenchent des événements que vous pouvez gérer dans le code.

#### 4. **Événements Principaux d'un Formulaire**
   - **Load** : Se produit lorsque le formulaire est en cours de chargement (avant d'être affiché).
   - **Closing** : Se produit lorsque l'utilisateur essaie de fermer la fenêtre. Vous pouvez annuler la fermeture si nécessaire.
   - **Closed** : Se produit après que la fenêtre a été fermée.
   - **Resize** : Se produit lorsque l'utilisateur redimensionne la fenêtre.
   - **Click** : Se produit lorsque l'utilisateur clique sur la fenêtre.

#### 5. **La Classe MessageBox**
   - **MessageBox** est une classe qui permet d'afficher des messages à l'utilisateur dans une petite fenêtre.
   - **Méthode Show** : Affiche un message avec un titre, des boutons et une icône.
     ```csharp
     MessageBox.Show("Message", "Titre", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
     ```
   - **Boutons** : `OK`, `YesNo`, `YesNoCancel`, etc.
   - **Icônes** : `Information`, `Warning`, `Error`, `Question`, etc.

#### 6. **Composants Essentiels**
   - **TextBox** : Zone de saisie de texte. Vous pouvez récupérer le texte saisi avec `textBox.Text`.
   - **Label** : Étiquette pour afficher du texte statique.
   - **Button** : Bouton sur lequel l'utilisateur peut cliquer. L'événement `Click` est utilisé pour gérer les clics.
   - **ComboBox** : Liste déroulante avec une zone de saisie. L'événement `SelectedIndexChanged` est utilisé pour détecter un changement de sélection.
   - **CheckBox** : Case à cocher pour des options binaires (vrai/faux). L'événement `CheckedChanged` est utilisé pour détecter un changement d'état.
   - **RadioButton** : Bouton radio pour des choix exclusifs (un seul bouton peut être sélectionné dans un groupe).
   - **DateTimePicker** : Permet à l'utilisateur de sélectionner une date.
   - **MenuStrip** : Permet de créer des menus (comme "Fichier", "Édition", etc.).

#### 7. **Gestion des Événements**
   - **Événements Souris** :
     - **MouseEnter** : La souris entre dans la zone du contrôle.
     - **MouseLeave** : La souris quitte la zone du contrôle.
     - **MouseMove** : La souris bouge dans la zone du contrôle.
     - **MouseDown** : L'utilisateur appuie sur un bouton de la souris.
     - **MouseUp** : L'utilisateur relâche un bouton de la souris.
   - **Événements Clavier** :
     - **KeyDown** : Se produit lorsque l'utilisateur appuie sur une touche.
     - **KeyPress** : Se produit lorsque l'utilisateur appuie sur une touche de caractère.
     - **KeyUp** : Se produit lorsque l'utilisateur relâche une touche.

#### 8. **Exemple de Code**
   - **Gestion d'un clic sur un bouton** :
     ```csharp
     private void button1_Click(object sender, EventArgs e)
     {
         MessageBox.Show("Vous avez cliqué sur le bouton !");
     }
     ```
   - **Gestion d'un changement de texte dans une TextBox** :
     ```csharp
     private void textBox1_TextChanged(object sender, EventArgs e)
     {
         label1.Text = textBox1.Text; // Affiche le texte saisi dans un Label
     }
     ```

#### 9. **Propriétés et Méthodes des Formulaires**
   - **Propriétés** :
     - **Text** : Le titre de la fenêtre.
     - **Size** : La taille de la fenêtre.
     - **Location** : La position de la fenêtre à l'écran.
     - **WindowState** : L'état de la fenêtre (normal, minimisé, maximisé).
   - **Méthodes** :
     - **Show()** : Affiche la fenêtre.
     - **Hide()** : Masque la fenêtre.
     - **Close()** : Ferme la fenêtre.

#### 10. **Création de Menus**
   - Utilisez le composant **MenuStrip** pour créer des menus.
   - Ajoutez des options de menu (`ToolStripMenuItem`) et gérez leurs événements `Click`.
   - Exemple :
     ```csharp
     private void menuItem_Click(object sender, EventArgs e)
     {
         MessageBox.Show("Option de menu cliquée !");
     }
     ```

#### 11. **Conseils pour le Partiel**
   - **Comprendre les événements** : Les événements sont au cœur des applications WinForms. Assurez-vous de comprendre comment les gérer (clic, changement de texte, etc.).
   - **Manipuler les composants** : Savoir comment récupérer et modifier les propriétés des composants (comme `Text`, `Checked`, etc.).
   - **Utiliser MessageBox** : C'est un outil simple pour afficher des messages à l'utilisateur.
   - **Pratiquer** : Créez de petites applications pour vous familiariser avec les différents composants et événements.

---

### Conclusion
WinForms est une technologie puissante pour créer des interfaces graphiques en C#. En maîtrisant les concepts de base comme les composants, les événements, et la gestion des interactions utilisateur, vous serez capable de créer des applications Windows fonctionnelles et interactives. Bonne révision et bon courage pour votre partiel !
