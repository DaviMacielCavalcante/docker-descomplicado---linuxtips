# Define a imagem base como Ubuntu 20.04
FROM ubuntu:20.04

# Define o mantenedor da imagem (informações de contato)
LABEL maintainer="Davilão davilão@gmail.com"

# Atualiza a lista de pacotes e instala o Nginx e o Curl
# Remove arquivos desnecessários para reduzir o tamanho da imagem
RUN apt-get update && apt-get install nginx curl -y && rm -rf /var/lib/apt/lists/*

# Expõe a porta 80 para permitir tráfego HTTP
EXPOSE 80

# Baixa uma imagem específica de um repositório do GitHub e salva no diretório /root/
# (Nota: O comando ADD pode ser usado para baixar arquivos de URLs, mas não é a melhor prática para isso)
ADD https://github.com/DaviMacielCavalcante/SiteFranquiaDarkSouls/blob/main/imagens/ds1/bosses/chaos-witch-quelaag-g.jpg /root/

# Copia o arquivo index.html do host para o diretório /var/www/html/ no container
COPY index.html /var/www/html/

# Define o diretório de trabalho como /var/www/html
WORKDIR /var/www/html

# Define uma variável de ambiente chamada APP_VERSION com o valor 1.0.0
ENV APP_VERSION=1.0.0

# Define o comando padrão que será executado quando o container iniciar
# Neste caso, o Nginx será iniciado
ENTRYPOINT ["nginx"]

# Define os argumentos passados para o comando do ENTRYPOINT
# "-g daemon off;" faz com que o Nginx rode em primeiro plano (necessário para containers)
CMD ["-g", "daemon off;"]

# Define um healthcheck para verificar se o Nginx está funcionando corretamente
# O comando curl -f localhost verifica se o servidor está respondendo
# Se não responder em 4 segundos, o healthcheck falha
HEALTHCHECK --timeout=4s CMD curl -f localhost || exit 1