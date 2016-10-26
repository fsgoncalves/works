# works
trabalhos feitos em referência a faculdade e/ou fora dela.
 /* trabalho da faculdade - linguagem C*/
 /*
Integrantes Grupo 4:
Fernando Gonçalves
Iamasse
Lucas
*/

#include <stdio.h> // A biblioteca stdio contem as funções printf e scanf
#include <stdlib.h> // A biblioteca stdlib funciona como um emulador do prompt do windows
#include <string.h> // A biblioteca string.h funciona para a manipulação das strings.
#include <conio.h> // A biblioteca Conio, disponibiliza funções para a manipulação da tela, assim 

struct dados_aluno{
       char cpf[12], nome[51];
       float nota, presenca;
       struct dados_aluno *prox;
       } *inicio=NULL;
       
struct dados_professor{
       char cod[7], nome[51];
       struct dados_professor *proxi;
       } *inic=NULL;
       
struct dados_curso{
       char nome[30], professor[51], aluno[51];
       struct dados_curso *proxii;
       } *inici=NULL;
       
struct dados_aluno * aluno_primeiro()                                                      // FUNÇÃO PARA
{                                                                                          // CADASTRAR ALUNO
       int resp;                                                                           // PASSA COMO PARAMETRO
        struct dados_aluno *aluno;                                                         // A VARIAVEL 'ALUNO'
        aluno = (struct dados_aluno *) malloc (sizeof(struct dados_aluno));                // TRATA TBM A QTDE DE DIGITOS DO CPF
        gotoxy (1,1);
        printf ("O Aluno possui ensino medio completo? 1 = Sim\n");
        gotoxy (1,2);
        scanf  ("%d", &resp);
        
        if (resp == 1)
       {
           system ("cls");
           fflush (stdin);
           while (strlen (aluno->cpf) < 11 || strlen (aluno->cpf) > 11)
           {
            gotoxy (1,1);
            printf ("Informe o CPF do aluno: \n");
            gotoxy (1,2);
            fgets  ( aluno->cpf, 12, stdin);
            fflush (stdin);
             if (strlen(aluno->cpf) == 11)
                {        
                  gotoxy (1,3);
                  printf ("Informe o nome do aluno: \n");
                  gotoxy (1,4);
                  gets   (aluno->nome);
                  aluno->prox=NULL;
                  return (aluno);
                }
             else 
              printf ("\n\nQuantidade de digitos invalidas.\n");
              getch();
              system ("cls");
           }
       }
        else
         printf ("Ensino medio eh pre-requisito para efetuar a matricula.");
         getch();
         fflush (stdin);

}

void demais_alunos(struct dados_aluno *aluno)                                            // FUNÇÃO PARA
{                                                                                        // CADASTRAR
   int resp1;                                                                            // ALUNOS
   struct dados_aluno *aux, *alunos;                                                     // RECEBE COMO PARAMETRO
   aux = aluno;                                                                          // A VARIAVEL 'ALUNO'
   
   gotoxy (1,1);
   printf ("O Aluno possui ensino medio completo? 1 = Sim\n");
   gotoxy (1,2);
   scanf  ("%d", &resp1);
   system ("cls");
   fflush (stdin);
   
   if (resp1 == 1)
   {                    
      while (aux->prox != NULL) 
     
        aux = aux->prox;
        alunos = (struct dados_aluno *) malloc (sizeof(struct dados_aluno));
         
          while (strlen (alunos->cpf) < 11 || strlen (alunos->cpf) > 11)
          {
             gotoxy (1,1);
             printf ("Informe o CPF do aluno: \n");
             gotoxy (1,2);
             fgets  ( alunos->cpf, 12, stdin);
             fflush (stdin);
             if (strlen(alunos->cpf) == 11)
                    { 
                       gotoxy (1,3);
                       printf ("Informe o nome do aluno: \n");
                       gotoxy (1,4);
                       gets (alunos->nome);
                       alunos->prox=NULL;
                       aux->prox = alunos;
                    }
             else
                   {
                     printf ("\n\nQuantidade de digitos invalidas.\n");
                     getch();
                     system ("cls");
                   }
                  
          }
     
  }
   else
         printf ("Ensino medio eh pre-requisito para efetuar a matricula.\n");
         system ("pause");
         fflush (stdin);
    
 
}

struct dados_professor * professor_primeiro()                                                     // FUNÇÃO PARA
{                                                                                                 // CADASTRAR
      struct dados_professor *professor;                                                          // PROFESSOR
      professor = (struct dados_professor *) malloc (sizeof(struct dados_professor));             // PASSA COMO PARAMETRO
                                                                                                  // A VARIAVEL 'PROFESSOR'
      gotoxy (1,1);
      printf ("Informe o codigo do professor: \n");
      gotoxy (1,2);
      gets (professor->cod);
      gotoxy (1,3);
      printf ("Informe o nome do professor: \n");
      gotoxy (1,4);
      gets (professor->nome);
      professor->proxi=NULL;
      return (professor);
}

