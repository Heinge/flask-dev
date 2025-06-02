Imatge Docker amb aplicació Flask + supervisor + SSH, preparada per a desenvolupament web.

📦 Contingut

- Ubuntu 24.04
- Python 3
- Flask
- Supervisor
- OpenSSH Server

🔨 Build
    docker build -t flask-dev .

▶️ Execució manual
    docker run -d --name flask \
      -p 8000:8000 \
      -p 9001:9001 \
      -p 2123:22 \
      flask-dev


🔑 Accés SSH

ssh ubuntu@localhost -p 2123

Usuari: ubuntu
Contrasenya: ubuntu


🌐 Web
L'aplicació Flask escolta al port 8000

El Supervisor WebUI està al port 9001 (admin/admin)

📂 Directori de treball
El directori on es troba l'aplicació és:
/app

🔧 Detalls tècnics
Supervisor gestiona l’arrencada del servei Flask

Flask corre a 0.0.0.0:8000

SSH actiu al port 22 del contenidor

📌 Requisits

  · Docker instal·lat
  
  · Port 8000, 9001, 2123 lliures al host
