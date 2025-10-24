# Guia de conteúdos do repositório

## ZCCOLCK

JCL que utiliza a procedure IGYWCL para compilar um código-fonte COBOL baseado no template SAMPREQ. **Seus parâmetros estão preenchidos com base no contexto do exemplo**, mas estão todos **comentados para facilitar o reaproveitamento em qualquer outro contexto**.

## COBGO

JCL que executa o programa gerado pelo JOB ZCCOLCK. **Seus parâmetros estão preenchidos com base no contexto do exemplo**, mas estão todos **comentados para facilitar o reaproveitamento em qualquer outro contexto**.

## SAMPREQ

Template de um código-fonte COBOL que faz uma chamada API via z/OS Connect Requester OAS2. **Seus parâmetros não estão preenchidos**, mas existe um passo a passo comentado para que o **preenchimento seja simples**.

# Se você deseja compilar outro tipo de programa

Você pode reaproveitar os JOBS ZCCOLCK e COBGO para compilar, link-editar e executar qualquer outro programa COBOL. E se quiser aproveitar o template SAMPREQ para escrever outro programa COBOL.

# Se você quer fazer uma chamada API utilizando o z/OS Connect Requester OAS2

Recomendamos fortemente que os demais passos contidos nesse arquivo já tenham sido configurados (configuração do server.xml e geracão dos copybooks e do .ara): [Configurando Requester Parte 1](https://github.com/gabriel-paiva17/Compilar-Linkeditar-E-Executar-COBOL/blob/main/configs-para-zcee-req/Configurando%20um%20API%20Requester%20em%20OAS%202%20-%20Parte%201.pdf)

Nesse caso é bem mais simples, o exemplo utilizado faz uma chamada API via **BATCH**, mas pode ser muito útil para outras formas de chamada também. Lembre-se de substituir as variáveis para valores existentes no seu contexto.

# Pré-requisitos

Abaixo está uma lista de elementos que precisam ser encontrados, ou criados para que o programa seja executado. **Lembre-se**: você pode utilizar elementos equivalentes sem problema algum.

<img width="1099" height="110" alt="image" src="https://github.com/user-attachments/assets/53be47d5-df9f-493b-a86c-bcc55f271323" />
