# Running Massa-Node

* Full Documentation : https://docs.massa.net/en/latest/testnet/install.html
* Join discord : https://discord.gg/NXWYS46y
* _pastikan udah join Bot discord juga_
* Ubuntu basic Command : 
---
## Donwload && Requirements
1. VPS
2. Putty *[Link](https://www.putty.org/)*
3. File Zilla *[Link](https://filezilla-project.org/download.php)*
---
## Getting Started

### Step 1 [ Update && Install ]

### Update Ubuntu
```bash
sudo apt-get update && upgrade
```
### Install
**1. Ubuntu libs**
```bash
sudo apt install pkg-config curl git build-essential libssl-dev libclang-dev
```
**2. install rustup**
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
**3. configure path**
```bash
source $HOME/.cargo/env
```
**4. check rust version**
```bash
rustc --version
```
**5. install nigthly**
```bash
rustup toolchain install nightly
```
**6. set it as default**
```bash
rustup default nightly
```
**7. check rust version**
```bash
rustc --version
```




### Step 2 [ Open Port ]

```bash
ufw allow ssh
ufw allow 31244
ufw allow 31245
ufw enable
```
check list port
```bash
sudo ufw status verbose
```



### Step 3 [ Download Massa && Intsall Screen session ]
**Download**
```bash
git clone --branch testnet https://github.com/massalabs/massa.git
```
**update**
```bash
cd massa
```
```bash
git pull
```
```bash
cd
```
**Install Screen session**
```bash
sudo apt install screen
```



### Step 4 [ Sett up wallet ]
Masuk ke direktori
```bash
cd massa/massa-client/
```
&& kemudian jalankan perintah
```bash
cargo run
```
> _tunggu sampe proses selesai (note: untuk pertama kali isi password & di ingat ya ges ya )_

Buat wallet baru
```bash
wallet_generate_secret_key
```
check wallet info
```bash
wallet_info
```
> _save wallet ( Address, pubkey, secret key )_
exit && kemabli ke direktori awal
#### Copy address && Ambil Faucet di discord 
Exit
```bash
exit
```
```bash
cd
```



### Step 5 [ Create session && Routebility && Run Node ]
Buat sesi node
```bash
screen -S nodeRunning
```
Set Up Routebility
```bash
sudo nano massa/massa-node/config/config.toml
```
lalu paste
```bash
[network]
routable_ip = "Isi dengan alamat IP"
```
> _setelah itu Ctrl+X ketik Y dan enter_

Run Node
```bash
cd massa/massa-node
```
```bash
RUST_BACKTRACE=full cargo run --release -- -p <isi password massa-client/wallet> |& tee logs.txt
```
> * PASTIKAN UDAH BENER LOGS NYA, KALO MASIH BELUM BENER CLOSE ( CTRL + C ) DAN LANJUT KE STEP TROBLESHOTING BOOTSTRAP 
> 
> * KALO UDAH BENER close session dengan cara Ctrl+A+D dan lanjut ke step 6

### Step 6 [Buys Rolls]
```bash
cd
```
```bash
cd massa/massa-client
```
```bash
cargo run
```
Buy Rolls
```bash
buy_rolls <isi address massa> <roll count> <fee>

contoh:
buy_rolls VkUQ5MA4niNBhAEP7uVf89tvPfUHcbgy6BrdLM9SAuFSyy9DE 1 0
```
Register secret key untuk Node jalankan stake
```bash
node_add_staking_secret_keys <isi dengan secret key massa>

contoh:
node_add_staking_secret_keys paste secretkey di sini
```
> Sekarang nunggu rolls nya udah aktif atau belum, biasanya 1-2 jam baru bisa aktif

cek status
```bash
wallet_info
```
## DONE

---

## TROBLESHOTING BOOTSTRAP, SOON..!!!
























