<img src="https://image.ibb.co/d5CEyR/logofinal_png.png"/>

# Sugestões e dicas

 > Bom, foi notado no decorrer da disciplina que algumas das ferramentas que nós usamos para a nossa aplicação foram um pouco "perigosas", 
 no sentido de poder apresentar problemas no decorrer do desenvolvimento. Mas o intuíto aqui é poder explicar, baseado no nosso projeto, que
 que é possível utilizar algumas dessas ferramentas sem obter problemas.
 

## Devise
> Foi a gem que mais adiantou o nosso projeto, além de que ela foi bastante contestada por vários períodos por apresentar alguns problemas
quando fosse necessário dar o deploy no Heroku. Ela apresenta uma interface de autenticação de usuário completa, além de proporcionar
questões como uma segurança de boa qualidade pelo fato de criptografar a senha dos usuários, e também outras vantagens como ser de fácil
compreensão e implementação. Para informações sobre os processos básicos de instalação, os links utilizados por nós estão a seguir:  
- https://github.com/plataformatec/devise<br/> 
- https://www.youtube.com/watch?v=lXK42-sTIhM  <br/> 
> O primeiro tem a página da gem com informações mais completas
e ao segundo apresenta de forma mais compreensivel como ela funciona em vídeo. <br/> 
### Dificuldades e dicas
> O que eu posso adiantar é que as views do devise foram
bem difíceis de lidar, pois ele trabalha com vários formulários do rails e é difícil de conseguir aplicar, de uma forma fácil, modificações nas 
mensagens de erro. As caixas de input de usuário apresentam problemas de deslocamento na tela, e demoramos bastante para encontrar como corrigir isso,
e acabamos descobrindo que o CSS que cuidava dessa parte estava localizado no arquivo de scaffolds geral da aplicação. Outro problema também que 
que os emails de confirmação e reset de conta não estavam funcionando e não sabíamos o motivos, mas acabamos descobrindo que eram alguns problemas
relacionados ao domínio em que os emails deveriam ser encaminhados. O problema era semelhante a esse: <br/> 
- https://stackoverflow.com/questions/17321939/devise-forgot-password-email-not-received <br/> 
> Sobre questões com o Heroku, não tivemos problemas em relação ao devise, o problema foi com a helper tag de imagens, que no Heroku só
aceitava com os parâmetros entre parênteses. Outra coisa que é necessária ressaltar é que o Devise cria basicamente um scaffold que tem funcionalidades
próprias, então é criada uma migração que é logo direcionada ao banco de dados, então antes de ser migrada ela pode ser customizada para armazenar informações
adicionais dos usuários, para ficar mais completo. Basicamente, outros problemas que foram sendo encontrados ao decorrer da disciplina foram
sanados a partir dos monitores e do Stack Overflow (melhor plataforma do universo).
## Omniauth e Pundit
> Essas gems funcionam diretamente com o devise, o que facilita bastante o desenvolvimento, além de que fazem o seu trabalho de modo a facilitar a implementação das suas tarefas.
A gem do omniauth usada por nós foi o do facebook, mas as com outras plataformas como o gmail tem implementações semelhantes. Aqui está um link
de como implementá-lo: <br/> 
- http://onebitcode.com/criando-autenticacao-com-o-facebook-em-10-minutos-devise-omniauth/<br/>
> O maior problema apresentado no uso dessa gem foi um problema relacionado a autenticação com alguns tipos de conta. A função que pegava as
informações do facebook e colocava como padrão no devise não ficavam consistentes e o usuário sempre era direcionado para a página de cadastro
em um loop eterno. Para resolver esse problema foi necessário fazer uma alteração no modelo do devise para que a função que pegasse esses dados
os armazenasse de maneira padrao, no nosso caso, o uid do usuário sempre era pego de maneira padrão, então o juntamos com o domínio de email
"@facebook.com". Não ficava muito bom esteticamente, mas tinha uma maneira de consertar isso, fazendo como na imagem: <br/>
<img src="https://image.ibb.co/bDDGhw/assa.png"> <br/>
O pundit é uma gem para autorização, nela a partir de uma coluna a mais na tabela de usuários denominada "role", o usuário comum é diferenciado do
administrador, isso garante várias vantagens a aplicação, dentre elas a mais valiosa, a segurança de que algum usuário desavisado não estrague
a aplicação. Ela limita qual página o usuário comum pode acessar. Não tivemos problemas também ao decorrer do uso dessa gem, então vou apenas disponibilizar
de onde nós aprendemos a utilizá-la : <br/>
- https://www.youtube.com/watch?v=kkt-tnKy_9Q <br/>
> Em considerações finais, o que tenho a dizer é, se precisam dessas funcionalidades nas suas aplicações, usem e abusem dessas ferramentas, pois adiantam bastante o desenvolvimento,
 além de proporcionar uma visão melhor de como tudo isso funciona.
 
 ## Action Cable

