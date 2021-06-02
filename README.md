# Gerenciamentos
<html>
    <head>
        <title>Lista Ligada</title>
        <meta charset="UTF-8">
        <script src="Metodos_Lista_Ligada.js"></script>
    <script src="Executa_Programa_Lista_Ligada.js"></script>
    </head>
    <body>
        <h1>Título: Gerenciamento de agenda</h1>
        <button type="button" onclick="Programa()">Executar</button>
        <p id="resultado"></p>
    </body>
    <script>
    /* A função No está incompleta
    
*/ //---------------------------------------------------------segunda parte-----------------------------------------------------------------------------------

function No(n,t) {
  this.nome = n;
  this.numero = t;
  this.prox = null;
}

function ListaLigada() {
    this.cabeca = null
}
ListaLigada.prototype.estaVazia = function() {
  if (this.cabeca === null) {
    return true;
  } else {
    return false;
  }
}

ListaLigada.prototype.tamanho = function() {
  var NoAtual = this.cabeca;
  var quantidade = 0;
  while (NoAtual !== null) { 
    quantidade++;  
    NoAtual = NoAtual.prox;
  }
  return quantidade;
};
ListaLigada.prototype.insereNaCabeca = function(n,t) {
  var NovoNo = new No(n,t);
  NovoNo.prox = this.cabeca;
  this.cabeca = NovoNo;  
};


ListaLigada.prototype.insereNoFim = function(valor) {
  var NovoNo = new No(valor);
  var NoAtual = this.cabeca;
  if (this.estaVazia()) {
    this.cabeca = NovoNo;
  } else {
    while (NoAtual.prox !== null) { 
      NoAtual = NoAtual.prox;
    }
    NoAtual.prox = NovoNo;    
  }
};

ListaLigada.prototype.insere = function(posicao, valor) {
  if ((posicao <= 0) | (posicao > (this.tamanho() + 1))) {
    return -1;
  }
  if (posicao == 1) {
    this.insereNaCabeca(valor);
    return 0;
  }  
  var NovoNo = new No(valor);
  var NoAtual = this.cabeca;
  var PosicaoAtual = 1;
  while (PosicaoAtual < (posicao - 1) ) { 
      NoAtual = NoAtual.prox;
      PosicaoAtual++;
  }
  NovoNo.prox = NoAtual.prox;
  NoAtual.prox = NovoNo;
  return 0;
};

ListaLigada.prototype.remove = function(n) {
  if (this.estaVazia()) {
    return -1;
  }
  if (this.cabeca.nome == n) {
    this.cabeca = this.cabeca.prox;
    return 0;
  }
  var NoAtual = this.cabeca;
  var NoAnt = null;
  while ((NoAtual.prox !== null) & (NoAtual.nome != n)) { 
    NoAnt = NoAtual;
    NoAtual = NoAtual.prox;
  }
  if (NoAtual.nome == n) { 
    NoAnt.prox = NoAtual.prox;
    return 0;
  } else {
    return -1;
  }
};

ListaLigada.prototype.removePosicao = function(n) {
  if ((n <= 0) | (posicao > this.tamanho())) {
    return -1;
  }
  var NoAtual = this.cabeca;
  var NoExcluido = null;
  if (n == 1) {
    this.cabeca = NoAtual.prox;
    return 0;
  }  
  var PosicaoAtual = 1;
  while (PosicaoAtual < (n - 1) ) { 
      NoAtual = NoAtual.prox;
      PosicaoAtual++;
  }
  NovoExcluido = NoAtual.prox;
  NoAtual.prox = NovoExcluido.prox;
  return 0;
};

ListaLigada.prototype.posicaoNo = function(valor) {
  if (this.estaVazia()) {
    return -1;
  }
  if (this.cabeca.info == valor) {
    return 1;
  }
  var NoAtual = this.cabeca;
  var NoAnt = null;
  var posicao = 1;
  while ((NoAtual.prox !== null) & (NoAtual.info != valor)) { 
    NoAnt = NoAtual;
    NoAtual = NoAtual.prox;
    posicao++;
  }
  if (NoAtual.info == valor) { 
    return posicao;
  } else {
    return -1;
  }  
};

