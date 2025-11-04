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

## Soal 2
- **Aldarion**

Lakukan instalasi `server dhcp` terlebih dahulu.
```
apt-get update && apt-get install isc-dhcp-server -y
```
Buka `/etc/default/isc-dhcp-server` lalu tambahkan `eth0` pada `INTERFACESv4`.
```
INTERFACESv4="eth0"
```
Buat konfigurasi `dhcp`.
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
Mulai `server dhcp`.
```
service isc-dhcp-server start
```

- **Durin**

Lakukan instalasi `relay dhcp`.
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
                        2025103001      ; Serial
                        604800          ; Refresh
                        86400           ; Retry
                        2419200         ; Expire
                        604800 )        ; Negative Cache TTL

; Name Servers
        IN NS   ns1.k54.com.
        IN NS   ns2.k54.com.

; A Records
@       IN A    192.238.3.3
ns1     IN A    192.238.3.3
ns2     IN A    192.238.3.4

; Node Records
palantir        IN A    192.238.4.3
elros           IN A    192.238.1.7
pharazon        IN A    192.238.2.4
elendil         IN A    192.238.1.2
isildur         IN A    192.238.1.3
anarion         IN A    192.238.1.4
galadriel       IN A    192.238.2.5
celeborn        IN A    192.238.2.6
oropher         IN A    192.238.2.7

; CNAME
www     IN CNAME        k54.com.
EOF

nano /etc/bind/k54/192.238.3.rev

cat > /etc/bind/k54/192.238.3.rev << 'EOF'
$TTL 604800
@       IN SOA  ns1.k54.com. root.k54.com. (
                        2025103001      ; Serial
                        604800          ; Refresh
                        86400           ; Retry
                        2419200         ; Expire
                        604800 )        ; Negative Cache TTL

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
