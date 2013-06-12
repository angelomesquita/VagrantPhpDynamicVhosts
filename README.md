#VagrantPhpDynamicVhosts

Um exemplo de máquina virtual baseada no Debian Linux com Vhosts Dinâmicos com Apache2, PHP 5.4, Mysql e PhpMyadmin.

##Requisitos:

1.	Instale [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
2.	nstale [Vagrant] (http://www.vagrantup.com/)
3.	Baixe uma Box Ubuntu [precise32 VirtualBox] (http://files.vagrantup.com/precise32.box)
4.	[Git] (http://git-scm.com/)
5.	DnsMasq(Linux) e Acrylic DNS(Windows)

##Como usar essa máquina:

1.Clone o repositório ou Baixe o arquivo Zipado.()
2.Verifique o caminho da Box no Arquivo Vagrantfile, adcione o caminho da Box que foi feito o Download.()
3.No Terminal, execute vagrant up
4.Após a instalação digite na url : 127.0.0.1:8080 para verificar se está suficionando, se não conseguir acessar o servidor, 
e estiver aparecendo uma mensagem dizendo que você não tem permissão para acessar o servidor, você precisa da permissão
 de leitura e escrita na pasta do repositório da box, e na pasta vhosts depois feito isso e so criar normalmente as 
 pastas dentro do vhosts, política de segurança do Linux!
5. Agora vamos deixar a url mais amigável para o seu desenvolvimento, para isso vamos instalar um programa que faz esse serviço, 
ele cria um cache de DNS local, mais sobre o assunto nesse [link aqui](http://blog.davidsonpaulo.com/2012/08/como-usar-o-dnsmasq-para-criar-um-cache-de-dns-local.html)

6.DnsMasq(Linux/Mac) basta abrir o terminal e digitar: 
* sudo apt-get install dnsmasq
* Após concluir a instalação, vamos configurar o dnsmasq, acesse o arquivo dnsmasq.conf que está localizado no diretório /etc/ : sudo nano /etc/dnsmasq.conf
* Adcione as seguintes linhas: 
listen-address=127.0.0.1
address=/.dev/127.0.0.1
* feche e salve o arquivo.
* Reinicie o serviço do dnsmasq: sudo service dnsmasq restart
* Após a o reinicio do serviço  de um ping teste.dev e verifique se está cominicando com o endereço , ctrl+c para para o ping.

7.Pronto agora e só você criar a pasta do seu projeto dentro da pasta vhosts/ seguido da pasta public/ e dentro da pasta public/ você coloca os arquivos do seu projeto, por exemplo vhosts/meuprojeto/public/arquivos.php, agora você vai até o seu navegador e digitar a url o nome da pasta do seu projeto, seguido do nome do vhost dinâmico .dev:8080 , exemplo http://meuprojeto.dev:8080

8.[Acrylic DNS] (Windows) (http://sourceforge.net/projects/acrylic/)
* Baixe o Acrylic DNS e instale.
* Altere as configurações do Protocolo ipv4, nas configurações de rede local, coloque o servidor dns preferencial o endereço da sua localhost 127.0.0.1.
* Agora va em /Todos os Programas/Acrylic DNS Proxy/Config/Edit Custon Hosts File e adicione as seguites linhas no final do arquivo: 
127.0.0.1 localhost
127.0.0.1 *.dev
* Feche e salve o arquivo.
* Agora reinicie o serviço do Acrylic em /Todos os Programas/Acrylic DNS Proxy/Config/Restart Acrylic Services.
*Faça o passo 7.

Pronto agora você tem uma box pra começar os seus estudos no mundo php e começar a desenvolver os seus projetos!
Para acessar o PhpMyAdmin e só digitar, meuprojeto.dev:8080/phpmyadmin
O usuário e a senha é root.
