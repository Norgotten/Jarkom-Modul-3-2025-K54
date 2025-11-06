# Jarkom-Modul-3-2025-K54

| No | Nama                              | NRP         |
|----|-----------------------------------|-------------|
| 1  | Salsa Bil Ulla         | 5027241052 |
| 2  | Hafiz Ramadhan   | 5027241096  |

## Soal 1
<img width="1380" height="806" alt="Screenshot 2025-10-28 183442" src="https://github.com/user-attachments/assets/c56bae7c-eaf6-4fb3-8c26-dfa09a227b2f" />

Berdasarkan desain topologi yang telah dibuat di GNS3, berikut implementasi konfigurasi jaringan:

- **Durin**
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
 	address 192.238.1.1
 	netmask 255.255.255.0

auto eth2
iface eth2 inet static
 	address 192.238.2.1
 	netmask 255.255.255.0

auto eth3
iface eth3 inet static
 	address 192.238.3.1
 	netmask 255.255.255.0

auto eth4
iface eth4 inet static
 	address 192.238.4.1
 	netmask 255.255.255.0

auto eth5
iface eth5 inet static
 	address 192.238.5.1
 	netmask 255.255.255.0

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.238.0.0/16
```

- **Elendil**
```
auto eth0
iface eth0 inet static
 	address 192.238.1.2
 	netmask 255.255.255.0
 	gateway 192.238.1.1
```

- **Isildur**
```
auto eth0
iface eth0 inet static
 	address 192.238.1.3
 	netmask 255.255.255.0
 	gateway 192.238.1.1
```

- **Anarion**
```
auto eth0
iface eth0 inet static
 	address 192.238.1.4
 	netmask 255.255.255.0
 	gateway 192.238.1.1
```

- **Miriel**
```
auto eth0
iface eth0 inet static
 	address 192.238.1.5
 	netmask 255.255.255.0
 	gateway 192.238.1.1
```

- **Amandil**
```
auto eth0
iface eth0 inet dhcp

up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- **Elros**
```
auto eth0
iface eth0 inet static
 	address 192.238.1.7
 	netmask 255.255.255.0
 	gateway 192.238.1.1
```

- **Gilgalad**
```
auto eth0
iface eth0 inet dhcp

up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- **Celebrimbor**
```
auto eth0
iface eth0 inet static
 	address 192.238.2.3
 	netmask 255.255.255.0
 	gateway 192.238.2.1
```

- **Pharazon**
```
auto eth0
iface eth0 inet static
 	address 192.238.2.4
 	netmask 255.255.255.0
 	gateway 192.238.2.1
```

- **Galadriel**
```
auto eth0
iface eth0 inet static
 	address 192.238.2.5
 	netmask 255.255.255.0
 	gateway 192.238.2.1
```

- **Celeborn**
```
auto eth0
iface eth0 inet static
 	address 192.238.2.6
 	netmask 255.255.255.0
 	gateway 192.238.2.1
```

- **Oropher**
```
auto eth0
iface eth0 inet static
 	address 192.238.2.7
 	netmask 255.255.255.0
 	gateway 192.238.2.1
```

- **Khamul**
```
auto eth0
iface eth0 inet static
 	address 192.238.3.2
 	netmask 255.255.255.0
 	gateway 192.238.3.1
```

- **Erendis**
```
auto eth0
iface eth0 inet static
 	address 192.238.3.3
 	netmask 255.255.255.0
 	gateway 192.238.3.1
```

- **Amdir**
```
auto eth0
iface eth0 inet static
 	address 192.238.3.4
 	netmask 255.255.255.0
 	gateway 192.238.3.1
```

- **Aldarion**
```
auto eth0
iface eth0 inet static
 	address 192.238.4.2
 	netmask 255.255.255.0
 	gateway 192.238.4.1
```

- **Palantir**
```
auto eth0
iface eth0 inet static
 	address 192.238.4.3
 	netmask 255.255.255.0
 	gateway 192.238.4.1
```

- **Narvi**
```
auto eth0
iface eth0 inet static
 	address 192.238.4.4
 	netmask 255.255.255.0
 	gateway 192.238.4.1
```

- **Minastir**
```
auto eth0
iface eth0 inet static
 	address 192.238.5.2
 	netmask 255.255.255.0
 	gateway 192.238.5.1
