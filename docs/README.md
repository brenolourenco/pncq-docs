## Repo de documentação do PNCQ

### Levantar servidor

Para levantar o servidor da documentação, basta executar esse comando abaixo no terminal do Linux

```shell
docker run \
  -d -p 3000:3000 \
  -v ~/repos/pncq-docs/docs:/usr/local/docsify \
  --name pncq-docs \
  littlstar/docker-docsify

# Obs: Sempre verificar o caminho correto da pasta docs
```
### Permissão para alterar os arquivos (fazer commits)

Caso não esteja sendo possível salvar as alterações nos arquivos, fornecer permissão no terminal do Linux conforme comandos abaixo

```shell
sudo chown -R cpd ~/repos
```

### Acessar a documentação pelo navegador

Para acessar via servidor interno basta digitar na barra de endereços do navegador http://192.168.0.246:3000 ou https://celsojr-pncq.github.io/pncq-docs/ para acesso público via internet

### Comandos do Docker usados com frequência

```shell
# Para verificar se o container está no ar
docker ps | grep 'docsify'

# ou se não estiver no ar
docker ps -a | grep 'docsify'

# Verificar os logs de erro do container
docker logs -t pncq-docs

# Para parar o container
docker stop {container id}

# Para dar start novamente no container
docker start {container id}

# Remover container parados e desnecessários
# ATENÇÃO: Validar os filtros a fim de não remover outros containers acidentalmente
docker rm $(docker ps -a | grep 'docsify' | awk {'print $1'})
```
