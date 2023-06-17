https://media.tenor.com/apaLlyjoPuYAAAAi/dinkdonk-emote.gif
# usando o iptables:

Hllo! basicamente o iptables é uma ferramenta/firewall em nível de pacotes que já vêm por padrão nos sistemas operacionais, mesmo que seja versão minimal

# como funciona:

simples... através da comparação de regras para saber se um pacote tem ou não permissão para passar

# usagem:

ele e usado para cotrolar as regras de filtragem de pacotes em um sistemas baseados em Linux. configurando o iptables colocando regras especificias como bloquear a entrada de pacotes o iptables funciona controlando o tráfego de rede de entrada e saída ou seja um firewall.

# usagem2:

iptables usa uma série de chains (cadeias) predefinidas, como INPUT, OUTPUT,FOWARD, para organizar e processar os pacotes de acordo com as regras definidas pelo usuário.

# Regras

// Limpar todas as regras existentes:
iptables -F

// permitir tráfego de loopback (o localhost)
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

// permitir conexões SSH de entrada:
iptables -A INPUT -p tcp --dport 22 -j ACCEPT

// Permitir conexões HTTP e HTTPS de entrada:
iptables -A INPUT -p tcp --dport 90 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j ACCEPT

// Permitir conexões estabelecidas e relacionadas de entrada
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

// Bloquear todo o tráfego de entrada não solicitado
iptables -A INPUT -j DROP

// Permitir todo o tráfego de saída
iptables -A OUTPUT -j ACCEPT

// permitir conxões estabelecidas de saída
iptables -A INPUT -m conntrack --ctstate ESTABLISHED -j ACCEPT

# Salvar regras para que sejam carregadas na inicialização:

iptables-save > /etc/iptables/rules.v4