```
Berikut adalah contoh pengetesan dengan ping ke `google.com`.
<img width="1324" height="279" alt="image" src="https://github.com/user-attachments/assets/1976faa9-d059-4466-8871-5850a62c7e92" />

## Soal 2
- **Aldarion**

Lakukan instalasi server DHCP terlebih dahulu.
```
apt-get update && apt-get install isc-dhcp-server -y
```
Buka `/etc/default/isc-dhcp-server` lalu tambahkan `eth0` pada `INTERFACESv4`.
```
INTERFACESv4="eth0"
```
Buat konfigurasi DHCP.
```
cat > /etc/dhcp/dhcpd.conf << EOF
authoritative;
# Subnet 1
subnet 192.238.1.0 netmask 255.255.255.0 {
    range 192.238.1.6 192.238.1.34;
    range 192.238.1.68 192.238.1.94;
    option routers 192.238.1.1;
    option broadcast-address 192.238.1.255;
    option domain-name-servers 192.168.122.1;
    default-lease-time 600;
    max-lease-time 7200;
}
# Subnet 2
subnet 192.238.2.0 netmask 255.255.255.0 {
    range 192.238.2.35 192.238.2.67;
    range 192.238.2.96 192.238.2.121;
    option routers 192.238.2.1;
    option broadcast-address 192.238.2.255;
    option domain-name-servers 192.168.122.1;
    default-lease-time 600;
    max-lease-time 7200;
}
# Subnet 3
subnet 192.238.3.0 netmask 255.255.255.0 {
    option routers 192.238.3.1;
    option broadcast-address 192.238.3.255;
    option domain-name-servers 192.168.122.1;
    default-lease-time 600;
    max-lease-time 7200;
}
# Reservation: Khamul
host khamul {
    hardware ethernet 02:42:61:15:e4:00;
    fixed-address 192.238.3.95;
}
# Subnet 4
subnet 192.238.4.0 netmask 255.255.255.0 {
    option routers 192.238.4.1;
    option broadcast-address 192.238.4.255;
    option domain-name-servers 192.168.122.1;
}
EOF
```
Mulai server DHCP.
```
service isc-dhcp-server start
```

- **Durin**

Lakukan instalasi relay DHCP.
```
apt-get update && apt-get install isc-dhcp-relay -y
```
Ganti default dengan ini:
```
cat > /etc/default/isc-dhcp-relay << EOF
SERVERS="192.238.4.2"
INTERFACES="eth1 eth2 eth3 eth4 eth5"
OPTIONS=""
EOF
```
Nyalakan `IP Forwarding`.
```
net.ipv4.ip_forward=1
```
Lalu mulai `relay dhcp`.
```
service isc-dhcp-relay start
```
<img width="1323" height="140" alt="image" src="https://github.com/user-attachments/assets/9fcf9613-9e6f-485b-864c-7f1bcd49ee17" />

## Soal 3
- **Minastir**

Lakukan instalasi `bind9`.
```
apt-get update && apt-get install bind9 -y
```
Isi konfigurasi opsi seperti berikut:
```
cat > /etc/bind/named.conf.options << 'EOF'
options {
    directory "/var/cache/bind";
    forwarders {
        192.168.122.1;
        8.8.8.8;
        8.8.4.4;
    };
    forward only;
    dnssec-validation no;
    listen-on { any; };
    allow-query { any; };
    auth-nxdomain no;
    listen-on-v6 { any; };
    recursion yes;
};
EOF
```
Mulai service `bind9`.
```
service bind9 start
```

- **Non-Route Static**

Tambahkan konfigurasi resolver di semua node static selain router.
```
echo "nameserver 192.238.5.2" > /etc/resolv.conf
```

- **Client**

Lakukan pengetesan seperti berikut di Client.
```
nslookup google.com
nslookup k54.com
nslookup www.k54.com
```
<img width="1347" height="579" alt="image" src="https://github.com/user-attachments/assets/4a44ed70-ecf1-46e2-acdd-9a6b18918a53" />
<img width="1346" height="437" alt="image" src="https://github.com/user-attachments/assets/5243736e-bfe7-4cc8-9605-d6d82184e824" />

## Soal 4
- **Erendis**

Lakukan instalasi `bind9` dan package utility-nya.
```
apt update && apt-get install bind9 bind9utils -y
```
Isi konfigurasi opsi seperti berikut:
```
cat > /etc/bind/named.conf.options << EOF
options {
    directory "/var/cache/bind";
    forwarders {
        192.238.5.2;
    };
    dnssec-validation no;
    listen-on { any; };
    allow-query { any; };
    auth-nxdomain no;
    listen-on-v6 { any; };
    recursion yes;
};
EOF
```
Lalu isi konfigurasi lokal seperti berikut:
```
cat > /etc/bind/named.conf.local << EOF
zone "k54.com" {
    type master;
    notify yes;
    also-notify { 192.238.3.4; };
    allow-transfer { 192.238.3.4; };
    file "/etc/bind/k54/k54.com";
};

