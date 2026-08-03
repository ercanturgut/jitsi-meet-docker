# Linux Üzerinde Docker ile Jitsi Meet & Free SSL Kurulumu

Bu repository, Oracle Linux 8 işletim sistemi üzerinde Docker ve Docker Compose kullanarak, **ücretsiz Let's Encrypt SSL** sertifikasına sahip prodüksiyon ortamına hazır bir Jitsi Meet video konferans altyapısının kurulumunu içerir.

---

## 🏗 Proje Mimarisi

* **Jitsi Web:** Nginx tabanlı ön yüz altyapısı ve otomatik SSL sertifika yönetimi.
* **Prosody:** XMPP haberleşme sunucusu.
* **Jicofo:** Oturum yönetimi ve konferans orkestratörü.
* **JVB (Jitsi Videobridge):** Media akış (RTP/UDP) kanalı.

---

## 🚀 Adım Adım Kurulum Rehberi

### 1. Kurulum Öncesi Hazırlık
Linux sunucunuzda gerekli paketleri güncelleyin ve Docker'ı yükleyin:

```bash
# Sistem Güncellemesi ve Paketler
dnf -y update
dnf install yum-utils curl git -y

# Docker Repository Ekleme & Kurulum
dnf config-manager --add-repo [https://download.docker.com/linux/centos/docker-ce.repo](https://download.docker.com/linux/centos/docker-ce.repo)
dnf install -y docker-ce --allowerasing
systemctl enable --now docker

# Docker Compose Kurulumu
curl -L "[https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname](https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname) -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose