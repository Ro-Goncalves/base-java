# Um pouco Sobre Maven

## Instalação

Para instalar o maven, é relativamente fácil, basta baixar o binário mais [neste link](https://maven.apache.org/download.cgi). Descompactar em alguma pasta do seu computador. Para deixar a execução dele mais fácil, basta colocar o caminhinho `diretório-maven/bin` no **PATH** de seu SO.

Para testar execute:

```bash
mvn --version

Apache Maven 3.9.1 (2e178502fcdbffc201671fb2537d0cb4b4cc58f8)
Maven home: U:\GIT\util\maven
Java version: 17.0.10, vendor: Oracle Corporation, runtime: C:\Program Files\Java\jdk-17
Default locale: pt_BR, platform encoding: Cp1252
OS name: "windows server 2019", version: "10.0", arch: "amd64", family: "windows"
```

## Criar um projeto

Primeiro, devemos acessas a pasta na qual iremos criar o projeto. Depois utilizando a linha de comando, devemos fazer o seguinte.

Se quisermos usar o modo **interativo**

```bash
mvn org.apache.maven.plugins:maven-archetype-plugin:generate

Choose a number or apply filter (format: [groupId:]artifactId, case sensitive contains): 2110: # para escolher o tipo de projeto
Choose org.apache.maven.archetypes:maven-archetype-quickstart version: # para escolher a versão de maven-archetype-quickstart
1: 1.0-alpha-1
2: 1.0-alpha-2
3: 1.0-alpha-3
4: 1.0-alpha-4
5: 1.0
6: 1.1
7: 1.3
8: 1.4
Choose a number: 8: 8
Define value for property 'groupId': com.rogon # definir o groupId do projeto
Define value for property 'artifactId': demo # definir o artifactId
Define value for property 'version' 1.0-SNAPSHOT: : # definir a versão do projeto
Define value for property 'package' com.rogon: :
Confirm properties configuration:
groupId: com.rogon
artifactId: demo
version: 1.0-SNAPSHOT
package: com.rogon
 Y: : # confirmar tudo o que foi escolhido
```

Ou, podemos passar algumas informações direto no cli

```bash
mvn org.apache.maven.plugins:maven-archetype-plugin:generate -DarchetypeArtifactId="maven-archetype-quickstart" -DarchetypeGroupId="org.apache.maven.archetypes" -DarchetypeVersion="1.4" -DgroupId="com.rogon" -DartifactId="demo" 
```

Onde:
- `org.apache.maven.plugins:maven-archetype-plugin`: Plugin que irá auxiliar na criação do POM
- `generate`: goal do plugin para gerar um projeto a partir de um arquivo de modelo
- `DarchetypeArtifactId`: Indica qual é o modelo que será utilizado
- `DarchetypeGroupId`: Indica a qual grupo o modelo pertence
- `DarchetypeVersion`: Indica a versão do modelo
- `DartifactId`: Indica qual é o nome do seu projeto, ao menos é assim que eu uso, por exemplo *meu-projeto-java-lindo*, *laboratorio*, etc
- `DarchetypeGroupId`: Indica quem está desenvolvendo o projeto, por exemplo, na empresa que trabalho uso *br.com.nomedaempresa* em meus particulares uso *com.rogon*

## POM

É no `pom.xml` que a mágica acontece. Existe bastatante coisas nele, até mesmo nesse simples que é criado no inicio. Vamos as que precisamos saber nesse momento.

```xml
<modelVersion>Versão do modelo utilizado pelo maven</modelVersion>

<groupId>Mesmo que foi definido ao criar o projeto -DarchetypeGroupId</groupId>
<artifactId>Mesmo que foi definido ao criar o projeto -DartifactId</artifactId>
<version>Versão do projeto</version>

<url>URL do site do projeto</url>
<name>Nome do projeto, mesmo que artifactId</name>
<properties>Contém as propriedades do projeto</properties>
<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
<maven.compiler.source>1.17</maven.compiler.source>
<maven.compiler.target>1.17</maven.compiler.target>

<packaging>: tipo de empacotamento que o Maven irá utilizar quando o usuário quiser fazer a distribuição do projeto.

<name>: nome do projeto. Diferentemente do artifactId, não faz parte da identificação do projeto. O valor padrão é o valor do artifactId.

```


## Referências

- [Andeson Gome - Maven Criando um Projeto Maven Simples](https://medium.com/@andgomes/criando-um-projeto-maven-simples-a2ad88b25e78)
- [Maven](https://maven.apache.org/ref/3.9.6/maven-model/maven.html)
