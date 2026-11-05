# VPN Configuration

## Objectif
Configurer VPN site-to-site et client-to-site (IPsec, WireGuard, OpenVPN) sécurisés et performants.

## Quand l'utiliser (triggers)
- « VPN », « IPsec », « WireGuard », « OpenVPN », « tunnel chiffré », « remote access ».
- Connexion sécurisée sites distants ou remote workers.
- Remplacement VPN legacy (PPTP interdit).

## Hors périmètre
- Firewall rules → skill Firewall Rule Design.
- Architecture réseau complète → networkFirewall (autre skill).
- Cloud VPN (AWS Site-to-Site VPN, Azure VPN Gateway) → l'agent d'architecture cloud (IaC provisioning).

## Inputs requis
- Type VPN (site-to-site, client-to-site).
- Protocole (IPsec IKEv2, WireGuard, OpenVPN).
- Endpoints (public IPs, subnets privés).
- Encryption (AES-256, ChaCha20).

## Sorties attendues
- Configuration VPN (ipsec.conf, wg0.conf, openvpn.conf).
- Certificats/clés (WireGuard keys, OpenVPN CA/certs).
- Tests tunnel (ping cross-subnet, traffic encrypted).
- Runbook troubleshooting VPN (tunnel down, MTU issues).

## Workflow recommandé
1. **WireGuard (preferred, performance)** :
   - Générer clés : wg genkey | tee privatekey | wg pubkey > publickey.
   - Config serveur /etc/wireguard/wg0.conf :
     ```
     [Interface]
     PrivateKey = <server_private_key>
     Address = 10.0.0.1/24
     ListenPort = 51820
     
     [Peer]
     PublicKey = <client_public_key>
     AllowedIPs = 10.0.0.2/32
     ```
   - Config client :
     ```
     [Interface]
     PrivateKey = <client_private_key>
     Address = 10.0.0.2/24
     
     [Peer]
     PublicKey = <server_public_key>
     Endpoint = <server_public_ip>:51820
     AllowedIPs = 10.0.0.0/24, 192.168.1.0/24  # subnets accessibles via tunnel
     PersistentKeepalive = 25
     ```
   - Activer : wg-quick up wg0, systemctl enable wg-quick@wg0.
2. **IPsec IKEv2** (interopérabilité) : strongSwan config /etc/ipsec.conf.
3. **OpenVPN** (legacy, compatibilité) : server.conf, client.ovpn, CA certs.
4. Tests : ping 10.0.0.1 (serveur), tcpdump (vérifier traffic encrypted).

## Garde-fous
- Encryption forte (AES-256/ChaCha20, pas 3DES legacy).
- MTU adjusted (WireGuard 1420, IPsec 1400 si fragmentation).
- Firewall allow VPN (UDP 51820 WireGuard, UDP 500/4500 IPsec).
- DNS over VPN (force DNS WireGuard AllowedIPs, éviter DNS leaks).
- Keepalive (PersistentKeepalive 25 WireGuard, DPD IPsec).

## Template d'entrée (copier/coller)
```text
[VPN]
- Type : ...
- Protocole : ...
- Endpoints : ...

[Subnets]
- Privés accessibles : ...
```

## Template de sortie (copier/coller)
```text
[Configuration]
- Fichiers : ...
- Clés/certs : ...

[Tests]
- Tunnel up : ...
- Ping : ...
- Traffic encrypted : ...
```

## Checklist QA interne
- Encryption forte (AES-256/ChaCha20).
- MTU adjusted si nécessaire.
- Firewall allow VPN ports.
- DNS over VPN (pas leaks).
- Tests ping cross-subnet OK.

## KPI reliés
- Latency VPN (ms added vs direct).
- Throughput VPN (Mbps).
- Taux uptime tunnel (%).

## Definition of done
- VPN configuré et testé.
- Tunnel up, traffic encrypted.
- Runbook troubleshooting publié.

## Exemples d'usage

### Exemple 1 : [Titre du cas d'usage]
**Contexte** : [Description de la situation]
**Action** : [Ce qui a été fait]
**Résultat** : [Résultat obtenu]