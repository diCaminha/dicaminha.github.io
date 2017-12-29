---
layout: post
title: CRIAÇÃO DE LOOPS EM RANGE DE DATAS (java, js, ruby)
---

Nesse artigo listo algumas formas de criar uma iteração entre datas (dado um range entre uma data inicial e uma final);


+ Em JAVA (usando da biblioteca Joda-Time):

```java
for (LocalDate date = startDate; date.isBefore(endDate); date = date.plusDays(1)){
   //codigo para certo dia aqui
}
```


+ Em Javascript:

```
var dataHoje = new Date();
for (var d = new Date(2012, 0, 1); d <= now; d.setDate(d.getDate() + 1)) {
    //codigo para certo dia aqui
}
```


+ Em Ruby:
```ruby
(Date.new(2017, 01, 01)..Date.new(2017, 12, 29)).each do |dia|
  # codigo para certo dia aqui
end
```
