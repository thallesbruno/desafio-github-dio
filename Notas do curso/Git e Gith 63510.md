# Git e Github

Git Introdução

- Motivação - Registrar alterações realizadas em um projeto/arquivo/script/qualquer coisa que seja feito por uma pessoa apenas ou por um grande time
- Versionamento de arquivos
- Criado por Linus Torvalds
- Open source
- Benefícios
    - Controle de versão
    - Armazenamento em nuvem
    - Trabalho em equipe
    - Melhorar seu código
    - Reconhecimento

Command Line Interface e Instalação

- GUI x CLI
- Windows - cd/mkdir/dir/del
- Linux - cd/mkdir/ls/rm -rf

Funcionamento do Git

- SHA1
    - Usa funções hash para criptografar (encriptação gera conjunto de caracteres de 40 dígitos)
    - É uma forma curta de representar um arquivo
    
    ```bash
    echo "ola mundo" | openssl sha1
    (stdin)= d9802fa01c4c1dfc4ddaf61f766d8d56ad8a8699
    ```
    

Objetos internos

- Blobs
    
    ```bash
    ➜  ~ echo 'conteudo' | git hash-object --stdin
    fc31e91b26cf85a55e072476de7f263c89260eb1
    ➜  ~ echo 'conteudo' | openssl sha1
    (stdin)= 65b0d0dda479cc03cce59528e28961e498155f5c
    ```
    
    ![Untitled](Git%20e%20Gith%2063510/Untitled.png)
    
    ```bash
    ➜  ~ echo 'conteudo' | git hash-object --stdin
    fc31e91b26cf85a55e072476de7f263c89260eb1
    ➜  ~ echo -e 'blob 9\0conteudo' | openssl sha1
    (stdin)= fc31e91b26cf85a55e072476de7f263c89260eb1
    ```
    
    - Git guarda os arquivos usando SHA1 e adiciona metadados do próprio Git dentro da informação criptografada
- Trees
    - Armazenam Blobs
    - Monta a estrutura dos arquivos
    
    ![Untitled](Git%20e%20Gith%2063510/Untitled%201.png)
    
    ![Untitled](Git%20e%20Gith%2063510/Untitled%202.png)
    
- Commits
    - Elemento essencial do Git
    - Quando se tem um commit, tem a garantia de que ele é único
    
    ![Untitled](Git%20e%20Gith%2063510/Untitled%203.png)
    
    ![Untitled](Git%20e%20Gith%2063510/Untitled%204.png)
    
- Sistema distribuído e Seguro
    - É quase impossível alterar um commit, por isso a versão que existe em uma máquina, se estiver atualizada, é exatamente a mesma que estiver no servidor ou que estiver em uma outra máquina qualquer. Isso por conta da organização de blobs, trees e commits

Chave SSH e Token

- Github força a utilização de SSH para enviar os códigos em seus servidores (a partir de 2021)
- *Criar chave SSH (privada e pública)*
- *Adicionar no Github*
- Token
    - Usar para liberar o download via HTTPS, assim gera o token e passa para a pessoa que irá baixar o repositório via HTTPS

Iniciando Git

- Comandos básicos
    - git init
    - git add .
    - git commit -m
    - git config —global user.email
    - git config —global user.name

Ciclo de Vida no Git

![Untitled](Git%20e%20Gith%2063510/Untitled%205.png)

- Explicando a imagem:
    - Arquivo não é rastreado pelo Git
    - Adiciona o arquivo ao rastreamento, ele vai para Staged
    - Edita o arquivo, ele vai de Unmodified para Modified
    - De Modified ele vai para Stagged
    - De Stagged o arquivo fica pronto para o Commit
    - Feito o Commit, o arquivo volta para Unmodified e fica pronto para ser alterado novamente
    - Se quiser, pode ser feita a remoção do arquivo do rastreamento, voltando ele para Untracked
- Estrutura com servidor remoto (Github, Gitbucket, servidor remoto próprio, etc.)
    
    ![Untitled](Git%20e%20Gith%2063510/Untitled%206.png)
    

Resolvendo conflitos no Github

- Quando baixamos uma versão do projeto do Github, realizamos a alteração e ao mesmo tempo outra pessoa baixa esse projeto e altera esse mesmo arquivo e realiza o git push, a versão que está em nossa máquina torna-se desatualizada. Quando tentarmos realizar o git push será mostrada uma mensagem de erro, apontando que deve ser verificado o arquivo antes de realizar, assim é necessário fazer um git pull (provavelmente irá solicitar para fazer um git merge)
    
    ![Untitled](Git%20e%20Gith%2063510/Untitled%207.png)
    
- Passo a passo
    - Abrir o arquivo
    - Verificar as divergências
    - Corrigir no arquivo e salvar
    - git add .
    - git commit -m
    - git push
- git remote -v
    - visualizar repositórios remotos