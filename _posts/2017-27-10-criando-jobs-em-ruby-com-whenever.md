Há um tempo atrás, para um projeto na empresa a qual trabalho,  tive que lhe dar com a questão de criar jobs em RoR
que realize tasks temporariamente, foi ai que encontrei essa gem bastante simples, e eficiente.

Sendo mais específico, a necessidade era de ter um job que ficasse constantemente verificando se tinha algo novo em uma
fila no SQS da amazon. Se caso tivesse, dispararia um método na minha aplicaço. 

De primeira, obviamente, caí na [webpage doc do rails](http://guides.rubyonrails.org), (que por sinal, sensacional), e vi
sobre o Active Job, que é algo nativo, do core. Certo que me proporciona muita utilidades, desde scheduling até mailing, e
usando de toda uma tecnologia de queues...

Porém queria algo menos complexo, mais prático, mais vapt vupt.. Foi ai que apareceu a gem Whenever.


### Uso do gem WHENEVER para cron jobs em ruby ###

### Instalação

```sh
$ gem install whenever
```

Ou com o Bundler

```ruby
gem 'whenever', :require => false
```

### Usando o whenever

```sh
$ cd /apps/meu-projeto
$ wheneverize .
```

Irá criar um arquivo inicial `config/schedule.rb`(verifique se o folder config existe no projeto!)

### Comandos

Para executar seu job, use o comando:
```sh
$ whenever --update-crontab
```
Para ver cron jobs instalados: `crontab -l`.

### Exemplo de schedule.rb

```ruby
every 2.hours do # 1.minute 1.day 1.week 1.month 1.year tambem é suportado
  runner "ModelNome.metodoNome"
end
```
### Avisos extras
Por padrão, o cron é configurado pra rodar em ENV production, então se está querendo rodar em dev, acrescente:
```ruby
every 2.minutes do 
  runner "ModelNome.metodoNome", environment: :development
end
```
