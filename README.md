

# 🧠 `lanceur.sh` — IA du dev : détecte, compile, lance

![lanceur](https://img.shields.io/badge/lanceur-IA%20du%20dev-00C4B4?style=for-the-badge&logo=bash)
![C++](https://img.shields.io/badge/C%2B%2B-17-blue?style=flat&logo=c%2B%2B)
![Bash](https://img.shields.io/badge/Bash-4.0%2B-89CFF0?style=flat&logo=gnu-bash)

Un script Bash **sobre et intelligent** pour compiler automatiquement vos fichiers C++.  
Il **détecte les bibliothèques utilisées dans le code**, compile avec les bons liens, et **lance l’exécutable**.

> **Pensé pour les développeurs artisanaux, les formateurs techniques, et les explorateurs de projets modulaires.**

---

## ✨ Fonctionnalités

- 🔍 Détection automatique des bibliothèques (`SFML`, `Boost.Asio`, `Poco`)  
- 🧱 Création d’un projet minimal si aucun `.cpp` n’est présent  
- 🛠️ Compilation modulaire avec `g++ -std=c++17 -O2`  
- 🚀 Lancement automatique de l’exécutable après compilation  
- 📚 Usage pédagogique : chaque étape est claire, commentée, et traçable  

---

## 📦 Dépendances

| Outil                  | Requis si utilisé |
|------------------------|------------------|
| `bash`                 | ✅ Oui            |
| `g++` (C++17)          | ✅ Oui            |
| `libsfml-dev`          | Si SFML détecté  |
| `libboost-system-dev` | Si Boost détecté |
| `libpoco-dev`          | Si Poco détecté  |

> *Installez-les avec votre gestionnaire de paquets (`apt`, `brew`, `pacman`, etc.)*

---

## 🧪 Utilisation

### 🔹 Compilation + lancement automatique
```bash
./lanceur
```

### 🔹 Création d’un projet minimal
```bash
./lanceur init
```

### 🔹 Exemple réel

```cpp
// main.cpp
#include <SFML/Graphics.hpp>
#include <iostream>

int main() {
    sf::RenderWindow window(sf::VideoMode(800, 600), "lanceur magique");
    std::cout << "SFML détecté automatiquement !\n";
    while (window.isOpen()) {
        sf::Event e;
        while (window.pollEvent(e))
            if (e.type == sf::Event::Closed) window.close();
        window.clear(sf::Color::Black);
        window.display();
    }
}
```

```bash
$ ./lanceur
Analyse du code...
SFML détecté
Compilation → go
Libs détectées : sfml-graphics sfml-window sfml-system
→ g++ -std=c++17 -Wall -Wextra -O2 main.cpp -o go -lsfml-graphics -lsfml-window -lsfml-system
Compilation OK

Lancement de ./go...
SFML détecté automatiquement !
[fenêtre SFML s'ouvre]
```

---

## 🧱 Structure interne

| Étape       | Fonction         | Description                                      |
|-------------|------------------|--------------------------------------------------|
| 1️⃣ Détection | `detect_libs()`  | Analyse les `.cpp` avec `grep` pour détecter les libs |
| 2️⃣ Init      | `init_project()` | Crée un `main.cpp` minimal avec `cat << EOF`     |
| 3️⃣ Compile   | `compile()`      | Construit `CMD=()` et compile proprement         |
| 4️⃣ Lancement | `launch()`       | Exécute `./go` et affiche le code retour         |

---

## 🚀 Installation

```bash
git clone https://github.com/mathieu-karim/lanceur.git
cd lanceur
chmod +x lanceur
./lanceur init    # première fois
./lanceur         # et c’est parti !
```

---

## 📁 .gitignore recommandé

```
# lanceur
go
*.o
*.out
```

---

## 🤝 Contribuer

Tu veux ajouter :
- `raylib` ?
- `SDL2` ?
- Un mode "montre" ?
- Un nouveau jeu de lanceur ?

Ouvre une issue ou une PR — on code ensemble.

---

## ✍️ Signature

> Créé avec soin par **SMK**  
> Accompagné de **GitHub Copilot**  
> Et de **Grok** — l’IA qui code avec toi, pas pour toi.  
>  
> _"Parce que g++ c’est bien. Mais lanceur, c’est mieux."_  
> Made with 🧠, 🛠️, et un peu de magie IA.

---

## 🏷️ Bonus : Badges GitHub