void demais_professores (struct dados_professor *professor)                                             // FUNÇÃO PARA
{                                                                                                       // CADASTRAR
     struct dados_professor *aux, *professores;                                                         // PROFESSORES
     aux = professor;                                                                                   // RECEBE COMO PARAMETRO
                                                                                                        // A VARIAVEL 'PROFESSOR' 
     while (aux->proxi != NULL)
            aux = aux->proxi;
            professores = (struct dados_professor *) malloc (sizeof(struct dados_professor));
            
            gotoxy (1,1);
            printf ("Informe o codigo do professor: \n");
            gotoxy (1,2);
            gets (professores->cod);
            gotoxy (1,3);
            printf ("Informe o nome do professor: \n");
            gotoxy (1,4);
            gets (professores->nome);
            professores->proxi=NULL;
            aux->proxi = professores;
}

struct dados_curso * curso_primeiro()                                                      // FUNÇÃO QUE
{                                                                                          // CADASTRA CURSO
      int resp, resp1;                                                                     // PASSANDO COMO PARAMETRO A VARIAVEL 'CURSO'
      struct dados_aluno *listaluno;
      listaluno = (struct dados_aluno *) malloc (sizeof(struct dados_aluno));
      struct dados_professor *listaprofessor;
      listaprofessor = (struct dados_professor *) malloc (sizeof(struct dados_professor));
      struct dados_curso *curso;
      curso = (struct dados_curso *) malloc (sizeof(struct dados_curso)); 
      
      
      gotoxy (1,1);
      printf ("Digite o nome do curso: \n");
      gotoxy (1,2);
      gets (curso->nome);
      for (listaluno = inicio; listaluno != NULL; listaluno = listaluno->prox)                          // LISTA OS
      {                                                                                                 // ALUNOS
          printf ("Aluno: %s", listaluno->nome);                                                        // CADASTRADOS
          printf ("\nO aluno esta matriculado neste curso? 1 = Sim\n");
          scanf  ("%d",&resp);
          if (resp == 1)
                strcpy (curso->aluno, listaluno->nome);                
      }
      
     for (listaprofessor = inic; listaprofessor != NULL; listaprofessor = listaprofessor->proxi)        // LISTA OS
      {                                                                                                 // PROFESSORES
          printf ("Professor: %s,", listaprofessor->nome);                                              // CADASTRADOS
          printf ("\nO professor da aula neste curso? 1 = Sim\n");
          scanf  ("%d", &resp1);
          if (resp1 == 1)
                strcpy (curso->professor, listaprofessor->nome);                      
      }
      curso->proxii=NULL;
      return (curso);

}

void demais_cursos (struct dados_curso * curso)                                         // FUNÇAÕ QUE 
{                                                                                       // CADASTRA OS DEMAIS OUTROS CURSOS
      int resp, resp1;                                                                  // RECEBENDO COMO PARÂMETRO A VARIAVEL 'CURSO'
      struct dados_aluno *listaluno;
      listaluno = (struct dados_aluno *) malloc (sizeof(struct dados_aluno));
      struct dados_professor *listaprofessor;
      listaprofessor = (struct dados_professor *) malloc (sizeof(struct dados_professor));
      struct dados_curso *aux, *cursos;
      aux = curso;
     
     while (aux->proxii != NULL)
            aux = aux->proxii;
            cursos = (struct dados_curso *) malloc (sizeof(struct dados_curso));
            
            gotoxy (1,1);
            printf ("Digite o nome do curso: \n");
            gotoxy (1,2);
            gets (cursos->nome);
            for (listaluno = inicio; listaluno != NULL; listaluno = listaluno->prox)  // LISTA OS ALUNOS
                  {                                                                   // CADASTRADOS
                     printf ("Aluno: %s", listaluno->nome);
                     printf ("\nO aluno esta matriculado neste curso? 1 = Sim\n");
                     scanf  ("%d",&resp);
                        if (resp == 1)
                            strcpy (cursos->aluno, listaluno->nome);
                                    
                  }
            for (listaprofessor = inic; listaprofessor != NULL; listaprofessor = listaprofessor->proxi)  // LISTA OS PROFESSORES 
                  {                                                                                      // CADASTRADOS
                     printf ("Professor: %s,", listaprofessor->nome);
                     printf ("\nO professor da aula neste curso? 1 = Sim\n");
                     scanf  ("%d", &resp1);
                        if (resp1 == 1)
                            strcpy (cursos->professor, listaprofessor->nome);
                                    
                  }
            cursos->proxii=NULL;
            aux->proxii = cursos;
}