ListaLigada.prototype.insereOrdenado = function(n, t) {
  var ordernar = new No(n, t);
   if (this.estaVazia()) {
    this.cabeca = ordernar;
    return 1;
  }
  if ( n<this.cabeca.nome ) {
    this.insereNaCabeca (n, t);
    return 2;
  }
  var Aux1, Aux2 ; 
  Aux1 = null;
  Aux2 = this.cabeca; 
  
  while ((Aux2.prox!== null ) && (n > Aux2.nome)) {
  Aux1 = Aux2;
  Aux2=Aux2.prox;
  }
  if (( Aux2.prox===null )&& (Aux2.nome<n)){
  Aux2.prox= ordernar;
  return 3;
  }
  else { 
  ordernar.prox=Aux1.prox ; 
  Aux1.prox = ordernar;
  return 4  ;
  }
};

ListaLigada.prototype.exibeLista = function() {
  var NoAtual = this.cabeca;
  var Texto="";
  Texto="";
  while (NoAtual !== null) { 
    Texto += ""+ NoAtual.nome +  "  :  " + NoAtual.numero + "</br></br>" ;  
    NoAtual = NoAtual.prox;
  }
  Texto += "";
  return Texto;
};

ListaLigada.prototype.Ordernar2 = function() {
  
var NoAtual = this.cabeca;

var Texto="";

Texto="";


 
 while (NoAtual !== ordernar) {
 NoAtual = NoAtual.prox;
 }

Texto += "" + NoAtual.nome +  "  :  " + NoAtual.idade +  " anos  </br></br>" ;
 NoAtual = NoAtual.prox;


  
Texto += "";

return Texto;


}; 
//-----------------------------------------------------------------terceira parte --------------------------------------------------------------------------------

function LimparTela() {
    document.getElementById("resultado").innerHTML = "";
} 
function Mostrar(Texto) {
    document.getElementById("resultado").innerHTML += Texto + "</br></br>";
}
function Menu() {
    var escolha;
    escolha = prompt ("      Menu - escolha uma das opções   \n" +
                         "1 - Inserir novo contato\n" +
                         "2 - Excluir contato\n" +
                         "3 - Procurar contato\n" +
                         "4 - Exibir todos os contato\n" +
                         "5 - Exibir todos os contato em ordem alfabética\n" +
                         "6 - Mostra a quantidade\n" +
                         "7 - Procurar contatos \n" +
                         "8 - Excluir tudo");
           return escolha;
           
}

function opcao1() {
  var  n, t;
  n = prompt("Digite o nome ");
  t = prompt("Digite o  numero");
  
  LLOrdenada.insereOrdenado(n, t);
  LL.insereNaCabeca(n,t);
  Mostrar("Contato inserido com sucesso");
  Mostrar("");
  
}

function opcao2() {
  var n;
  n = prompt("Informe um elemento para ser removido da lista");
  Mostrar("--- Remover um item da lista ---");
  if (LL.remove(n) === 0) {
    Mostrar("Contato removido com sucesso");
  } else {
    Mostrar("***ERRO: Contato não removido da lista");
  } 
}
function opcao3(){
 var valor;
  valor = prompt("Informe um elemento para ser localizado a posição na da lista");
  Mostrar("--- Retorna a posição de um item na lista ---");
  Mostrar("Posição do elemento na lista: " + LL.posicaoNo(valor));  
   
}
function opcao4() {
  Mostrar("Todos os Contatos");
  Mostrar(LL.exibeLista());

  }

function opcao5(){
    Mostrar(LLOrdenada.exibeLista()); 
}
function opcao6(){
Mostrar("--- Retorna o tamanho da lista ---");
  Mostrar("Quantidade de elementos da lista: " + LL.tamanho());
}
function opcao7(){
  var valor;
  valor = prompt("Informe um elemento para ser inserido no fim da lista");
  LL.insereNoFim(valor);
  Mostrar("--- Inserir no fim da lista ---");
  Mostrar("Elemento inserido no fim da lista");  
  }

function opcao8() {    
    LL.cabeca = null;
    Mostrar("Todos os dados foram excluídos!!!")
}

function Programa() {
    var opcao;
    var valor;
    var posicao;
    LimparTela();
    Mostrar("");
    opcao = Menu();
    switch (opcao) {
        case "1":
            opcao1("");
            break;
        case "2":
            opcao2();
            break;
        case "3":
            opcao3();
            break;
        case "4":
            opcao4();
            break;
        case "5":
            opcao5();
            break;
        case "6":
            opcao6();
            break;
        case "7":
            opcao7();
            break;
        case "8":
            opcao8();
            break;
        default:
            Mostrar("Selecione uma opção");
    }
}


var LL = new ListaLigada();
var LLOrdenada = new ListaLigada();
    
    </script>
</html>
