# Guia de Falas — Aula 01: Lógica, Condicionais e Loops em C
## IbTech — Encontro 01

**Duração total:** ~2h
**Apresentador:** Igor
**Linguagem:** C

---

## SLIDE 1 — Capa (2 min)

"Fala, pessoal! Bem-vindos ao primeiro encontro oficial da IbTech. Hoje a gente vai do zero até um programa que toma decisões e repete ações. Vocês vão sair daqui com um joguinho rodando no computador de vocês."

"A gente escolheu C de propósito. É a mãe de quase toda linguagem moderna. Mais difícil no começo, mas quem entende C não sofre com nada depois."

---

## SLIDE 2 — Agenda (1 min)

"Três blocos: primeiro a gente monta a base (lógica, como escrever e rodar um programa em C). Segundo: if/else, ensinando o computador a decidir. Terceiro: loops, ensinando a repetir. No final, exercício prático que junta tudo."

---

## BLOCO 1 — BASE (~30 min)

---

## SLIDE 3 — 1 e 0 (4 min)

"O computador pensa em 1 e 0. Verdadeiro e falso. Em C isso é literal: o número 0 é falso, qualquer outro número é verdadeiro. Se vocês escreverem if(1), sempre entra. if(0), nunca entra. Não tem tipo booleano original no C."

**Interativo:** Perguntas pro público responder 1 ou 0.

---

## SLIDE 4 — Operadores (6 min)

Passar pelos operadores lógicos e de comparação. Focar nos símbolos de C:

"E é &&. OU é ||. NÃO é !. Igualdade é ==, não =. Essa confusão entre = e == vai ser o erro número 1 de vocês. Um guarda valor, o outro compara."

Usar exemplos rápidos verbais: "Se tem dinheiro E não tá chovendo: if(dinheiro && !chovendo)"

---

## SLIDE 5 — Ambiente (10 min)

Guiar instalação ao vivo. Beatriz e monitores ajudam.

**Passo 1 — VS Code:** "Quem não tem, baixa na Microsoft Store (Windows) ou brew no Mac."

**Passo 2 — Extensões:** "Dentro do VS Code, clica no ícone de quadradinhos na lateral esquerda (Extensions). Busca e instala duas extensões:"
- "C/C++ da Microsoft — dá syntax highlight, autocomplete e detecção de erros"
- "Code Runner do Jun Han — coloca um botão de Play pra rodar o código com um clique"

**Passo 3 — GCC:** "O Code Runner precisa do GCC instalado por baixo. Windows: MinGW. Mac: abre o terminal e digita xcode-select --install. Linux: sudo apt install gcc."

"Pra testar: abram o terminal do VS Code (Ctrl+` ou View > Terminal), digitem gcc --version. Se apareceu a versão, tá funcionando."

**Configuração importante do Code Runner:** "Vão em Settings (Ctrl+,), busquem 'code runner run in terminal' e marquem a opção. Isso faz o programa rodar no terminal integrado ao invés do Output, que é necessário pro scanf funcionar."

"Criem uma pasta ibtech. Dentro, arquivo aula01.c. Extensão .c obrigatória."

"Pra rodar: cliquem no triângulo de Play no canto superior direito ou usem Ctrl+Alt+N. O Code Runner compila e roda pra vocês. Não precisa digitar gcc no terminal."

**Plano B:** Se alguém não conseguir instalar GCC, usar https://www.onlinegdb.com/online_c_compiler no navegador.

---

## SLIDE 6 — Anatomia (8 min)

**Este é o momento mais importante da aula. Ir devagar.**

Digitar junto:

```c
#include <stdio.h>

int main() {
    printf("Hello World!\n");
    return 0;
}
```

Explicar cada linha:

"#include <stdio.h> — é importar a caixa de ferramentas. Sem isso, printf e scanf não existem. stdio = Standard Input Output."

"int main() — função principal. Todo programa C começa aqui. O int diz que ela retorna um número inteiro."

"{ } — chaves abrem e fecham o bloco. Tudo que tá dentro das chaves pertence ao main."

"printf — exibe texto. O \n pula linha. Sem \n, o cursor fica colado."

"; — ponto e vírgula no final de toda instrução. Esquecer é o erro mais frequente. O compilador vai reclamar."

"return 0 — diz pro sistema: acabou sem erros. Zero é convenção de sucesso."

**Compilar e rodar ao vivo:** "Salvem. Cliquem no Play (triângulo no canto superior direito). Apareceu Hello World no terminal lá embaixo? Parabéns, primeiro programa em C."

---

## SLIDE 7 — Variáveis (5 min)

"Em C, vocês declaram o tipo antes de usar. Não é como Python que adivinha."

Digitar junto e explicar:

