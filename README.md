# lab7_fonctions.py
# --- ÉTAPE 1 : Créer une fonction et l'appeler ---
def saluer():
    print("Bonjour depuis une fonction !")
    print("Ravi de te voir")  # Ajout demandé

print("--- Étape 1 ---")
saluer()
saluer()

# --- ÉTAPE 2 : Paramètres ---
def presentation(nom, age):
  print(f"Je m'appelle {nom} et j'ai {age} ans.")

print("\n--- Étape 2 ---")
presentation("Alice", 25)
presentation("Mohamed", 30)

# --- ÉTAPE 3 : Retourner un résultat ---
def additionner(a, b):
    total = a + b
    return total

print("\n--- Étape 3 ---")
resultat = additionner(3, 5)
print("Résultat de l'addition :", resultat)
print("Type du retour :", type(resultat))

# --- ÉTAPE 4 : Paramètres optionnels et arguments nommés ---
def calcul_ttc(prix_ht, taux=0.2):
    return prix_ht * (1 + taux)

def afficher_message(message, prefix="[INFO]"):
    print(f"{prefix} {message}")

print("\n--- Étape 4 ---")
print(f"Prix TTC (défaut 20%) : {calcul_ttc(100)}")
print(f"Prix TTC (taux 5.5%) : {calcul_ttc(100, 0.055)}")
afficher_message("Le calcul est terminé")
afficher_message("Accès refusé", prefix="[ERREUR]")

# --- ÉTAPE 5 : Nombre variable d'arguments (*args) ---
def somme(*args):
    total = 0
    for valeur in args:
        total += valeur
    return total

def produit(*args):
    if not args:
        return 1
    p = 1
    for n in args:
        p *= n
    return p

print("\n--- Étape 5 ---")
print("Somme multiple :", somme(1, 2, 3, 4))
print("Produit multiple :", produit(2, 3, 4))

# --- ÉTAPE 6 : Portée des variables ---
compteur = 0  # Variable globale

def incrementer_pur(valeur):
    return valeur + 1

print("\n--- Étape 6 ---")
compteur = incrementer_pur(compteur)
print("Compteur après incrémentation pure :", compteur)

# --- ÉTAPE 7 : MINI-PROJET (Gestion de classe) ---

def moyenne(notes):
    if not notes:
        return 0
    return sum(notes) / len(notes)

def appliquer_bonus(notes, bonus=1):
    return [min(note + bonus, 20) for note in notes]

def filtrer_notes(notes, seuil):
    return [note for note in notes if note >= seuil]

def rapport(notes, bonus=1, seuil=12, titre="Rapport des notes"):
    notes_bonus = appliquer_bonus(notes, bonus)
    notes_valides = filtrer_notes(notes, seuil)
  lignes = [
        f"=== {titre} ===",
        f"Notes originales : {notes}",
        f"Notes bonus (+{bonus}) : {notes_bonus}",
        f"Moyenne initiale : {moyenne(notes):.2f}",
        f"Moyenne bonus : {moyenne(notes_bonus):.2f}",
        f"Notes >= {seuil} : {notes_valides} (total {len(notes_valides)})"
    ]
    return "\n".join(lignes)

# --- TEST DU MINI-PROJET ---
if __name__ == "__main__":
    print("\n--- Étape 7 : Mini-Projet ---")
    mes_notes = [12, 9, 15, 8, 17, 13, 19, 10]
    print(rapport(mes_notes))
    print("\n" + rapport(mes_notes, bonus=2, seuil=14, titre="Rapport avancé"))