void editar (struct dados_aluno *aluno)                                             // FUNÇÃO PARA
{                                                                                   // CADASTRAR AS NOTAS E PRESENÇAS DOS ALUNOS
     struct dados_aluno *aux;                                                       // RECEBE COMO PARAMETRO A VARIAVEL 'ALUNO'
     
     aux=aluno;
     while(aux!= NULL)
    //for (aux = inicio; aux != NULL; aux = aux->prox)
     {
        gotoxy (1,1);
        printf("Codigo: %s\n",aux->cpf);
        gotoxy (1,2);
        printf("Aluno: %s\n",aux->nome);
        gotoxy (1,3);
        printf("Digite a nota do aluno: \n");
        gotoxy (1,4);
        scanf ("%f", &aux->nota);
        gotoxy (1,5);
        printf ("Digite a frequencia do aluno: \n");
        scanf ("%f", &aux->presenca);
        system ("cls");
        aux = aux->prox;
     }
}


void listar (struct dados_aluno *aluno)                                                // FUNÇÃO PARA LISTAR OS ALUNOS
{                                                                                      // RECEBE COMO PARAMETRO A VARIAVEL 'ALUNO'
     struct dados_aluno *aux;
     
     aux=aluno;
    while(aux != NULL)
     {
        printf("Codigo: %s\n",aux->cpf);
        printf("Aluno: %s\n",aux->nome);
        printf("Nota: %f\n", aux->nota);
        printf ("Frequencia: %f\n\n", aux->presenca);
        aux = aux->prox;
     }
        system("pause");
}

void listar_curso (struct dados_curso *curso)                                           // FUNÇÃO PARA LISTAR
{                                                                                       // OS CURSOS CADASTRADOS E SEUS
     struct dados_curso *aux;                                                           // RESPECTIVOS ALUNOS / PROFESSORES
     
     aux = curso;
    while(aux != NULL)
  //  for (aux = inici; aux != NULL; aux = aux->proxii)
     {
        printf("Curso: %s\n",aux->nome);
        printf("Aluno: %s\n",aux->aluno);
        printf("Professor: %s\n\n", aux->professor);
    //    aux = aux->proxii;
     }
        system("pause");
}
       
int menu_principal()
{
    int resposta;
    clrscr();
    gotoxy (1,1);
    printf ("|===|=============================|");
    gotoxy (1,2);
    printf ("|||||   M E N U                   |");
    gotoxy (1,3);
    printf ("|===|=============================|\n");
    gotoxy (1,4);            
    printf ("|<1>| CADASTRAR ALUNO             |\n");
    gotoxy (1,5);
    printf ("|<2>| CADASTRAR NOTAS E PRESENCAS |\n");
    gotoxy (1,6);            
    printf ("|<3>| LISTAR    ALUNOS            |\n");
    gotoxy (1,7);
    printf ("|<4>| CADASTRAR PROFESSOR         |\n");
    gotoxy (1,8);                       
    printf ("|<5>| CADASTRAR CURSO             |\n");
    gotoxy (1,9);            
    printf ("|<6>| LISTAR    CURSO             |\n");
    gotoxy (1,10);
    printf ("|<7>| SAIR                        |\n");
    gotoxy (1,11);
    printf ("|===|=============================|\n");
    gotoxy (1,12);
    scanf ("%d", &resposta);
    fflush (stdin);
    clrscr();
    return (resposta);
}

main ()
{
     int opcao=0;

     
     while (opcao != 7)
     {
           opcao = menu_principal();
           
           if (opcao == 1)                                        // CHAMA 
                if (inicio == NULL)                               // O
                    inicio = aluno_primeiro();                    // MENU     
                else                                              // CADASTRAR 
                    demais_alunos(inicio);                        // ALUNO  
                    
                    
           if (opcao == 2)                                        // CHAMA
                if (inicio == NULL)                               // O
                     printf ("Não foram feitos cadastros.\n");    // MENU
                else                                              // CADASTRO DE
                     editar (inicio);                             // NOTAS E PRESENÇAS
                     
                     
           if (opcao == 3)                                        // CHAMA
                if (inicio == NULL)                               // O
                     printf ("Não foram feitos cadastros.\n");    // MENU
                else                                              // LISTAR
                     listar (inicio);                             // ALUNOS
                     
                     
           if (opcao == 4)                                        // CHAMA
                if (inic == NULL)                                 // O
                    inic = professor_primeiro();                  // MENU
                else                                              // CADASTRAR
                    demais_professores(inic);                     // PROFESSOR
                    
                    
           if (opcao == 5)                                        // CHAMA
                if (inici == NULL)                                // O 
                    inici = curso_primeiro();                     // MENU
                else                                              // CADASTRAR
                    demais_cursos(inici);                         // CURSO


          if (opcao == 6)                                         // CHAMA
               if (inici == NULL)                                 // O
                     printf ("Não foram feitos cadastros.\n");    // MENU
                else                                              // LISTAR
                     listar_curso (inici);                        // CURSOS

                
           
     }
}

