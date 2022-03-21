# Docker

- O Docker tem uma interface de linha de comando para controlar a Docker Engine.
- Com Docker podemos virtualizar containers, imagens, redes, volume, etc, isso gastando menos processamento do que com uma VM.
- A ideia do Docker, de modo geral, é a seguinte:

    "Containers are like diapers" "Containers são como fraldas"

- Isso porque podemos apagar todo o sistema de arquivo que ainda assim poderemos recuperar a imagem.
Geralmente a sintaxe do Docker segue o seguinte padrão:

```
    docker {object} {action}
    docker {container | image | network | volume |etc} {ls | inspect | rm | create}
```

Exemplos:
```
    $ docker container rm alpine
    $ docker image ls
```
<hr/>

## Containers:

- Criando container chamado alpine

    ```
    $ docker container create --name <nome_container> -it <imagem> sh
    ```

- Inicializando container

    ```
    $ docker container start <imagem>
    ```

- Anexando-se a um container:

    ```
    $ docker container attach <imagem>
    ```

- Rodando um container

    ```
    $ docker container run --name <nome_container> -it <imagem> sh
    ```

- Listando containers mostrando o tamanho:

    ```
    $ docker container ls -a -s
    ```

- Parando containers:

    ```
    $ docker container stop <container>
    ```

- Copiando containers:

    ```
    $ docker container cp <src> <dst>
    ```

- Removendo containers:

    ```
    $ docker container rm <nome do container>
    ```

- Inspecionando containers:

    ```
    $ docker container inspect <nome do container>
    ```

- Renomeando containers:

    ```
    $ docker container rename <nome_antigo> <novo_nome>
    ```
<hr/>

## Mapeando Volumes:
Volumes são utilizados para salvar o estado de containers.

```bash
docker container run -v <diretorio_Host>:<diretorio_Container> <imagem>
```
<hr/>

## Mapeando Portas
Geralmente segue a seguinte sintaxe:

```bash
docker run -p <porta_host>:<porta_container> <imagem>
```

Exemplo:
```bash
docker run --name meu-nginx -d -p 8080:80 nginx sh
```

Outro comando importante no Docker é o exec, segue um exemplo de como usa-lo:
```bash
docker container exec <nome_container> <comando>
```

É importante porque com ele conseguimos executar comandos em um container sem precisar entrar no container.

<hr/>

## Imagens
- Exportando container para uma imagem:
```bash
docker container commit <nome_container> mynewimage
```

- Exportando uma imagem para um arquivo .tar:
```bash
docker image save mynewimage> /tmp/mynewimage.tar 
```

- Importando uma imagem a partir de um arquivo .tar:
```bash
docker image load < /tmp/mynewimage.tar
```

- Listando imagens
```bash
docker image ls
```

- Removendo imagens
```bash
docker image rm <nome_id_imagem>
```

- Construindo imagens a partir de Dockerfiles:
```bash
docker image build -t <nome_imagem> <contexto>
```

- Obtendo histórico de uma imagem:
```bash
docker image history <nome_imagem>:<versão>
```
<hr/>

Além de containers e imagens com o Docker também é possível gerenciar outros objetos, por exemplo:
- networks
- node
- plugin
- secret
- service
- stack
- swarm
- volume