<h1 align="center"> Mars Protocol Testnet Katılmak için Gentx işlemleri 
</h1>


## 🟢 Bilgi

Mars Protocol'ün Testnetine katılabilmek için Gentx dosyası işlemlerini ele alacağız ayrıca Discord üzerinden Operatör rölü alacağız..


 
 * [Discord](https://discord.gg/marsprotocol)
 * [Telegram Destek Kanalımız](https://t.me/HerculesNode)



## 🟢 KURULUM
<br> 
Buraya, kaşifte görünecek takma adınızın (doğrulayıcı) adını yazmalısınız.  

1- İsim <br>
```shell
NODENAME=<NODE-İSMİNİZİ-YAZIN>
```
<BR>

2- Değişkenleri kaydedin ve sisteme aktarın


```shell
echo "export NODENAME=$NODENAME" >> $HOME/.bash_profile
echo "export WALLET=wallet" >> $HOME/.bash_profile
echo "export CHAIN_ID=mars-1" >> $HOME/.bash_profile
source $HOME/.bash_profile
```

<BR>

3- Güncelleme Paketi

```shell
sudo apt update && sudo apt upgrade -y
```


4- Diğer Yüklemeler

```shell
sudo apt-get install make build-essential gcc git jq chrony -y

```

5- 

```shell
ver="1.18.2"
cd $HOME
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz"
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz"
rm "go$ver.linux-amd64.tar.gz"
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> ~/.bash_profile
source ~/.bash_profile

```

6- 

```shell
cd $HOME
git clone https://github.com/mars-protocol/hub.git
cd hub
git checkout v1.0.0
make install

```

7- 

```shell
marsd config chain-id $CHAIN_ID
marsd config keyring-backend test

```

8- Başlangıç Düğümü

```shell
marsd init $NODENAME --chain-id $CHAIN_ID

```

9- Testnet için yeni cüzdan kurtarın veya oluşturun

```shell
marsd keys add $WALLET

```

10- Cüzdan Kurtarma ( kaybettiyseniz yapın )

```shell
marsd keys add $WALLET --recover

```

11- Genesis Hesabı Ekle

```shell
WALLET_ADDRESS=$(marsd keys show $WALLET -a)
marsd genesis add-account $WALLET_ADDRESS 1000000umars

```

12- GentX Oluştur

```shell
marsd genesis gentx $WALLET 1000000umars \
--chain-id $CHAIN_ID \
--moniker=$NODENAME \
--commission-max-change-rate=0.01 \
--commission-max-rate=1.0 \
--commission-rate=0.05 \
--identity="" \
--website="" \
--details="" \
--min-self-delegation=1

```


11- Yedeklemeniz Gerekenler

* 24 word mnemonic oluşturulan cüzdanınızın
* $HOME/.mars/config/*



## 🟢 Kurulum Dosyaları <br>

* Gentx ile PR gönderin
* ${HOME}/.mars/config/gentx/gentx-XXXXXXXX.json içeriğini kopyalayın.
* https://github.com/mars-protocol/networks   Hesabına Gidin ve Forklayın
* Aşağıdaki Resim adımlarına göre yapabilirsiniz.

<br><br>

*Create New File /  gentx-<VALIDATOR_NAME>.jsonaltında bir dosya oluşturun
![image](https://user-images.githubusercontent.com/101635385/206646379-dca0bb55-6722-4e43-bbda-e7178431de5d.png)

<br><br>

*Ardından Bilgisaysarınıza indirdiğiniz Json dosyasını direk tutup içine atın
![image](https://user-images.githubusercontent.com/101635385/206646669-6a80cd39-cf20-4869-8e2f-1dce331d6a1f.png)

<br><br>
*Daha sonra sol üstten pull request diyip sağ taraftan yeşil butona basalım
![image](https://user-images.githubusercontent.com/101635385/206646874-eb75c9a4-193c-441c-96f1-10269bd902cf.png)

<br><br>
*Write kısmı için bu sefer gentx dosyamızı not defteri ile açıyoruz
![image](https://user-images.githubusercontent.com/101635385/206647031-e1977eb3-072f-4683-b453-97be9b121fe9.png)

<br><br>
*Not defteri ile açtığımız dosyayı kopyalayıp yapıştırıyopruz ve pull oluştu:
![image](https://user-images.githubusercontent.com/101635385/206647097-44b76fa7-b62f-4913-b04f-23aab3741915.png)




