# protocolo-http-thomas-lamounier

#Fundamentação
-Cliente e servidor: o que acontece desde digitar uma URL no navegador até a página aparecer, de forma resumida?

O cliente coloca a URL e o seu navegador e tenta estabelecer uma conexão com o IP/Servidor dai o cliente manda um REQUEST pro SERVER e gera uma resposta o Cliente recebe e o navegador le o conteudo enviado e mostra pro usuario

-Anatomia da requisição e da resposta: linha inicial, cabeçalhos e corpo. Mostre um exemplo real de cada, tirado do seu próprio servidor.

```
import { pageAlunos, pageContato, pageCursos, pageHome, pageNOTFOUND } from "./view.js";

export function route(req,res) {
    if(req.method === "GET" && req.url === "/"){
        res.writeHead(200, { "Content-Type": "text/html"});
        res.end(pageHome())
        return;
    }
    res.writeHead(404, {"Content-Type": "text/html"})
    res.end(pageNOTFOUND())
}
```

linha inicial

aqui nesse codigo estou falando que se o USER tentar acessar/requerir a URL / (home page ou landpage que nesse caso seria a pagina inicial)
estou ditando que se ele tentar acessar essa pagina ele conseguiria acessar se fosse essa URL caso não seria mandando pra uma pagina não encontrada o 404
isso é um pedido do USER querer acessar o site então a linha inicial é oque o USER quer chegar se ele pediu EX: slasla.com/ ele vai ser madando pra cá mas se não chegar tem que mandar pro 404

cabeçalho

nesse espaço " res.writeHead(200, { "Content-Type": "text/html"});"
o {"Content-type":"text/html"} estou dizendo o tipo do cabeçalho carregado 
cabeçalho é os detalhes tecnicos ele dita oque é oque eu to te mandando

Corpo

```
let produtos = ["teclado", "mouse", "monitor"]

const itens = produtos.map((produto) => `<li>${produto}</li>`).join('');  

const html =`
<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<tittle>lista de produtos</tittle>
</head>
<body>
<h1>OLA SEJA BEM VINDO A LOJA DO TIÃO</h1>
<ul>
<li><a href="">${itens}</a></li>
</ul>
</body>
</html>
`
res.writeHead(200, { 'Content-Type': 'text/html' });
res.end(`${html}`);
```

aqui eu entreguei um corpo HTML pra mostrar os produtos aqui só to pedindo pra me mostrar uma lista e o corpo é isso ele carrega a estrutura as imagens e outras ele carrega a carga do site


Métodos: GET, POST, PUT, PATCH e DELETE, para que serve cada um, e o que significa um método ser seguro e idempotente.

-get

pega informações guardadas no servidor

-post

coloca informações dentro do servidor

-put

coloca informações porém só faz isso sem efeito colateral e faz substituições permanentes

-patch

faz substituições ou alterações parciais porém possui efeito colaterais

-delete

remove/apaga essas informações

Códigos de status: o que representa cada família (1xx a 5xx) e o significado de pelo menos 200, 201, 301, 302, 304, 400, 401, 403, 404, 405 e 500. Explique a diferença entre 401 e 403, e entre 301 e 302.

-200 O código HTTP 200 OK é a resposta de status de sucesso que indica que a requisição foi bem sucedida. Uma resposta 200 é cacheável por padrão.(deu tudo certo)

-201 O status HTTP "201 Created" é utilizado como resposta de sucesso, indica que a requisição foi bem sucedida e que um novo recurso foi criado (a request pra criar algo deu bom)

-301 O código de resposta de status de redirecionamento 301 Moved Permanently do protocolo HTTP indica que o recurso requisitado foi movido permanentemente para a URL dada pelo cabeçalho Localização headers ( seu conteudo foi movido permanentemente)

-302 O código de estado HyperText Transfer Protocol (HTTP) 302 Found indica que o recurso foi temporariamente movido para a URL informada pelo cabeçalho Localização (esse muda temporario até voltar a informação então ele não vai voltar até que volte a informação pra ele mas se a informação nunca for voltar ai vira um 301)

-304 O código de resposta HTTP de redirecionamento do cliente 304 Not Modified indica que não há necessidade de retransmitir a requisição de recursos(desde que foi acessado não alterou)

-400 O código de status de resposta HTTP 400 Bad Request indica que o servidor não pode ou não irá processar a requisição devido a alguma coisa que foi entendida como um erro do cliente (ele não consegue ou não pode te dar oque você pediu por que ele entendeu que nesse seu pedido seu navegador tava com algum tipo de problema antes de pedir)

-401 O código de resposta de status de erro do cliente HTTP 401 Unauthorized indica que a solicitação não foi aplicada porque não possui credenciais de autenticação válidas para o recurso de destino.(você pediu só que aquilo que você pediu não tem autorização pra aquilo por que você não tem credenciais para aquilo você é um ze ninguem tentando entrar na casa branca claramente você não tem autorização)

-403 O código de resposta de status de erro do cliente HTTP 403 Forbidden indica que o servidor entendeu o pedido, mas se recusa a autorizá-lo.(aqui é quando você tem as credenciais mas você não foi autorizado)

-404 A resposta de erro 404 Not Found indica que o servidor não conseguiu encontrar o recurso solicitado (não encontrou oque você queria encontrar)

-405 Este status de resposta indica que o verbo HTTP utilizado não é suportado, por exemplo: a requisição ocorre por meio de um get, porém o único método disponível é o post( é quando você tem a chave mas pra entrar na sua casa não adianta ter a chave porque você só entra na sua casa com a chave da sua casa ela é a unica ou uma das unicas que você consegue acessar sua casa porque só aceita esse tipo de chave)

-500 Quando o servidor retorna um código de erro (HTTP) 500, indica que encontrou uma condição inesperada e que o impediu de atender à solicitação.(quando é erro interno no servidor)

Cabeçalhos: para que servem e o papel de pelo menos Content-Type, Content-Length, Location, Allow, Cache-Control, User-Agent e Accept.













FONTE:https://www.devmedia.com.br/http-get-e-post/41221
https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Reference/Methods/PATCH
https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Reference/Status/500