zone "3.238.192.in-addr.arpa" {
    type master;
    notify yes;
    also-notify { 192.238.3.4; };
    allow-transfer { 192.238.3.4; };
    file "/etc/bind/k54/192.238.3.rev";
};
EOF
```
Buat direktori yang diperlukan.
```
mkdir /etc/bind/k54
```
Lalu edit zona konfigurasi DNS seperti berikut:
```
cat > /etc/bind/k54/k54.com << 'EOF'
$TTL 604800
@       IN SOA  ns1.k54.com. root.k54.com. (
                        2025103001
                        604800
                        86400
                        2419200
                        604800 )

        IN NS   ns1.k54.com.
        IN NS   ns2.k54.com.

@       IN A    192.238.3.3
ns1     IN A    192.238.3.3
ns2     IN A    192.238.3.4

palantir        IN A    192.238.4.3
elros           IN A    192.238.1.7
pharazon        IN A    192.238.2.4
elendil         IN A    192.238.1.2
isildur         IN A    192.238.1.3
anarion         IN A    192.238.1.4
galadriel       IN A    192.238.2.5
celeborn        IN A    192.238.2.6
oropher         IN A    192.238.2.7

www     IN CNAME        k54.com.
EOF
```
Lalu buat reverse zone nya seperti berikut:
```
cat > /etc/bind/k54/192.238.3.rev << 'EOF'
$TTL 604800
@       IN SOA  ns1.k54.com. root.k54.com. (
                        2025103001
                        604800
                        86400
                        2419200
                        604800 )

; Name Servers
        IN NS   ns1.k54.com.
        IN NS   ns2.k54.com.

; PTR Records
3       IN PTR  ns1.k54.com.
4       IN PTR  ns2.k54.com.
EOF
```
Mulai service `bind9`.
```
service bind9 start
```
Lakukan pengetesan seperti berikut:
```
nslookup k54.com 127.0.0.1
nslookup palantir.k54.com 127.0.0.1
```

- **Amdir**

Lakukan instalasi `bind9` dan package utility-nya.
```
apt update && apt-get install bind9 bind9utils -y
```
Isi konfigurasi lokal seperti berikut:
```
cat > /etc/bind/named.conf.local << EOF
zone "k54.com" {
    type slave;
    masters { 192.238.3.3; };
    file "/var/cache/bind/k54.com";
};

zone "3.238.192.in-addr.arpa" {
    type slave;
    masters { 192.238.3.3; };
    file "/var/cache/bind/192.238.3.rev";
};
EOF
```
Mulai server `bind9`.
```
service bind9 start
```
Lakukan pengetesan seperti berikut:
```
nslookup k54.com 127.0.0.1
nslookup ns1.k54.com 127.0.0.1
```

- **Aldarion**

Buka `/etc/dhcp/dhcpd.conf` dan ganti `domain-name-servers` di semua subnet menjadi `192.238.5.2`. Lalu mulai ulang server.
```
service isc-dhcp-server restart
```

- **Minastir**

Buat konfigurasi opsi seperti berikut:
```
cat > /etc/bind/named.conf.options << 'EOF'
options {
    directory "/var/cache/bind";
    forwarders {
        192.238.3.3;
        192.238.3.4;
        8.8.8.8;
    };
    forward only;
    dnssec-validation no;
    listen-on { any; };
    allow-query { any; };
    auth-nxdomain no;
    listen-on-v6 { any; };
    recursion yes;
};
EOF
```
Mulai ulang server.
```
service bind9 restart
```

- **DHCP Client (Amandil & Gilgalad)**

Lakukan instalasi client DHCP.
```
apt-get update && apt-get install isc-dhcp-client -y
```
Minta IP baru dari server DHCP.
```
dhclient -r
dhclient eth0
```
Lakukan pengetesan seperti berikut:
```
nslookup k54.com
nslookup palantir.k54.com
nslookup ns1.k54.com
```
<img width="1354" height="583" alt="image" src="https://github.com/user-attachments/assets/e2e4fe28-7b74-433a-b1f3-46f1237d6347" />

- **Amdir**

Cek zona transfer dari master ke slave DNS seperti berikut:
```
ls -la /var/cache/bind/
```
<img width="1357" height="191" alt="image" src="https://github.com/user-attachments/assets/e693300d-b2aa-4716-97ad-bce8f8076545" />

Lalu lakukan pengecekan seperti berikut:
```
nslookup k54.com 127.0.0.1
nslookup ns1.k54.com 127.0.0.1
nslookup palantir.k54.com 127.0.0.1
```
<img width="1356" height="467" alt="image" src="https://github.com/user-attachments/assets/13f6ae98-3674-4a4b-841d-7299c0831c50" />

## Soal 5
- **Erendis**

Edit untuk menammbahkan pesan rahasia seperti berikut:
```
@               IN TXT  "Cincin Sauron menuju Elros"
@               IN TXT  "Aliansi Terakhir menuju Pharazon"
elros           IN TXT  "Cincin Sauron"
pharazon        IN TXT  "Aliansi Terakhir"
```
Mulai ulang service `bind9`.
```
service bind9 restart
```
Lakukan pengetesan seperti berikut:
```
nslookup www.k54.com 127.0.0.1
nslookup 192.238.3.3 127.0.0.1
nslookup 192.238.3.4 127.0.0.1
nslookup -type=TXT k54.com 127.0.0.1
nslookup -type=TXT elros.k54.com 127.0.0.1
nslookup -type=TXT pharazon.k54.com 127.0.0.1
```

- **Amdir**

Lakukan pengetesan yang sama pada slave.
```
nslookup www.k54.com 127.0.0.1
nslookup 192.238.3.3 127.0.0.1
nslookup 192.238.3.4 127.0.0.1
nslookup -type=TXT k54.com 127.0.0.1
nslookup -type=TXT elros.k54.com 127.0.0.1
nslookup -type=TXT pharazon.k54.com 127.0.0.1
```

## Soal 6
- **Aldarion**

Ganti `lease-time` sesuai soal tiap subnet.
```
# Subnet 1
default-lease-time 1800;    # 30 MENIT
max-lease-time 3600;        # 1 JAM

# Subnet 2
default-lease-time 600;     # 10 MENIT
max-lease-time 3600;        # 1 JAM

# Subnet 3
default-lease-time 1800;    # 30 MENIT  
max-lease-time 3600;        # 1 JAM
```
Mulai ulang `server dhcp`.
```
service isc-dhcp-server restart
```

- **Client DHCP (Amandil & Gilgalad)**

Tes dengan minta IP pada server DHCP.
```
dhclient -r
dhclient -v eth0
```

## Soal 7

- **Worker Laravel (Elendil, Isildur, Anarion)**

Lakukan instalasi yang diperlukan.
```
apt-get update && apt-get install -y nginx php8.4 php8.4-fpm php8.4-mysql php8.4-mbstring php8.4-xml php8.4-curl php8.4-zip git unzip htop
```
Lalu setup composer untuk manage PHP packages di projek Laravel.
```
curl -sS https://getcomposer.org/installer -o composer-setup.php
php composer-setup.php --install-dir=/usr/local/bin --filename=composer
chmod +x /usr/local/bin/composer
```
Lalu buka `/etc/nginx/sites-available/laravel` untuk mengedit konfigurasi nginx aplikasi Laravel, ganti `<worker>` sesuai dengan nama worker.
```
server {
    listen 80;
    server_name elendil.k54.com;
    root /var/www/laravel/public;
    index index.php index.html;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.4-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }

    location ~ /\.ht {
        deny all;
    }
}
```
Lanjut nyalakan situs `nginx` dan hapus tampilan default-nya.
```
ln -s /etc/nginx/sites-available/laravel /etc/nginx/sites-enabled/
rm /etc/nginx/sites-enabled/default
```
Mulai ulang `nginx` dan `php`.
```
service nginx restart
service php8.4-fpm restart
```
Lanjut download dan setup projek Laravel.
```
mkdir -p /var/www
cd /var/www
git clone https://github.com/elshiraphine/laravel-simple-rest-api.git laravel
cd laravel
composer install --no-dev --optimize-autoloader
```
Lanjut setup environment dan security key untuk Laravel, serta set permissions.
```
cp .env.example .env
php artisan key:generate
chown -R www-data:www-data /var/www/laravel
chmod -R 755 /var/www/laravel/storage
chmod -R 755 /var/www/laravel/bootstrap/cache
```
Lalu edit konfigurasi environment Laravel dengan `nano .env`. Edit database dan application seperti berikut:
```
DB_CONNECTION=mysql
DB_HOST=192.238.4.3
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=k54
DB_PASSWORD=mclaren

