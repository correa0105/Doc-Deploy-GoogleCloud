> ## CONFIGURANDO CHAVE SSH

<br>

Digite **ssh-keygen -t "tipo de chave"** ou **ssh-keygen** (será criado o padrão id_rsa)

Digite o nome ou deixa padrão

Digite uma senha ou deixe sem para finalizar a criação da chave.

Digite **eval $(ssh-agent)** para iniciar o processo do agente e tambem definir as variais de ambiente

Digite **ssh-add ~/.ssh/id_rsa** para adicionar a identidade dentro do SSH

Copie oque tem dentro da pasta ~/.ssh/id_rsa.pub (pode usar o comando **cat ~/.ssh/id_rsa.pub**)

Adicione na plataforma que você ira integrar, como Google Cloud, Git, Aws e etc.

<br>

> ## CONFIGURANDO GIT P/ DEPLOY
 
<br>

**git config --global user.email "meu@email"** para configurar um email para ser registro dos commits

**git config --global user.email "Meu nome"** para configurar um nome para registro dos commits

**git init** para iniciar o git

**git add .** para adicionar todas as mudanças feitas em arquivos rastreados para o staging area

**git commit -am "msg commit"** para commitar (adicionar uma nova versão do repositório)

<br>

> ## ENVIANDO REPOSITÓRIO PARA O GOOGLE CLOUD

<br>

Após acessar o servidor do google cloud com o comando **ssh "ip servidor"**

Crie um repositório de metadados dentro do seu user do servidor e inicie o git com **git init --bare**.

Crie um repositório do seu app e inicie o git com **git init**

Adicione um repositório remoto referenciando seu repositório de metadados usando **git remote add "nome da branch(normalmente main)" "caminho do repositório de metadados"**

Volte para seu repositório local (onde esta o seu app) configure o git e commite tudo

Adicione um repositório remoto referenciando o ip do servidor com **git remote add "nome da branch(normalmente origin)" "ip_do_servidor:nome do repositório de metadados"**

Envie os dados do repositório local para o remoto utilizando **git push "nome da branch remota" "nome da branch local"**

Entre no servidor e acesse repositório do seu app

Puxe os arquivos do que estão no repositório de metadados para o repositório do app utilizando o comando **git pull "nome da branch remota" "nome da branch local"**

<br>

> ## CONFIGURAR PM2 NO GOOGLE CLOUD

<br>

**sudo apt install curl -y** para instalar o curl

**curl -sL https://deb.nodesource.com/setup_12.x | sudo bash -** para fazer o download do script de instalação do Node.js

**sudo apt install nodejs -y** para instalar o NodeJS

Va no seu app, instale o node_modules com **npm install** e em seguida instale o pm2 com o comando **sudo npm install -g pm2**

Configure as portas, variaveis do .env e etc.

Inicie o servidor com o comando **pm2 start "caminho do servidor (normalmente ./index.js ou ./server.js)" --name="nome do servidor"**

Configure o script de startup automatico do servidor usando o comando **pm2 startup**

Copie o script informado e cole no bloco de comando

<br>

> ## CONFIGURAR NGINX NO GOOGLE CLOUD

<br>

Digite o comando **sudo apt install nginx** dentro do servidor para instalar o nginx

Digite o comando **sudo systemctl status nginx** para verificar se o nginx está funcionando corretamente

Crie um arquivo de texto dentro de sites-enabled do nginx usando o comando **sudo nano /etc/nginx/sites-enabled/"nome do arquivo de configuração"**

Cole o padrão de configuração do Nginx que você possui e salve

Remova o arquivo default utilizando o comando sudo rm default

Reinicie o nginx usando comando **sudo systemctl restart nginx** para que tudo funcione normalmente