> Utilizamos o Action Cable, funcionalidade disponibilizada na versão 5 do rails e que nos ajudou a desenvolver um chat em tempo real de forma muito interessante. Segui esse tutorial abaixo para realizar o desenvolvimento, modificando o necessário para o nosso projeto e adicionando melhorias, como, por exemplo, limpar o campo de comentário após a inserção, criar o "layout" para o chat com barra de rolagem e incluir a informação de data e hora no comentário que já faz parte da tabela.
Dica: no tutorial ele não cita a necessidade de ter a gem jquery-rails no seu gemfile, mas ela é necessária para que funcione e também incluir sua dependência //= require jquery no arquivo application.js que fica em app/assets/javascripts
- http://onebitcode.com/como-criar-um-chat-em-tempo-real-usando-action-cable-rails-5/
> Um "problema" de utilizar o Action Cable é que no Heroku, versão gratuita, não é possível acompanhar o chat em tempo real, você precisa comentar e atualizar a página para visualizar novos comentários, para usar em tempo real é preciso pagar pela conta. 

## Chartkick 

> Utilizei para geração dos gráficos e estátisticas a gem chartkick que é muito fácil de usar e possibilita gerar gráficos bonitos e bem feitos, de forma fácil e totalmente iterativa. Segue abaixo o link do site e o do github dos desenvolvedores dessa gem:
- https://www.chartkick.com/
- https://github.com/ankane/chartkick

## Importando arquivo CSV

> A funcionalidade de importação do arquivo CSV deu bastante trabalho, mas foi muito útil após finalizar. Com a importação do arquivo que pegamos no site de dados abertos, importamos e incluimos esses dados nas tabelas do banco da nossa aplicação. Assisti vários vídeos e li várias informações na internet para entender como funcionaria essa importação. Segue abaixo um link do youtube com um vídeo sobre o assunto, importante ressaltar que não usei só esse vídeo e foi preciso vários outros ajuste para contemplar o que eu precisei:
- https://www.youtube.com/watch?v=W8pohTautj8

> Dica: Sempre lembrar de colocar para o formato UTF-8.
 
 ## Outras dicas
 - Sempre que é chamado um gerador do rails, também são criados testes automáticos no Rspec, recomendamos que esses testes sejam excluídos ou revisados, tivemos alguns
 problemas com eles;
 - Não tenha medo de usar o C9, sempre que puder <b>faça um clone!</b>
 - Utilize bem das branchs e aprenda a utilizar bem o Github para não acabar perdendo pontos por desatenção;
 - <b>Sempre, sempre, sempre utilize do Stack Overflow</b>, garantimos que o seu problema não foi o primeiro da face da terra, ele estará lá resolvido em algum lugar, é so saber procurar :);
 - Recomendamos que no começo estudem o rails o mais rápido possível, a estrutura dele é amigável, mas para quem nunca trabalhou com uma framework assim
 pode ser tornar um pesadelo :( 
 