APP_URL=http://<worker>.k54.com
APP_ENV=production
APP_DEBUG=false
```
Mulai ulang `nginx` dan `php`.
```
service nginx restart
service php8.4-fpm restart
```
Lakukan pengetesan seperti berikut:
```
curl -I http://localhost
curl http://localhost
```

- **Client Statis (Miriel & Celebrimbor)**

Lakukan pengetesan pada klien statis seperti berikut:
```
apt-get update && apt-get install lynx -y
lynx http://elendil.k54.com
curl http://elendil.k54.com
curl -I http://elendil.k54.com
ping elendil.k54.com -c 5
```

## Soal 8

- **Palantir**

Install dan jalankan `mariadb`.
```
apt-get update && apt-get install mariadb-server -y
service mariadb start
service mariadb enable
```
Lalu setup database dan user di `mariadb`.
```
mysql -u root -e "CREATE DATABASE laravel;"
mysql -u root -e "CREATE USER 'k54'@'%' IDENTIFIED BY 'mclaren';"
mysql -u root -e "GRANT ALL PRIVILEGES ON laravel.* TO 'k54'@'%';"
mysql -u root -e "FLUSH PRIVILEGES;"
```
Lalu buka firewall database agar bisa diakses dari server lain dengan `nano /etc/mysql/mariadb.conf.d/50-server.cnf`.
```
# bind-address = 127.0.0.1       > di comment aja
```
Mulai ulang `mariadb.`
```
service mariadb restart
```
Lakukan pengetesan seperti berikut:
```
mysql -u root -e "SELECT user, host FROM mysql.user WHERE user = 'k54';"
mysql -u root -e "SHOW GRANTS FOR 'k54'@'%';"
mysql -u root -e "SHOW DATABASES;"
```

- **Worker Laravel (Elendil, Isildur, Anarion)**

Ganti konfigurasi keamanan tiap worker seperti berikut:
Elendil: 
```
listen 8001;
server_name elendil.k54.com;
if ($host !~* ^(elendil\.k54\.com)$ ) { return 444; }
```
Isildur:
```
listen 8002;
server_name isildur.k54.com;
if ($host !~* ^(isildur\.k54\.com)$ ) { return 444; }
```
Anarion:
```
listen 8003; 
server_name anarion.k54.com;
if ($host !~* ^(anarion\.k54\.com)$ ) { return 444; }
```
Mulai ulang `nginx`.
```
service nginx restart
```

- **Elendil**

Lakukan instalasi pada `mariadb` dan jalankan migrasi.
```
apt-get install -y mariadb-client
mysql -h 192.238.4.3 -u k54 -p laravel
# exit aja

php artisan migrate

php artisan tinker
>>> DB::connection()->getPdo();
>>> exit;
```

## Soal 9

- **Client Statis (Miriel & Celebrimbor)**

Lakukan instalasi `lynx` terlebih dahulu.
```
apt-get update && apt-get install lynx -y
```
Lakukan pengetesan seperti berikut:
```
lynx http://elendil.k54.com:8001
lynx http://isildur.k54.com:8002  
lynx http://anarion.k54.com:8003

curl http://elendil.k54.com:8001/api/airing
curl http://isildur.k54.com:8002/api/airing
curl http://anarion.k54.com:8003/api/airing
```

## Soal 10

- **Elros**

Lakukan instalasi `nginx` terlebih dahulu.
```
apt-get update && apt-get install -y nginx
```
Lalu buka `/etc/nginx/sites-available/reverse-proxy` untuk membuat konfigurasi reverse proxy dengan `nginx`.
```
upstream kesatria_numenor {
    server elendil.k54.com:8001;
    server isildur.k54.com:8002;
    server anarion.k54.com:8003;
}