```c
int idade = 21;        // inteiro
float nota = 8.5;      // decimal
char letra = 'A';      // UM caractere, aspas SIMPLES
char nome[50] = "Igor"; // texto, aspas DUPLAS
```

"char com aspas simples: um caractere. String com aspas duplas: vários caracteres. Trocar dá erro."

"O [50] no nome significa: reservei espaço pra 50 caracteres. Em C, string não é tipo nativo, é um array de chars."

---

## SLIDE 8 — Printf e Scanf (8 min)

**Printf:**

```c
printf("Nome: %s\n", nome);
printf("Idade: %d\n", idade);
printf("Nota: %.1f\n", nota);
```

"%d pra int, %f pra float, %s pra string, %c pra char. A ordem das variáveis depois da vírgula corresponde à ordem dos % no texto."

**Scanf:**

```c
printf("Seu nome: ");
scanf("%s", nome);       // string: SEM &

printf("Sua idade: ");
scanf("%d", &idade);     // int: COM &
```

"O & é endereço de memória. O scanf precisa saber ONDE guardar. Pra int, float, char: usa &. Pra string: o nome do array já é o endereço, não precisa."

"Esquecer o & é o erro número 2 em C. Compila, roda, e dá comportamento estranho."

**Teste rápido:** Todo mundo faz um programa que pede nome e idade e imprime.

---

## BLOCO 2 — CONDICIONAIS (~35 min)

---

## SLIDE 9 — Transição (1 min)

"Agora que vocês sabem pedir dados e mostrar na tela, vamos ensinar o computador a tomar decisões."

---

## SLIDE 10 — if/else (10 min)

Digitar junto:

```c
int idade;
printf("Sua idade: ");
scanf("%d", &idade);

if (idade >= 18) {
    printf("Maior de idade\n");
} else {
    printf("Menor de idade\n");
}
```

"Condição entre parênteses. Bloco entre chaves. Se verdadeiro, entra no if. Se falso, entra no else."

"O else é opcional. Se vocês não precisam fazer nada quando for falso, não precisa ter else."

**Compilar e rodar.** Testar com valores diferentes.

**Exercício rápido (3 min):** "Façam um programa que pede um número e diz se é positivo, negativo ou zero." Deixar eles tentarem antes de mostrar solução.

---

## SLIDE 11 — else if (10 min)

"E se tiver mais de duas opções?"

Digitar junto o exemplo das notas:

```c
float nota;
printf("Nota: ");
scanf("%f", &nota);

if (nota >= 9.0) {
    printf("A\n");
} else if (nota >= 7.0) {
    printf("B\n");
} else if (nota >= 5.0) {
    printf("C\n");
} else {
    printf("Reprovado\n");
}
```

"O programa testa de cima pra baixo. No primeiro verdadeiro, entra e ignora o resto. Se nota é 8.0: testa >= 9? Não. Testa >= 7? Sim. Imprime B. Acabou."

"O else no final pega tudo que não entrou em nenhuma condição anterior. É a rede de segurança."

---

## SLIDE 12 — Combinando condições (5 min)

"Vocês podem juntar condições com && e || dentro do if."

Exemplos rápidos:

```c
// Pode dirigir se tem 18+ E tem carteira
if (idade >= 18 && tem_carteira) {
    printf("Pode dirigir\n");
}

// Final de semana se é sábado OU domingo
if (dia == 6 || dia == 7) {
    printf("Final de semana!\n");
}
```

"Usem parênteses pra controlar a ordem quando misturar && e ||."

---

## SLIDE 13 — Exercício calculadora (10 min)

Mostrar o exemplo da calculadora no slide. Deixar eles digitarem e rodarem.

"Notem o espaço antes do %c no scanf: scanf(' %c', &op). Esse espaço é pra ignorar o Enter que ficou no buffer do teclado. Sem ele, o scanf pula a leitura do char. É uma peculiaridade do C."

"Salvem e cliquem no Play pra rodar."

"E olhem a divisão: testamos b != 0 junto com op == '/' usando &&. Dividir por zero em C não dá erro bonito, dá comportamento indefinido."

---

## BLOCO 3 — LOOPS (~35 min)

---

## SLIDE 14 — Transição (1 min)

"Condicionais ensinam o computador a decidir. Loops ensinam a repetir. É onde o computador mostra pra que veio: fazer a mesma coisa milhões de vezes sem cansar."

---

## SLIDE 15 — while (10 min)

Digitar junto:

```c
int contador = 1;

while (contador <= 5) {
    printf("Contando: %d\n", contador);
    contador++;
}
```

"while = enquanto. Enquanto contador for menor ou igual a 5, repete. A cada volta, soma 1."

"contador++ é atalho de C pra contador = contador + 1. Funciona igual."

