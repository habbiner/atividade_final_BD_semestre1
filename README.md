**Instruções**

**Trabalho Final - Modelagem de Banco de Dados**

Para este Trabalho Final, você deverá demonstrar todo o conhecimento adquirido durante o semestre na disciplina de Modelagem de Banco de Dados. Siga as etapas abaixo para desenvolver a Modelagem de Dados Completa:

1. **Cenário:**
   Se passando por uma empresa/usuário, crie um cenário descrevendo a necessidade de um sistema (exemplos: sistema comercial, biblioteca, bancário etc.). Faça um texto detalhado identificando entidades, atributos e relacionamentos. É obrigatório ter no mínimo 5 entidades e todos os tipos de atributos (simples, compostos, multivalorados, derivados e atributos chave) e relacionamentos (UM PARA UM (1:1), UM PARA MUITOS (1:N) e MUITOS PARA MUITOS (N:N)).

2. **Modelagem Conceitual:**
   Faça o Diagrama de Entidade-Relacionamento (DER) completo do cenário criado. Respeite todas as regras do Modelo Entidade-Relacionamento (MER).

3. **Modelagem Lógica:**
   Faça o Modelo Lógico do cenário criado, demonstrando os tipos de dados esperados em cada atributo (varchar, int etc.). Apresente de forma clara as chaves primárias e estrangeiras, bem como a relação entre as tabelas.

4. **Modelagem Física:**
   Faça a implementação desse cenário em algum Sistema de Gerenciamento de Banco de Dados (SGBD) de sua escolha (SQL Server, MySQL etc.).

5. **Dados:**
   Faça a inserção de dados em todas as tabelas, com pelo menos 20 dados em cada tabela.

6. **CRUD:**
   Demonstre por meio de prints o CRUD dentro do SGBD (Inserção de dados, Leitura de Dados, Deleção e Alteração de Dados).

7. **Relatórios:**
   Utilizando a Seleção, Filtro e Ordenação, crie 10 consultas para exibir os dados do seu Banco de Dados, demonstrando principalmente a relação entre as tabelas.

**O que deverá ser entregue:**
- Link do GitHub contendo todos os códigos SQL criados.
- README bem estruturado contendo textos e prints demonstrando domínio nos 7 itens acima solicitados.
- Separe as seções do README usando os títulos: Cenário, Modelagem Conceitual, Modelagem Lógica, Dados, CRUD e Relatórios.

<br>

---

<br>

**Cenário: Sistema de Controle em Laboratório de Análises Clínicas**

No ambiente de um laboratório de análises clínicas, diariamente são recebidas fichas acompanhando amostras de sangue para a realização de três tipos de exames: Hemograma completo, Perfil Bioquímico e Microbiológico. Essas fichas contêm campos obrigatórios como data da coleta, solicitante, material, estudo referente, data de entrada, quantidade de amostras, qualidade do envio, qualidade das amostras, número de identificação da amostra, nome do animal, idade do animal, espécie e sexo.

Atualmente, o controle é realizado por meio de papel, o que levou à necessidade de agilizar o processo e reduzir o uso de papel, muitas vezes faltando informações ou sendo ilegíveis. O banco de dados a ser desenvolvido visa armazenar as fichas das amostras, juntamente com os resultados gerados após a conclusão dos exames. Tanto a ficha de envio quanto os resultados podem ser acessados por meio de uma aplicação web, facilitando o acesso em tempo real dos veterinários aos resultados obtidos.

Cada veterinário terá seu próprio cadastro para acessar os resultados das amostras que enviou ao laboratório. O cadastro incluirá informações como nome completo, RG, CPF, CRMV (indicando se está ativo), especialidade, telefone, e-mail, endereço e estudo referente. Da mesma forma, cada biomédico terá seu cadastro, contendo nome completo, RG, CPF, CRBM (indicando se está ativo), especialidade, telefone, e-mail e endereço.

Informações da fazenda também são necessárias, como nome da fazenda, localização, proprietário, telefone do proprietário e e-mail. Para a liberação dos resultados, é necessário preencher o código do laudo, status do laudo (concluído/pendente), data de liberação, biomédico responsável e se o logbook está preenchido.

**Entidades:**
- Biomédico
- Veterinário
- Amostra
- Fazenda
- Resultado

**Atributos:**
- **Biomédico:**
  - Nome completo
  - RG
  - CPF
  - CRBM (ativo ou não)
  - Especialidade (Humana ou animal)
  - Telefone
  - E-mail
  - Endereço
- **Veterinários:**
  - Nome completo
  - RG
  - CPF
  - CRMV (ativo ou não)
  - Especialidade (Animais de grande ou pequeno porte)
  - Telefone
  - E-mail
  - Endereço
  - Estudo referente (Nome do estudo)
- **Amostra:**
  - Data da coleta
  - Solicitante (Veterinário)
  - Material (Sangue, Urina, Fezes, etc.)
  - Estudo referente
  - Data de entrada
  - Quantidade de amostras
  - Qualidade do envio (Conforme, Tubo aberto e/ou rachados, Fichas molhadas)
  - Qualidade das amostras (Conforme, Coagulada/Hemolisada, Identificação apagada, sem identificação, Outros)
  - Número de identificação da amostra
  - Nome do animal
  - Idade do animal
  - Espécie (Bovino, Equino, Suíno, Ovino)
  - Sexo (Masculino, Feminino)
  - Exames solicitados (Hemograma completo, Perfil Bioquímico, Microbiológico)