server {
    listen 80;
    server_name elros.k54.com;

    location / {
        proxy_pass http://kesatria_numenor;
        proxy_set_header Host elros.k54.com;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```
Lanjut aktifkan `nginx` lalu hapus defaultnya, setelah itu dapat langsung menjalankan `nginx`.
```
ln -s /etc/nginx/sites-available/reverse-proxy /etc/nginx/sites-enabled/
rm -f /etc/nginx/sites-enabled/default
service nginx restart
```

- **Worker Laravel (Elendil, Isildur, Anarion)**

Ketik tiap command berikut sesuai terminal masing-masing.
```
if ($host !~* ^(elendil\.k54\.com|elros\.k54\.com)$ ) { return 444; }
if ($host !~* ^(isildur\.k54\.com|elros\.k54\.com)$ ) { return 444; }
if ($host !~* ^(anarion\.k54\.com|elros\.k54\.com)$ ) { return 444; }
```
Lanjut jalankan migrasi di semua terminal worker laravel.
```
php artisan migrate
```
Buka akses log.
```
tail -f /var/log/nginx/access.log
```

- **Client Statis (Miriel & Celebrimbor)**

Lakukan pengetesan dengan perintah seperti berikut:
```
lynx http://elros.k54.com
curl http://elros.k54.com/api/airing
```

## Soal 11

- **Worker Laravel (Elendil, Isildur, Anarion)**

buka `/etc/php/8.4/fpm/pool.d/www.conf` lalu edit seperti berikut untuk meningkatkan kapasitas `PHP-FPM` sesuai permintaan soal.
```
pm.max_children = 50           # dari default 5
pm.start_servers = 10          # dari default 2  
pm.min_spare_servers = 5       # dari default 1
pm.max_spare_servers = 20      # dari default 3
```
Lanjut mulai ulang `php`.
```
service php8.4-fpm restart
```
Lanjut buat cache.
```
php artisan config:cache
php artisan route:cache
```
Lanjut bikin daftar lokasi file class biar lebih cepat di-load.
```
composer dump-autoload --optimize
```

- **Palantir**

Buka `/etc/mysql/mariadb.conf.d/50-server.cnf` lalu edit seperti berikut:
```
[mysqld]
max_connections = 500          # dari default 151
```
Lalu mulai ulang `mariadb`.
```
service mariadb restart
```

- **Elros**

Lalu buka log dengan perintah berikut:
```
tail -f /var/log/nginx/access.log
```

- **Client (Miriel & Celembrimbor)**

Lakukan pengetesan seperti berikut:
```
apt-get update && apt-get install -y apache2-utils
ab -n 100 -c 10 http://elros.k54.com/api/airing/
ab -n 2000 -c 100 http://elros.k54.com/api/airing/
```

## Soal 12

- **Worker PHP (Galadriel, Celeborn, Oropher)**

Lakukan instalasi `nginx` dan `php`, lalu mulai service.
```
apt-get update && apt-get install -y nginx php8.4-fpm
service nginx start
service php8.4-fpm start
```
Buat direktori `mkdir -p /var/www/html`, lalu buat `index.php` seperti berikut:
```
cat > /var/www/html/index.php << 'EOF'
<?php
$hostname = gethostname();
echo "<h1>Sirkuit Pribadi  $hostname</h1>";
echo "<p>P balap, arena pribadi $hostname</p>";
echo "<p>Server: " . $_SERVER['SERVER_NAME'] . "</p>";
?>
EOF
```
Lanjut buat konfigurasi virtual host seperti berikut dengan mengganti <worker> sesuai terminal worker yang dijalankan:
```
cat >  /etc/nginx/sites-available/sirkuit << 'EOF'
server {
    listen 80;
    server_name <worker>.k54.com;
    
    if ($host !~* ^(<worker>\.k54\.com)$ ) {
        return 444;
    }
    
    root /var/www/html;
    index index.php index.html;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.4-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }
}
EOF
```
Lanjut aktifkan situs `nginx` dan hapus default, lalu jalankan `nginx` dan `php`.
```
ln -s /etc/nginx/sites-available/sirkuit /etc/nginx/sites-enabled/
rm -f /etc/nginx/sites-enabled/default
service nginx restart && service php8.4-fpm restart
```
Lalu beri hak akses seperti berikut:
```
chown -R www-data:www-data /var/www/html
chmod -R 755 /var/www/html
```
Lakukan pengetesan seperti berikut:
```
curl http://celeborn.k54.com
nslookup celeborn.k54.com
```

- **Client Statis (Miriel & Celebrimbor)**

Lakukan pengetesan seperti berikut:
```
lynx http://galadriel.k54.com
lynx http://celeborn.k54.com  
lynx http://oropher.k54.com

curl http://galadriel.k54.com
curl http://celeborn.k54.com
curl http://oropher.k54.com
```

## Soal 13

- **Worker PHP (Galadriel, Celeborn, Oropher)**

Buka `/etc/nginx/sites-available/sirkuit` dan ganti port sesuai ketentuan soal seperti berikut:
```
# Galadriel 8004
server {
    listen 8004;

# Celeborn 8005
server {
    listen 8005;

# Oropher 8006
server {
    listen 8006;
```

- **Client Statis (Miriel & Celebrimbor)**

Lakukan pengetesan seperti berikut:
```
curl http://galadriel.k54.com:8004
curl http://celeborn.k54.com:8005
curl http://oropher.k54.com:8006

curl http://galadriel.k54.com:8004/index.php
```

## Soal 14

- **Worker PHP (Galadriel, Celeborn, Oropher)**

Lakukan instalasi `apache`.
```
apt-get update && apt-get install -y apache2-utils
```
Buat direktori untuk menyimpan password dengan `mkdir -p /etc/nginx/secure`, lalu buat akun dan password dengan berikut:
```
htpasswd -bc /etc/nginx/secure/.htpasswd noldor silvan
```
Buka `/etc/nginx/sites-available/sirkuit` lalu edit seperti berikut:
```
server {
...
    root /var/www/html;
    index index.php index.html;

    auth_basic "Restricted Access";
    auth_basic_user_file /etc/nginx/secure/.htpasswd;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
...
        include fastcgi_params;
        
        auth_basic "Restricted Access";
        auth_basic_user_file /etc/nginx/secure/.htpasswd;
    }
}
```
Mulai ulang service `nginx`.
```
service nginx restart
```
Buat hak akses yang aman untuk file password.
```
chown www-data:www-data /etc/nginx/secure/.htpasswd
chmod 600 /etc/nginx/secure/.htpasswd
```

- **Client Statis (Miriel & Celebrimbor)**

Lakukan pengetesan seperti berikut:
```
curl -I http://galadriel.k54.com:8004/
curl -u noldor:silvan http://galadriel.k54.com:8004/
curl -H "Authorization: Basic $(echo -n 'noldor:silvan' | base64)" http://galadriel.k54.com:8004/
lynx http://galadriel.k54.com:8004/
```

## Soal 15

- **Worker PHP (Galadriel, Celeborn, Oropher)**

Buka `/etc/nginx/sites-available/sirkuit` lalu edit seperti berikut:
```
server {
...
    location / {
        try_files $uri $uri/ =404;
        
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    location ~ \.php$ {
...
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;

        fastcgi_param X-Real-IP $remote_addr;
        fastcgi_param X-Forwarded-For $proxy_add_x_forwarded_for;
        fastcgi_param X-Forwarded-Proto $scheme;
...
    }
}
```
Mulai ulang service `nginx`.
```
service nginx restart
```
Buka `/var/www/html/index.php` untuk mengedit halaman php seperti berikut:
```
<?php
$hostname = gethostname();
$visitor_ip = $_SERVER['HTTP_X_REAL_IP'] ??
              $_SERVER['HTTP_X_FORWARDED_FOR'] ??
              $_SERVER['REMOTE_ADDR'] ??
              'Unknown';

echo "<h1>Sirkuit Pribadi $hostname</h1>";
echo "<p>P balap, arena pribadi $hostname</p>";
echo "<p>Server: " . $_SERVER['SERVER_NAME'] . "</p>";
echo "<p>IP Pengunjung: <strong>$visitor_ip</strong></p>";
echo "<p>Waktu Akses: " . date('Y-m-d H:i:s') . "</p>";
?>
```
Lanjut edit hak akses seperti berikut:
```
chown www-data:www-data /var/www/html/index.php
chmod 644 /var/www/html/index.php
```

- **Client Statis (Miriel & Celebrimbor)**

Lakukan pengetesan seperti berikut:
```
curl -u noldor:silvan http://galadriel.k54.com:8004/
curl -u noldor:silvan http://celeborn.k54.com:8005/
curl -u noldor:silvan http://oropher.k54.com:8006/
```
