---
layout: post
title: CONCEITOS INTRODUTÓRIOS AO FRAMEWORK WEB JSF
---

Olá, hoje vou trazer aqui alguns pontos importantes para se ter conhecimento caso queira ter um bom background sobre a esoecificação JAVA
**Java Server Faces** (JSF) bastante usado na construção de interfaces de usuário baseada em componentes para app WEB.

*OBS: Esse post é baseado em uma revisão sobre JSF disponível na plataforma de ensino online ALURA*

**1. @ManagedBean**
Objetos anotados com essa Annotation vão ser administrados pelo JSF. Ou seja, será dele a responsabilidade de saber quando instanciar o
objeto.
No arquivo .xhtml, iremos referenciar essas classes através de EL (Expression Language). ex: #{exemploClasse.attr}

**2. Características próprias**
O JSF tem como características:
  . O uso de componentes ricos
  . desenvolvimento orientado ao evento
  . mantém o estado entre as requisições (statefull)

**3. Árvore de Componentes**
 O controlador padrão do JSF irá instanciar todos aqueles componentes criados no arquivo de view .xhtml e criará uma árvore de componentes
 com esses components (ficará guardado em memória). Essa árvore só é construida na primeira requisição (HTTP GET), nas demais, ele recebe 
 um idView correspondente à view que ja foi instanciada uma vez, e então busca sua àrvore correspondente.
 
 **4. Scope Annotations**
 Vão definir quanto tempo vive um Bean na aplicação.
 . @ViewScoped:  vive enquanto acessa mesma pagina, enquanto a tela existe
 . @RequestedScope: vive durante uma requisição
 . @SessionScope:  vive o tempo que durar a sessão do usuário
 . @ApplicationScoped - vive pela aplicação toda
 
 **5. Binding com Beans**
 Os components criados no xhtml possuem attributos que exercem funções de fazer binding com os beans do sistema.
  ex: no componente:  
   ```html 
    <h:commandButton action="#{someObject.someMethod}"
   ```
   Ao clicar no botão, o método someMethod vai ser executado.   E isso é graças ao atributo 'action'
   
   
   **6. Redirecionamento**
   O redirecionamento é feito com o retorno de método com String. Asism, esse valor de String retornado deve ser o nome da página que
   se quer direcionar.
   ```java
    public String form() {
        return "produto?faces-redirect=true";
    }
   ```
   O *faces-redirect=true* significa que o redirecionamento client-side (modificando a URL). Caso não coloque essa string no final da 
   string da página, o redirecionamento vai ser server-side.
   
   **7.Clico de vida**
   O clico de uma requisição no JSF segue a seguinte ordem:
    .Restorar a View
    .Adicionar os valored de request na view carregada
    .Proceso de Validação (Fazer a validação e converção)
    .Atualiza os dados do model correspondente
    .Invoca a aplicação (commandButton ou CommandLink...)
    . Renderiza Resposta
    
    *OBS: No caso do primeiro HTTP GET request, só acontece a primeira e a últimas fases*
    
    **8. Usando Ajax**
    Através do component <h:ajax> Serão feitas requisições via ajax, podendo enviar partes de formulario/página.
    
    **9.Templates com facelets**
    O JSF 2 usa facelets para aplicar templates nas páginas xhtml.
    A associação é feita envolvendo todo o conteúdo da página que importará o template pela tag ui:composition, 
    indicando pelo atributo template, o template a ser associado.
    
    Lembrando que através do ui:define preenchemos as lacunas do template!
