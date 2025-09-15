# Personal Home Cloud with Secure Multi-Level Access  
### Systems & Networking Project Proposal  
**Name:** Dhananjay Singh  

---

## 1. The Problem  
Today, families rely on public cloud services to store their most sensitive data—photos, documents, and personal files. This practice compromises privacy and security. The clear need is for a **home-based cloud server** that provides secure, remote access while keeping data under the user's full control.

A key challenge is managing user permissions. An effective solution must offer **role-based access control (RBAC)**, ensuring that an Owner, Family member, or Guest can only access what they're explicitly allowed to. Data must be encrypted, recoverable, and accessible from anywhere **without exposing the home network** to attacks.

---

## 2. Key Project Goals  
- **Home Cloud Server** → A central, private server for all family data.  
- **Role-Based Access** → Differentiate permissions for Owners, Family, and Guests.  
- **Secure Remote Access** → Allow users to connect safely from outside the home.  
- **Data Security** → Ensure all data is encrypted and recoverable.  
- **Centralized Management** → Provide a single control panel for the system.  
- **Network Protection** → Implement security controls like a firewall and VPN.  

---

## 3. Proposed Solution & Technologies  
This project uses a combination of modern, open-source technologies to build a robust and secure personal cloud:

- **Nextcloud** → The primary user interface for file management, syncing, and sharing.  
- **Keycloak** → Manages all authentication and user roles (Owner, Family, Guest).  
- **WireGuard** → A fast and simple VPN for creating a secure tunnel for remote access.  
- **Traefik** → A reverse proxy that automates HTTPS, simplifying routing and securing the system with automatic SSL certificates from Let's Encrypt.  
- **ZFS + LUKS** → Provides a powerful combination for data protection. ZFS handles data integrity and snapshots, while LUKS ensures full disk encryption.  
- **Docker Compose** → Simplifies deployment by defining the entire system in a single file, making it easy to replicate and manage.  

---

## 4. Why These Technologies?  
- **Nextcloud** → Rich pre-built feature set, saves development time.  
- **Keycloak** → Secure and scalable identity and access management with RBAC.  
- **WireGuard** → Modern, lightweight VPN better than legacy options.  
- **Traefik** → Simplifies TLS, load balancing, and routing in containers.  
- **ZFS + LUKS** → Enterprise-grade data safety and encryption at rest.  
- **Docker Compose** → Reproducible setup, easy to manage and demo.  

---

## 5. High-Level Diagram (Refer to the image attached in the repo) 

**Description:**  
- A central **Home Cloud Server** connects to the **Internet** via `VPN (WireGuard)` & `Traefik`.  
- Internal components:  
  - **Nextcloud** (file sharing & user experience)  
  - **Keycloak** (authentication & RBAC)  
  - **ZFS + LUKS** (secure data storage)  
  - **Docker Compose** (deployment)  
- External users:  
  - **Owner** (full access)  
  - **Family** (shared access)  
  - **Guest** (restricted, time-bound access)  

---

## 6. Illustrative Code  

```python
def check_access(user, file, role):
    if role == "owner":
        return True
    if role == "family" and file.shared_with_family:
        return True
    if role == "guest" and file.guest_link_valid:


## 7. Trade-offs & Future Improvements  

### Pros  
- Enhanced security and privacy.  
- Granular role-based access control.  
- Encrypted storage and VPN-secured remote access.  
- Professional, reproducible setup for demos.  

### Cons  
- Single-node setup (no high availability).  
- Requires Docker (and some Linux) knowledge for setup.  
- ZFS memory overhead — not ideal for very low-memory devices unless tuned.  

### Future Improvements  
- Move to Kubernetes for HA and better orchestration.  
- Add distributed/redundant storage (e.g., GlusterFS/Ceph) for reliability.  
- Integrate IDS/IPS, centralized logging, and automated key rotation.  
- Harden Keycloak and Nextcloud for enterprise security posture (WAF, rate limiting, advanced IAM policies).  

---

# 8. Demo Plan  

**Goal:** A clear, 6–8 minute demonstration that shows RBAC, secure access, and system health.  

1. **Project Overview (30s)** → Open `proposal.md` and summarize goals and architecture.  
2. **Show Running Services (30s)** → SSH to demo VM and run `docker compose ps`.  
3. **Keycloak (1 min)** → Show realm and roles (owner, family, guest).  
4. **Nextcloud (2 min)** → Login as Owner → upload a file → create a time-limited guest link.  
5. **Guest Access (30s)** → Open guest link in incognito to show restricted access.  
6. **WireGuard (1 min)** → Connect a client via WireGuard and access Nextcloud over TLS.  
7. **Monitoring & Recovery (30–60s)** → Show Grafana dashboard, list ZFS snapshots, explain a restore.  
8. **Q&A & Next Steps (remaining time)** → Discuss trade-offs and improvements.  
  
---

# 9. Conclusion  

This personal home cloud solution delivers **privacy, flexibility, and security**.  
It ensures full control over data, provides secure remote access, and enforces role-based permissions.  
The system strikes a balance between **simplicity and robustness**, making it a strong solution for personal/family use.  

        return True
    return False