"Se vocês esquecerem o contador++, o programa roda pra sempre. Loop infinito. Pra sair: Ctrl+C no terminal do VS Code."

**Salvar e clicar no Play pra rodar.**

**Exercício rápido:** "Façam um programa que pede uma senha e só aceita 1234. Se errar, pede de novo."

```c
int senha = 0;
while (senha != 1234) {
    printf("Senha: ");
    scanf("%d", &senha);
}
printf("Acesso liberado!\n");
```

---

## SLIDE 16 — for (10 min)

"O for é pra quando vocês sabem quantas vezes vai repetir."

Digitar junto:

```c
for (int i = 1; i <= 5; i++) {
    printf("Contando: %d\n", i);
}
```

"Mesmo resultado do while, mas tudo em uma linha: inicialização (int i = 1), condição (i <= 5), incremento (i++)."

**Exercício ao vivo:** Tabuada.

```c
int num;
printf("Tabuada de qual numero? ");
scanf("%d", &num);

for (int i = 1; i <= 10; i++) {
    printf("%d x %d = %d\n", num, i, num * i);
}
```

"Salvem e cliquem no Play. Testem com números diferentes."

---

## SLIDE 17 — while vs for (3 min)

"Regra simples: sabe quantas vezes? for. Não sabe? while."

"Senha: não sei quantas tentativas, while. Tabuada: sei que são 10 linhas, for."

"Os dois fazem a mesma coisa. A diferença é clareza de intenção."

---

## SLIDE 18 — Exercício final: Adivinhe o número (12 min)

"Agora vocês vão fazer um programa que junta tudo: variáveis, scanf, printf, while e if/else."

Mostrar o código do slide. Explicar:

"O programa tem um número secreto (42). O usuário chuta. Se chutou maior, diz 'Menor!'. Se chutou menor, diz 'Maior!'. Repete até acertar. No final, mostra quantas tentativas."

"Isso usa while (repetir até acertar), if/else if (dar a dica), scanf (ler chute), printf (mostrar dica) e ++ (contar tentativas). Tudo que vocês aprenderam hoje."

Deixar 10 minutos pra eles digitarem e clicarem no Play pra testar.

**Desafio extra pra quem terminar rápido:** "Limitem pra 10 tentativas. Se acabar, mostra 'Você perdeu! O número era 42.' Dica: podem usar uma variável de controle ou adicionar uma condição no while."

Solução do desafio (mostrar só se pedirem):

```c
while (chute != secreto && tentativas < 10) {
```

E no final:

```c
if (chute == secreto) {
    printf("Acertou em %d tentativas!\n", tentativas);
} else {
    printf("Perdeu! O numero era %d\n", secreto);
}
```

---

## SLIDE 19 — Encerramento (5 min)

"Pra fechar: hoje vocês viram lógica booleana, anatomia de um programa C, variáveis, printf, scanf, if/else/else if, while e for. Bastante coisa pra um encontro, mas vocês agora já conseguem fazer o computador ler dados, decidir e repetir."

"Próximo encontro: HTML e CSS. A gente sai do terminal e vai pro visual. Vocês vão aprender como interfaces são construídas e o modelo mental de que tudo na tela é caixa dentro de caixa."

"Tarefa pra casa: quem não terminou o jogo, termina. Quem terminou, tenta o desafio extra. Dúvidas no grupo."

---

## NOTAS PARA O APRESENTADOR

1. **O bloco 1 é fundação.** Se precisar gastar mais tempo na anatomia (slide 6) e no scanf (slide 8), gasta. Sem isso, os blocos 2 e 3 não funcionam.

2. **Erros de compilação são oportunidades.** Quando alguém levantar a mão com erro, projete na tela e resolva com todo mundo. Os erros mais comuns:
   - Esquecer ; → "expected ';' before..."
   - Esquecer & no scanf → compila mas crash ou lixo
   - Confundir = com == → compila mas comportamento errado
   - Esquecer #include <stdio.h> → "implicit declaration of printf"
   - Aspas duplas no char → "multi-character constant"

3. **Monitores:** Atos (4 anos de C) é o recurso mais forte. Pedro Henrique e Laura Marcolino também podem ajudar. Combine com eles antes.

4. **Plano B:** https://www.onlinegdb.com/online_c_compiler pra quem não conseguir instalar GCC.

5. **Ritmo:** Se o tempo apertar, corte o exercício da calculadora (slide 13) e vá direto pros loops. O exercício final (adivinhe o número) é mais importante porque integra tudo.

6. **O exercício final é o momento de energia.** Incentive competição amigável: "quem adivinhar com menos tentativas?" Isso engaja.

7. **Não cubra: ponteiros, structs, alocação dinâmica, arrays além do char[], funções.** Isso é conteúdo de aulas futuras.
