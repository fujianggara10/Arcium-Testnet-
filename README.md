# Arcium-Testnet-


# Testnet Arcium - MPC  

| Sistem yang Dibutuhkan | Minimum Perangkat Keras |  
| --- | --- |  
| CPU | 4 CPU |  
| Memori | 8 GB Memori |  
| Disk Data | 100+ GB Disk Data |  

## Perbarui & Tingkatkan  
```
sudo apt update && sudo apt upgrade -y  
```  

## Instalasi yang Diperlukan  
```
sudo apt install curl git wget htop tmux build-essential jq make lz4 gcc unzip -y  
sudo apt-get install -y libssl-dev  
```  
```
apt install curl iptables build-essential git wget jq make gcc nano tmux htop nvme-cli pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev screen -y  
```  

## Instalasi GO  
```
ver="1.23.0"  
```  
```
cd $HOME  
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz"  
sudo rm -rf /usr/local/go  
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz"  
rm "go$ver.linux-amd64.tar.gz"  
```  
```
echo 'export GOPATH=$HOME/go' >> ~/.bashrc  
echo 'export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin' >> ~/.bashrc  
source ~/.bashrc  
```  
```
go version  
```  

## Instalasi Rust  
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y  
. "$HOME/.cargo/env"  
rustc --version  
```  

## Instalasi Solana  
```
sh -c "$(curl -sSfL https://release.anza.xyz/stable/install)"  
```  
```
export PATH="$HOME/.local/share/solana/install/active_release/bin:$PATH"  
```  
**RESTART TERMINAL ANDA**  
```
solana --version  
```  

## Instalasi Anchor  
```
cargo install --git https://github.com/coral-xyz/anchor avm --force  
```  
```
avm --version  
```  
```
avm install latest  
avm use latest  
```  
```
anchor --version  
```  

## Instalasi YARN  
```
sudo apt install nodejs && sudo apt install npm  
```  
```
npm install --global yarn  
yarn --version  
```  

## Instalasi Docker + Docker Compose  
```
export DOCKER_API_VERSION=1.41  
```  
```
# Tambahkan GPG key resmi Docker:
sudo apt-get update  
sudo apt-get install ca-certificates curl  
sudo install -m 0755 -d /etc/apt/keyrings  
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc  
sudo chmod a+r /etc/apt/keyrings/docker.asc  

# Tambahkan repositori ke sumber Apt:
echo \  
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \  
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \  
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null  
sudo apt-get update  
```  
```
sudo apt-get -y install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin  
```  
```
sudo usermod -aG docker ${USER}  
```  
```
newgrp docker  
```  
```
docker --version  
```  

## Membuat Wallet Solana  
```
solana-keygen new  
```  
**SIMPAN PUBKEY DAN SEED PHRASE**  




### Instalasi Menggunakan Manajer Versi Arcium (arcup)  
`arcup` adalah alat untuk mengelola versi dari perangkat Arcium (termasuk CLI dan node MPC). Informasi lebih lanjut tentang arcup dapat ditemukan di sini. Alat ini memerlukan dependensi yang sama seperti membangun dari sumber.  

1. **Instal arcup**  
Saat ini, kami mendukung 4 target bawaan berikut:  
- `aarch64_linux`  
- `x86_64_linux`  
- `aarch64_macos`  
- `x86_64_macos`  

Kami belum mendukung Windows.  
Untuk menginstalnya, ganti `<YOUR_TARGET>` dengan target yang ingin Anda pasang, lalu jalankan perintah berikut:  
```
TARGET=<YOUR_TARGET> && curl -u testnet_user_20842437:ZTi9igBU6icam0y2 "https://bin.arcium.com/download/arcup_${TARGET}_0.1.30" -o ~/.cargo/bin/arcup && chmod +x ~/.cargo/bin/arcup
```  

2. **Instal versi CLI terbaru menggunakan arcup**  
```
arcup install
```  

3. **Verifikasi instalasi**  
```
arcium --version
```  

### Masalah  
Instalasi mungkin gagal karena berbagai alasan. Bagian ini mencakup daftar masalah paling umum dan solusinya, diambil dari panduan instalasi Anchor.  

**Dependensi yang Hilang**  
Pada sistem Linux, Anda mungkin perlu menginstal dependensi tambahan. Contohnya pada Ubuntu:  
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install -y pkg-config build-essential libudev-dev libssl-dev
```  

**$PATH Tidak Benar**  
Biner Rust, termasuk `arcup` dan `arcium`, diinstal ke direktori `~/.cargo/bin`. Karena direktori ini harus ada dalam variabel lingkungan `PATH`, instalasi Rust mencoba mengaturnya secara otomatis, tetapi mungkin gagal di beberapa platform.  

Untuk memverifikasi bahwa variabel lingkungan `PATH` diatur dengan benar, jalankan:  
```
which arcium
```  
Outputnya seharusnya terlihat seperti ini (dengan nama pengguna Anda):  
```
/home/user/.cargo/bin/arcium
```  
