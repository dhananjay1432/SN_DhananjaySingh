# SN_DhananjaySingh
# 🌐 Personal Home Cloud with Secure Multi-Level Access  

A **systems & networking project** that builds a private, family-oriented **home cloud server** with **secure remote access** and **role-based permissions**.  
Designed to protect sensitive data while providing a smooth, Nextcloud-powered user experience.  

---

## 🚀 Key Highlights  
- 🔐 **Role-Based Access Control (RBAC)** → Different roles (Owner, Family, Guest) with custom permissions.  
- 🌍 **Secure Remote Access** → WireGuard VPN + Traefik reverse proxy with HTTPS.  
- 🗄️ **Data Security** → ZFS for integrity + LUKS for full-disk encryption.  
- 🐳 **Reproducible Setup** → Docker Compose deployment for simplicity.  
- 📊 **Monitoring** → ZFS snapshots & Grafana dashboards for system health.  

---

## 🛠️ Technology Stack  
- **[Nextcloud](https://nextcloud.com/):** File management, syncing, and sharing.  
- **[Keycloak](https://www.keycloak.org/):** Identity and access management.  
- **[WireGuard](https://www.wireguard.com/):** Lightweight VPN for secure tunneling.  
- **[Traefik](https://traefik.io/):** Reverse proxy & automated HTTPS with Let’s Encrypt.  
- **[ZFS + LUKS](https://openzfs.org/):** Encrypted and reliable data storage.  
- **[Docker Compose](https://docs.docker.com/compose/):** Easy container orchestration.  

---

## 🏗️ High-Level Architecture  


**Flow:**  
1. Users (Owner, Family, Guest) connect via **WireGuard VPN**.  
2. **Traefik** handles HTTPS routing and SSL certificates.  
3. **Keycloak** manages authentication and role-based access.  
4. **Nextcloud** provides the main storage and sharing interface.  
5. Data is stored securely with **ZFS + LUKS encryption**.  

---

## ⚖️ Trade-offs & Future Improvements  
**Pros**  
- Full privacy and security.  
- RBAC with granular access.  
- Professional and reproducible deployment.  

**Cons**  
- Single-node setup (no HA).  
- Docker/Linux familiarity required.  
- ZFS overhead on low-memory devices.  

**Future Enhancements**  
- Kubernetes orchestration.  
- Distributed storage (GlusterFS/Ceph).  
- IDS/IPS integration for stronger monitoring.  


## 🎥 Demo Plan  
1. **Overview:** Walk through architecture.  
2. **Role-Based Login:** Show Owner, Family, Guest with different permissions.  
3. **Secure Access:** Connect via WireGuard and access Nextcloud.  
4. **Guest Link:** Generate and use a time-limited share link.  
5. **Monitoring:** Show Grafana dashboard + ZFS snapshots.  

---

## 📂 Repository Structure  

