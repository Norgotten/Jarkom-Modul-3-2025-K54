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
Lakukan instalasi `isc-dhcp-server` terlebih dahulu.
```
apt-get update && apt-get install isc-dhcp-server
```
