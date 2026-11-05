# Systemd Service Management

## Objectif
Maîtriser systemd pour gestion services Linux (création units, timers, dependencies, troubleshooting).

## Quand l'utiliser (triggers)
- « crée un service systemd », « configure timer », « dépendances services », « troubleshoot systemd ».
- Automatisation démarrage services au boot.
- Ordonnancement tâches (alternative cron via systemd timers).

## Hors périmètre
- Scripts Bash/Perl complexes → l'agent de scripting système.
- Conteneurs systemd (Quadlet) → l'agent de scripting système (spécialité Podman/Quadlet).
- Orchestration cloud (systemd cloud-init) → l'agent d'architecture cloud.

## Inputs requis
- Service à gérer (binaire, script, options démarrage).
- Dépendances (services prerequis, ordre démarrage).
- Stratégie restart (on-failure, always).
- Timer si nécessaire (périodicité cron-like ou calendar).

## Sorties attendues
- Fichier unit systemd (.service ou .timer + .service).
- Commandes systemctl (enable, start, status).
- Troubleshooting guide (journalctl logs, systemctl status).

## Workflow recommandé
1. Créer unit file /etc/systemd/system/myservice.service :
   ```
   [Unit]
   Description=...
   After=network.target
   
   [Service]
   Type=simple
   ExecStart=/path/to/binary
   Restart=on-failure
   
   [Install]
   WantedBy=multi-user.target
   ```
2. Reload systemd : systemctl daemon-reload.
3. Enable et start : systemctl enable --now myservice.
4. Vérifier status : systemctl status myservice, journalctl -u myservice.
5. Si timer : créer myservice.timer avec OnCalendar=... .

## Garde-fous
- Type correct (simple, forking, oneshot) selon binaire.
- Restart=on-failure pour robustesse production.
- Logs centralisés (journalctl -u service, forwarding syslog si nécessaire).
- User/Group non-root si possible (sécurité).

## Template d'entrée (copier/coller)
```text
[Service]
- Binaire/script : ...
- Dépendances : ...
- Restart policy : ...

[Timer si nécessaire]
- Périodicité : ...
```

## Template de sortie (copier/coller)
```text
[Unit file]
- Chemin : /etc/systemd/system/...
- Contenu : ...

[Commandes]
- systemctl enable --now ...

[Vérifications]
- systemctl status : ...
- journalctl : ...
```

## Checklist QA interne
- Unit file syntax valide (systemd-analyze verify myservice.service).
- Service démarre (systemctl start ok).
- Logs accessibles (journalctl -u service).
- Restart fonctionne si on-failure (kill process, vérifie restart auto).

## KPI reliés
- Taux succès démarrage service au boot (%).
- Temps moyen démarrage service (secondes).
- Nb restarts on-failure (monitoring).

## Definition of done
- Unit file créé et enabled.
- Service démarre au boot.
- Troubleshooting guide publié.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]