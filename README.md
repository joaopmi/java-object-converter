# java-object-converter

## Dependência

```xml
<dependency>
   <groupId>java.converter</groupId>
   <artifactId>java-object-converter</artifactId>
   <version>2.1.0</version>
</dependency>
```

## Sobre

Biblioteca para conversão de classes Java de um tipo A para um tipo B. Útil em conversão de entidades para DTOs e vice-versa.

É feita a tentativa de conversão de todos os atributos definidos em ambas as classes (A e B), falhando silenciosamente caso não seja possível. 

É possível a conversão de: 

- Objetos fonte para Coleções destino
- Coleções fonte para Coleções destino
- Coleções fonte para Arrays destino
- Arrays fonte para Coleções destino

## Documentação
  
`Documentação (javadoc) e source na dependência.`

## Exemplo

Classe fonte:

```java

public class Fonte{

 private boolean ativo = true;
 private String[] ruas = new String[]{"Esmeralda","Rubi","..."};

 public boolean isAtivo(){
        return this.ativo;
 }

public void setAtivo(final boolean ativo){
        this.ativo = ativo; 
 }

 public String[] getRuas(){
        return this.ruas;
 }

public void setRuas(final String[] ruas){
        this.ruas = ruas; 
 }
}
```

Classe destino:

```java
public class Destino{

 private String ativo;
 private List<String> ruas;

 public boolean isAtivo(){
        return this.ativo;
 }

public void setAtivo(final boolean ativo){
        this.ativo = ativo; 
 }

 public List<String> getRuas(){
        return this.ruas;
 }

public void setRuas(final List<String> ruas){
        this.ruas = ruas; 
 }
}
```

Realiza a conversão:

```java

 public static void main(final String[] args){
  final Destino destino = new ObjectConverter().convert( new Fonte(), Destino.class );
 }
```

Resultado:

```java
public class Destino{

 private String ativo = "true";
 private List<String> ruas;// lista contendo "Esmeralda","Rubi","..."

 public boolean isAtivo(){
        return this.ativo;
 }

public void setAtivo(final boolean ativo){
        this.ativo = ativo; 
 }

 public List<String> getRuas(){
        return this.ruas;
 }

public void setRuas(final List<String> ruas){
        this.ruas = ruas; 
 }
}
```
