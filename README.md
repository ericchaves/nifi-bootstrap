# nifi-bootstrap
Template básico para desenvovimento de fluxos nifi usando docker

# Guia rápido

Utilize o comando ```docker-compose up``` para subir um stack local composto pelos serviços:
- nifi
- mysql
- localstack

Após iniciar o container desenvolva seu fluxo de nifi normalmente. A boa prática é sempre desenvolver um fluxo dentro de um Processor Group e nunca diretamente no canvas facilianto futuramente a reutilização do processor group em outras instâncias de nifi.

Quando o fluxo estiver concluído e validado gere um template de nifi a partir do processor group e depois exporte-o para a pasta ``tempalates``.

O container nifi está linkado com os demais pelos nomes de serviço. Por exemplo, para que um processor possa se conectar no banco de dados mysql ele deve utilizar como nome de host o valor `mysql`.


# Estrutura de pastas

As pastas ```assets,lib,nifi e templates``` estão mapeadas dentro do container de nifi em /opt/nifi/{nome da pasta}.

* assets: utilize para salvar arquivos estáticos como imagens, html templates, etc.
* lib: utilize para salvar bibliotecas (normalmente em .jar) que serão referenciadas por script processors (pasta modules)
* scripts: utilize para salvar o conteúdo dos script processors.
* templates: utilize para salvar fluxos finalizados exportados como tempaltes.
