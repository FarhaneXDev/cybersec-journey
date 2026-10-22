# Linux Cheatcheet

## Navigation

### pwd
Affiche le chemin absolu du dossier courant. Elle (la commande) permet donc de se retrouver dans l'arborescence et est utile pour écrire des chemins absolus

---

### whoami
Comme son nom l'indique elle permet de savoir au nom de quel utilisateur l'on est connecté sur le système. Pour exécuter certains programme l'on a besoin d'être l'utilisateur principal (root) donc utile pour savoir avant de démarrer n'importe quoi 

---

### ls
Liste le contenu d'un dossier
Utilisée avec -l elle permet d'avoir le format détaillé (permissions, propriétaire, taille date)
Avec -a elle affiche aussi les fichiers cachés, ceux commençant par un point comme .xxx
Donc -la combinés donnent a la fois les permission et les fichiers cachés 

---

### cd
Change de dossier courant(change directory)
cd /var/www pointe vers /var/www
cd .. remonte d'un niveau dans l'arborescence des fichiers
cd - revient au répertoire visité précédemment
cd ~ retourne au dossier personnel

---

### --help
Cette commande s'utilise après des commandes principales pour obtenir une courte description et le guide d'utilisation de cette commande qui la précède. Ex: ls --help
-h est son modèle court

---

### man
Avec cette commande tapée au début d'un autre on a accès a un manuel (man comme son nom l'indique) avec plus d'information concernant la commande. Ex: man aircrack-ng

---

### locate
Suivi d'un mot clé (ou commande clé) elle permet de trouver dans l'entièreté des fichiers systèmes la localisation du mot clé tapé et d'écrire son path (
Ex: locate aircrack-ng

---

### whereis 
Permet de retrouver un binaire avec son path exactement au lieu de tout ls mot clé qui réfèrent à lui dans les fichiers systeme

---

### which
Affiche le chemin exact de l'exécutable qui sera lancé quand on tape une commande. Elle cherche uniquement dans les dossiers listés dans le PATH, donc elle répond à la question "quelle version de cette commande est utilisée ?"
Ex: which python3 donne /usr/bin/python3
Différence avec whereis : whereis donne le binaire mais aussi son manuel et ses sources, which donne seulement celui qui sera réellement exécuté
Si elle n'affiche rien c'est que la commande n'est pas installée ou pas dans le PATH

---

### find
Cherche des fichiers ou dossiers en parcourant l'arborescence en temps réel à partir d'un dossier de départ (contrairement à locate qui utilise une base de données pré-indexée, find est plus lent mais toujours à jour)
Syntaxe : find [où chercher] [critère]
find . -name "notes.txt" cherche un fichier par son nom dans le dossier courant et ses sous-dossiers
find /var -name "*.log" cherche tous les fichiers finissant par .log dans /var (le * remplace n'importe quoi)
-type f ne garde que les fichiers et -type d que les dossiers
Ex: find ~ -type d -name "projets" cherche un dossier nommé projets dans le dossier personnel

---

### grep
Cherche un texte à l'intérieur des fichiers (find cherche les fichiers, grep cherche ce qu'il y a dedans). Elle affiche chaque ligne qui contient le mot recherché
Ex: grep "error" app.log
-i ignore la casse (majuscule/minuscule)
-r cherche récursivement dans tous les fichiers d'un dossier
-n affiche le numéro de la ligne
Ex: grep -rn "password" . cherche "password" dans tous les fichiers du dossier courant en montrant la ligne
Elle s'utilise aussi très souvent après un pipe | pour filtrer le résultat d'une autre commande. Ex: ls -la | grep ".txt"

---

### ps
Affiche les processus (programmes en cours d'exécution) sur le système, chacun avec son PID (identifiant du processus)
ps seule montre seulement les processus du terminal actuel
ps aux montre tous les processus de tous les utilisateurs avec détails (utilisateur, CPU, mémoire, commande)
Utile avec grep pour retrouver un programme précis. Ex: ps aux | grep python
Le PID récupéré sert ensuite à arrêter un processus avec kill

---

### cat >
cat affiche normalement le contenu d'un fichier. Avec le > (redirection) on inverse : ce que l'on tape est écrit dans un fichier
Ex: cat > notes.txt puis on tape son texte, et on termine avec Ctrl+D pour sauvegarder
Attention : > écrase le contenu existant du fichier. Pour ajouter à la suite sans rien effacer on utilise >> 
Ex: cat >> notes.txt

---

### touch
Crée un fichier vide s'il n'existe pas. Si le fichier existe déjà elle ne supprime rien, elle met juste à jour sa date de modification
Ex: touch index.html
On peut en créer plusieurs d'un coup. Ex: touch a.txt b.txt c.txt

---

### mkdir
Crée un dossier (make directory)
Ex: mkdir projets
-p permet de créer toute une arborescence d'un coup, même si les dossiers parents n'existent pas encore
Ex: mkdir -p projets/web/frontend

---

### cp
Copie un fichier ou un dossier (copy). Syntaxe : cp [source] [destination]
Ex: cp notes.txt backup.txt crée une copie sous un autre nom
cp notes.txt ~/Documents/ copie le fichier dans un autre dossier
Pour copier un dossier avec tout son contenu il faut -r (récursif). Ex: cp -r projets projets_backup

---

### mv
Déplace un fichier ou un dossier (move). Syntaxe : mv [source] [destination]
Elle sert aussi à renommer, car renommer revient à déplacer vers un nouveau nom
Ex: mv ancien.txt nouveau.txt renomme le fichier
Ex: mv notes.txt ~/Documents/ le déplace dans Documents
Contrairement à cp, l'original disparaît de son emplacement de départ

---

### rm
Supprime un fichier (remove). Attention : il n'y a pas de corbeille sous Linux, ce qui est supprimé avec rm est perdu définitivement
Ex: rm notes.txt
-r supprime un dossier et tout son contenu
-i demande confirmation avant chaque suppression (pratique pour éviter les erreurs)
-f force la suppression sans poser de question
Danger : rm -rf combiné avec un mauvais chemin peut détruire tout le système, donc toujours vérifier avec pwd et ls avant

---

### rmdir ou rm -r
rmdir supprime uniquement un dossier vide, si le dossier contient quelque chose elle refuse (c'est une sécurité)
Ex: rmdir dossier_vide
rm -r supprime un dossier même s'il n'est pas vide, avec tout ce qu'il contient
Ex: rm -r projets_backup

---

###