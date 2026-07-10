# Projet 1 : Serveur Web Statique avec Nginx sur Ubuntu Server

## Description
Déploiement d'un serveur web statique Nginx sur Ubuntu Server 22.04 LTS
dans un environnement virtualisé VirtualBox — Projet de stage ISI Kef.

## Objectifs
- Installer et configurer un serveur web Nginx
- Sécuriser l'accès avec le pare-feu UFW
- Déployer une page HTML statique
- Tester l'accès depuis un navigateur externe

## Technologies utilisées
|     Outil     |  Version  |           Rôle         |
|---------------|-----------|------------------------|
| Ubuntu Server | 22.04 LTS | Système d'exploitation |
| Nginx         | 1.18+ -   | Serveur web            |
| UFW           |     -     | Pare-feu               |
| VirtualBox    | 7.x       | Virtualisation         |

## Architecture
```
PC Windows (Chrome)
       |
       | http://10.90.176.140
       |
  VirtualBox (mode Bridged)
       |
  VM Ubuntu Server 22.04
       |
  Nginx (port 80)
       |
  /var/www/html/index.html
```

## Étapes d'installation

### 1. Mise à jour du système
```bash
sudo apt update && sudo apt upgrade -y
```
### 2. Installation de Nginx
```bash
sudo apt install nginx -y
sudo systemctl enable nginx
sudo systemctl start nginx
```

### 3. Configuration du pare-feu UFW
```bash
sudo ufw allow 'Nginx HTTP'
sudo ufw allow 22/tcp
sudo ufw enable
sudo ufw status
```

### 4. Déploiement de la page HTML
```bash
sudo nano /var/www/html/index.html
```
### 5. Vérification
```bash
sudo systemctl status nginx
curl http://localhost
hostname -I
```

## Résultat final
- Nginx actif et démarré automatiquement au boot
- Pare-feu UFW configuré (HTTP autorisé)
- Page HTML accessible depuis Windows via `http://172.24.242.140`

## Compétences acquises
- Administration Linux (Ubuntu Server 22.04)
- Configuration serveur web (Nginx)
- Gestion des services systemd (systemctl)
- Sécurité périmétrique basique (UFW)
- Virtualisation réseau (VirtualBox modes NAT/Bridged)
