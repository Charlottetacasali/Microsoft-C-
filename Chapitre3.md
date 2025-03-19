### **Fiche de Révision : Interfaces Graphiques avec C# et WinForms**

---

#### **1. Introduction à WinForms**
- **Objectif** : Créer des interfaces utilisateur visuelles en C#.
- **Événements** : Les interactions entre l'interface et l'utilisateur sont gérées via des événements (ex : clics, saisie de texte).

---

#### **2. Création d'un Projet WinForms**
- **Étape 1** : Créer un projet de type **Application Windows Forms** dans Visual Studio.
- **Étape 2** : Glisser-déposer des composants (contrôles) depuis la **Toolbox** sur le formulaire (Form).
- **Étape 3** : Gérer les événements des composants (ex : clic sur un bouton).

---

#### **3. Structure d'une Application WinForms**
- **Form** : La fenêtre principale de l'application. Elle hérite de la classe `Form`.
- **Méthode `Main`** : Point d'entrée de l'application. Elle lance le formulaire principal.
  ```csharp
  static void Main() {
      Application.Run(new Form1());
  }
  ```

---

#### **4. Les Événements du Formulaire**
- **Load** : Se produit avant l'affichage du formulaire.
- **Closing** : Se produit lorsque le formulaire est en cours de fermeture (peut être annulé).
- **Closed** : Se produit après la fermeture du formulaire.
- **Exemple** :
  ```csharp
  private void Form1_Load(object sender, EventArgs e) {
      MessageBox.Show("Formulaire en cours de chargement");
  }
  ```

---

#### **5. La Classe MessageBox**
- **Utilisation** : Afficher des messages à l'utilisateur.
- **Syntaxe** :
  ```csharp
  MessageBox.Show("Message", "Titre", MessageBoxButtons.YesNo, MessageBoxIcon.Question);
  ```
- **Boutons** : `OK`, `YesNo`, `YesNoCancel`, etc.
- **Icônes** : `Information`, `Warning`, `Error`, `Question`.

---

#### **6. Les Composants Essentiels**
- **Label** : Affiche du texte.
- **TextBox** : Champ de saisie de texte.
- **Button** : Bouton cliquable.
- **ComboBox** : Liste déroulante.
- **CheckBox** : Case à cocher.
- **RadioButton** : Bouton radio (sélection exclusive).
- **DateTimePicker** : Sélection de date.
- **MenuStrip** : Barre de menu.

---

#### **7. Gestion des Événements des Composants**
- **Exemple avec un Button** :
  ```csharp
  private void button1_Click(object sender, EventArgs e) {
      MessageBox.Show("Bouton cliqué !");
  }
  ```
- **Exemple avec un TextBox** :
  ```csharp
  private void textBox1_TextChanged(object sender, EventArgs e) {
      label1.Text = textBox1.Text; // Affiche le texte saisi dans un Label
  }
  ```

---

#### **8. Propriétés et Méthodes des Composants**
- **TextBox** :
  - `Multiline` : Permet plusieurs lignes de texte.
  - `ScrollBars` : Ajoute des barres de défilement.
  - `Text` : Contenu du champ de saisie.
- **ComboBox** :
  - `DropDownStyle` : Style de la liste déroulante.
  - `SelectedIndexChanged` : Événement déclenché lors du changement de sélection.
- **CheckBox et RadioButton** :
  - `Checked` : État de la case à cocher ou du bouton radio.
  - `CheckChanged` : Événement déclenché lors du changement d'état.

---

#### **9. Les Menus**
- **MenuStrip** : Permet de créer des barres de menus.
- **Événements** : Gérer les clics sur les options du menu.
  ```csharp
  private void menuItem_Click(object sender, EventArgs e) {
      MessageBox.Show("Option de menu cliquée");
  }
  ```

---

#### **10. Les Événements Souris et Clavier**
- **Événements Souris** :
  - `MouseEnter` : La souris entre dans le contrôle.
  - `MouseLeave` : La souris quitte le contrôle.
  - `MouseClick` : Clic de souris sur le contrôle.
- **Événements Clavier** :
  - `KeyDown` : Touche enfoncée.
  - `KeyUp` : Touche relâchée.
  - `KeyPress` : Touche de caractère pressée.

---

#### **11. Exemple Pratique**
- **Création d'un formulaire simple** :
  - Ajouter un `TextBox`, un `Label`, et un `Button`.
  - Gérer l'événement `Click` du bouton pour afficher le texte saisi dans le `Label`.
  ```csharp
  private void button1_Click(object sender, EventArgs e) {
      label1.Text = textBox1.Text;
  }
  ```