- **Fazenda:**
  - Nome da fazenda
  - Proprietário
  - Telefone
  - E-mail
  - Localização
- **Resultado:**
  - Código do laudo
  - Status do laudo (Concluído/Pendente)
  - Data de liberação
  - Biomédico responsável
  - Logbook (Preenchido ou não)

**Relacionamentos:**
1. Veterinário e Amostra:
   - Relacionamento: 1 para N
   - Um veterinário pode enviar várias amostras (1 para N), mas cada amostra está associada a apenas um veterinário.
2. Biomédico e Amostra:
   - Relacionamento: 1 para N
   - Um biomédico pode estar associado a várias amostras (1 para N), mas cada amostra está associada a apenas um biomédico.
3. Amostra e Fazenda:
   - Relacionamento: 1 para 1 (ou 0 para 1, dependendo da relação entre amostra e fazenda)
   - Cada amostra está associada a uma fazenda, indicando a origem da amostra.
4. Amostra e Resultado:
   - Relacionamento: 1 para 1
   - Cada amostra está associada a apenas um resultado.
5. Resultado e Biomédico:
   - Relacionamento: 1 para 1
   - Cada resultado é gerado por apenas um biomédico.
6. Veterinário e Resultado:
   - Relacionamento: N para N
   - Vários veterinários podem estar interessados em ou associados a vários resultados, e vice-versa. Isso pode ser relevante se, por exemplo, diferentes veterinários precisarem acessar os mesmos resultados para uma amostra.

---
<br>

**Modelagem conceitual - DER**

<img src="DER.svg">

---
<br>

**Modelagem Lógica:**

<img src="Modelo lógico.png">

---
<br>

**Modelagem Física:**

Modelagem está na pasta "Scripts/create table.db"

---
<br>

**Dados:**

Scripts de inserção de dados está na pasta "Scripts/dados.db"

---
<br>

**CRUD:**

Todos os prints do CRUD está na pasta "CRUD"

---
<br>

**Consultas: (Todas as prints das consultas estão na pasta "Consultas")**

**Consulta 1 - Informações do Veterinário e Número de Amostra com Estudo**
Esta consulta retorna o nome do veterinário, o número da amostra e o nome do estudo associado à amostra. A junção é realizada usando a correspondência entre o identificador do veterinário e o identificador da amostra.

**Consulta 2 - Amostras Pendentes de Resultado para Espécie Ovina**
Esta consulta recupera o número da amostra e o nome do estudo para amostras de animais da espécie ovina que têm status de laudo pendente. A junção é realizada entre as tabelas de amostra e resultado usando os identificadores correspondentes e a condição de filtro especifica a espécie do animal e o status pendente do laudo.

**Consulta 3 - Resultados Concluídos com Informações do Biomédico e Veterinário**
Essa consulta recupera o código do laudo, o biomédico responsável e o nome do veterinário solicitante para resultados que estão marcados como concluídos. A junção é realizada entre as tabelas de resultado e veterinário usando os identificadores correspondentes, e a condição de filtro é aplicada para incluir apenas resultados concluídos.

**Consulta 4 - Detalhes de Amostras com Qualidade Conforme**
Esta consulta traz informações específicas de amostras, incluindo o número da amostra, nome do estudo e qualidade do envio, limitando os resultados às amostras que possuem a qualidade de envio conforme.

**Consulta 5 - Amostras Coletadas e Ordenadas por Data**
Esta consulta apresenta detalhes das amostras, incluindo número da amostra, nome do estudo e data de coleta. Os resultados são filtrados para incluir apenas amostras coletadas no mês de janeiro e são ordenados pela data de coleta em ordem crescente.

**Consulta 6 - Detalhes de Amostras de Bovinos com Laudo Concluído**
Esta consulta fornece informações detalhadas sobre amostras de bovinos, incluindo número da amostra e nome do estudo. Os resultados são filtrados para incluir apenas amostras de bovinos com laudo concluído.

**Consulta 7 - Relação entre Amostras, Veterinários e Data de Entrada**
Esta consulta apresenta informações sobre amostras, incluindo o número da amostra, o nome do veterinário e a data de entrada. Os resultados são ordenados pelo nome do veterinário e pela data de entrada.

**Consulta 8 - Quantidade Total de Amostras por Fazenda**
Nesta consulta, é apresentado o nome de cada fazenda juntamente com a quantidade total de amostras associadas a essa fazenda. O resultado inclui fazendas mesmo que não tenham amostras associadas.

**Consulta 9 - Amostras Pendentes por Mais de 38 Dias**
Nesta consulta, são apresentados detalhes de amostras pendentes há mais de 38 dias. As informações incluem o número da amostra, o status do laudo e a data de coleta.

**Consulta 10 - Relação entre Veterinários e Biomédicos**
Esta consulta exibe uma relação entre veterinários e biomédicos, apresentando os nomes dos veterinários e biomédicos associados. A ordenação é feita em ordem alfabética dos nomes dos veterinários.