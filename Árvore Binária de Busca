#include <cstdio>
#include <cstdlib>

struct no{
int conteudo;
no * dir, * esq;
};

struct arvore{
no * raiz;

void iniciar(int x){
  raiz=new no{x,nullptr,nullptr};
}

void inserir(int x){
  no *aux=raiz, *novo_no=new no{x,nullptr,nullptr};
  while(aux!=nullptr){
    if(x<aux->conteudo && aux->esq!=nullptr){
      aux=aux->esq;
    }
    else if(x<aux->conteudo && aux->esq==nullptr){ 
      aux->esq=novo_no;
      break;
    }
    if(x>aux->conteudo && aux->dir!=nullptr){
      aux=aux->dir;
    }
    else if(x>aux->conteudo && aux->dir==nullptr){ 
      aux->dir=novo_no;
      break;
    } 
  }
}

void aux_mostra(no *n){
    if(n!=nullptr){
     
    aux_mostra(n->esq);
    printf("%d ",n->conteudo);  
    aux_mostra(n->dir);
      }
  }

void mostra(){
aux_mostra(raiz);
printf("\n");
  
}

bool pertence(int x){
  no * n=raiz;
  while(n!=nullptr){
    if(x==n->conteudo){
      return true;
    }
    if(x<n->conteudo){n=n->esq;}
    else {n=n->dir;}//achei que fosse gerar um erro
  }
  return false;
}

void remover(int x){
  no **cima=&raiz;
  no * aux, *del;

  //achando o candidato
  while(true){
    //se for então eu saio do laço
    if(x==(*cima)->conteudo){break;}
    //se for menor eu deço a esquerda se não for nulo
    if(x<(*cima)->conteudo && (*cima)->esq!=nullptr){
      cima=&(*cima)->esq;
    }
    //se for maior eu deço a direita se não for nulo
    else if(x>(*cima)->conteudo && (*cima)->dir!=nullptr){
      cima=&(*cima)->dir;
  }
    //se não é igual menor ou maior é porque é nulo e eu cheguei no fim da 
    //árvore sem achar o elemento x então ele não está na árvore;
    else{break;}
    }
  
  //se eu saí do while e não era nulo então eu achei o cara que vou substituir
  if(*cima!=nullptr){
      // se era folha
      if((*cima)->dir==nullptr && (*cima)->esq==nullptr){
        *cima=nullptr;
        delete *cima;
        return;
      }
      //se tem os 2 filhos
      else if((*cima)->esq!=nullptr && (*cima)->dir!=nullptr){
        //achar predecessor
        //descer pela esquerda uma vez e depois descer a direita até nulo
        aux=(*cima)->esq;
        //se aux não é o predecessor eu deço pela direita até achar ele
        while(aux->dir!=nullptr){
          aux=aux->dir;
        }
        //o filho direito do candidato será filho direito do predecessor
        del=*cima; //guardando para remover mais tarde
        aux->dir=(*cima)->dir;//predecessor->dir receber filho direito do candidato
        *cima=(*cima)->esq;//pai do removido aponta para o filho esq do candidato
        del=nullptr;//torna o candidato em nulo
        delete del;//remove o candidato
        return;
      
      }
      // se tinha 1 filho
      else if((*cima)->dir==nullptr || (*cima)->esq==nullptr){
        
          //se só tem filho esq
        if((*cima)->dir==nullptr){
            aux=*cima;
            //se vou remover a raiz tenho que fazer a raiz apontar para o filho
            if(*cima==raiz){raiz=(*cima)->esq;}
            //se não é a raiz basta fazer o cima apontar para o filho
            else{*cima=(*cima)->esq;}
            delete aux;
            return;
          }
        
          //se só tem filho dir
        if((*cima)->esq==nullptr){
            aux=*cima;
            *cima=(*cima)->dir;
            if(*cima==raiz){raiz=(*cima)->dir;}
            delete aux;
            return;
          }
        
      }
  }
  
  return;
  }

  


};
int main(){
  arvore a;
  
  a.iniciar(100);
  a.inserir(50);
  a.mostra();
  a.inserir(150);
  a.mostra();
  a.inserir(200);
  a.inserir(30);
  a.inserir(55);
  a.mostra();
  a.remover(100);
  a.mostra();
  return 0;
}
