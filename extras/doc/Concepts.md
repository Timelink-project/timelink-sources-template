# Conceitos básicos para gestão do processo de transcrição

## Resumo

4 fases no processo de tratamento dos dados: _transcrição, tradução, importação e identificação_.

### Transcrição

Corresponde à produção de um ficheiro de texto, numa notação especial denominada `kleio`, com a informação contida na fonte histórica. Esta fase é feita por um operador (_transcritor_) num programa de processamento de texto, sendo recomendado o `Visual Studio Code` com extensões que facilitam a introdução da notação `kleio`.

### Tradução

Corresponde à extração de dados da transcrição, e criação de um ficheiro de dados, passível de ser importado num programa de gestão de dados.  Esta fase é feito pelo `Timelink`.

### Importação

Processamento de um ficheiro de dados produzido na fase de tradução, e inserção dos dados numa base de dados. Esta fase é feita no `Timelink`.
### Identificação

Processo de determinação que diferentes referências a pessoas nos dados. Esta fase é feita por um operador (_identificador_) através de um _înterface_ disponibilizado pelo `Timelink`.

###  Diferentes tipos de ficheiros   
* transcrição: `.cli`
* tradução: `.xml`, com os dados extraídos do ficheiro `.cli`,e relatórios de tradução `.rpt`,`.err` e ficheiros auxiliares `.str`,`.srpt`, `.inf`).
* importação: `.sql` para cópias de segurança da base de dados.
* identificação: `.cli`, que incluem índices de ocorrências de pessoas identificadas, funcionam como um índice.

Os diferentes ficheiros são geridos pelos diferentes intervenientes através de um repositório `Git`.

# A gestão dos ficheiros de um projeto `Timelink`
## Cada projeto tem um repositório `Git` de referência.

A cada projeto `Timelink` corresponde um repositório `Git` de referência, que contém todos os ficheiros gerados pelo processo de transcrição, tradução, importação e identificação.

`Git` é uma ferramenta criada para gerir o conteúdo de ficheiros que se alteram ao longo do tempo pelo contributo sucessivo de várias pessoas. 

>O `Git` é tipicamente usado em projectos informáticos em que o resultado final é um programa de computador. Nesses projectos é necessário integrar contributos de várias pessoas e alterações frequentes a ficheiros, devido a correção de erros ou implementação de novas funcionalidades.

_Repositório_ é o nome dado ao conjunto dos ficheiros de um projeto, que inclui também a história das alterações feitas aos ficheiros ao longo do tempo. Os repositórios `Git` permitem em qualquer momento saber quem e quando fez alterações a cada ficheiro, voltar a versões anteriores, e combinar alterações feitas por diferentes pessoas numa versão final.

> No `Timelink` o `Git` é utilizado para controlar os ficheiros com transcrições de fontes históricas, recolhidos por uma ou várias pessoas, e as identificações de co-ocorrências de pessoas e entidades nas fontes. 

Os reposítórios podem ser partilhados via internet, usando um serviço de hospedagem. Os projetos `Timelink` usam o serviço `Github`, que permite utilização gratuita mantendo os repositórios privados a um número reduzido de colaboradores.

> Através do `Github` projetos utilizando o `Timelink` podem incorporar o trabalho de vários colaboradores e gerar automaticamanete bases de dados acessíveis na internet

Quando se inicia um novo projecto, ou se migra um projeto existente para este formato, é criado um repositório `Git` acessível via internet.

> Para uma introdução ao `Git`, em português, ver: https://docs.github.com/pt/github/getting-started-with-github
## Acesso de colaboradores aos ficheiros do projeto.

Para permitir o contributo de várias pessoas num projeto, são feitas cópias dos repositórios e agregadas periodicamente as alterações feitas em cada um.

Duas operações sobre repositórios estão na base da organização da cooperação via `Git` na plataforma `github` (outras plataforma usam conceitos similares) : `clonar` e `bifurcar` (_fork_ em inglês).

`clonar` é a operação que efetua uma cópia do repositório da internet para um computador local. O objetivo desta operação é obter uma cópia dos ficheiro para alteração ou processamento num computador específico. Posteriormente à operação de `clonar` os ficheiros locais podem ser enviados de volta para o repositório na internet (operação `push`). A cópia local pode ser autalizada com alterações feitas por outros utilizadores no repositório na internet (operação de `pull`).

`bifurcar` é a operação que cria um novo repositório na internet a partir de um repositório já existe também na internet. O objetivo desta operação é permitir que se altere ou acrescente um repositório sem interferir no conteúdo do repositório de referência. Após a bifurcação as operação de atualização em ambas as direções afectam apenas a cópia do respositório e não o original. Existe uma operação específica para incorporar as alterações feitas na cópia bifurcada com o repositório original (`pull request`).


Diferentes colaboradores do projecto devem bifurcar o repositório de referência. 

Caso o projecto tenha mais que um coordenador que trabalham na mesma organização ou com proximidade e facilidade de contacto, podem trabalhar sobre _clones_ do repositório de referência.

Colaboradores que não pertencem à mesma organização normalmente trabalham sobre repositórios bifurcados. Sobre isto ver: https://github.community/t/branch-vs-fork/1206






A gestão do ramo `master` cabe ao responsável do projecto.


## Se há mais que uma base de dados, cada deve estar associada a um ramo.

Como ficou acima, a base de dados de referência de um projeto está associada ao ramo `master` do repositório de projeto.

Também é possível fazer uma variante da versão de referência, acrescentando mais fontes, alterando formatos de transcrição e regras de inferência e identificando pessoas e entidades de forma diferente. 

Nesse caso cria-se um novo ramo a partir do principal, ou faz-se uma bifurcação. e altera-se como for necessário.

> Mesmo se a intenção não é fazer uma variante da base de dados com informação diferente do `master`, mas apenas ter uma cópia local ou adicional, é importante que em cada instalação com uma base de dados operacional, exista um ramo do repositório associado. Esse ramo pode ser periodicamente ressincronizado com o ramo `master` de referência.

## Transcritores trabalham sobre repositórios isolados

...... TBD-----

# Conceitos base e enquadramento geral


## Comunidades, fontes e modelos de análise
No `Timelink` tratam-se conjuntos de fontes que correspondem a _comunidades_, em sentido lato. 

Nos casos mais típicos as comunidades são uma localidade, uma paróquia, uma cidade, uma empresa. 

No sentido mais geral a comunidade é um conjunto de pessoas e outras entidades que têm intereações frequentes entre si e por isso deixam nas _fontes históricas_ uma série de registos que podem ser correlacionados e estudados, reconstruindo as _histórias de vida_ e as _redes de relações_ das pessoas e entidades envolvidas.

Um projeto elaborado com `Timelink` envolve a transcrição de fontes histórica em quantidade significativa, seguido do seu processamento para alimentar uma base de dados centrada nas pessoas, os seus atributos, as suas relações e as funções que assumem em diferentes actos ou acontecimentos.

## Transcrição, tradução, importação e identificação/análise

Cada comunidade tratada com a metodologia `Timelink` produz uma série de representações informáticas que correspondem a níveis progressivos de abstração, partindo da informação das fontes até à elaborações de modelos analíticos pelo investigador, como _histórias de vida_, _redes interpessoais_ e outras construções intepretativas.

Essas representações informáticas são as seguintes:

* um conjunto de _transcrições_ de fontes históricas numa linguagem formal chamada `kleio`.
* um conjunto de _traduções_, que são ficheiros produzidos a partir das transcrições e que preparam a informação para importação numa base de dados.
* um conjunto de _identificações_ (pode haver outras coisas derivadas, como grupos ou redes, orecisamos de um termo mais genérico, como _análises_, ou _interpretações_) que são decisões tomadas pelo investigador sobre a co-ocorrência de pessoas, bens e outro tipo de entidades. Ao decidir que diferentes referências em diferentes fontes dizem respeito a uma mesma _entidade_,  o investigador permite a geração de representações derivadas como biografias, redes, etc... que suportam análises complexas da comunidade.

## O processo e os seus produtos

Estas representações informáticas resultam de um _processo_ que vai desde a atividade determinística de _transcrição_ até às decisões complexas, e por vezes ambíguas, da _identificação_. Em cada fase do processo são feitas transformações específicas da informação, utilizando ferramentas que produzem ficheiros com informação progressivamente mais _complexa_ e _menos determinística_ (no sentido em que é progressivamente mais afetada por escolhas e decisões a partir da informação factual). O processo permite definir diferentes _papéis_ e _responsabilidades_, que num projeto pequeno pode ser assumidos sempre pela mesma pessoa, mas que num processo maior podem envolver várias pessoas articuladas.

1. O _transcritor_ regista o conteúdo das fontes segundo um formato pré-determinado que procura captar a informação numa forma próxima do texto original. 
    * As principais decisões que toma são de natureza paleográfica e de compreensão do formato e notação de transcrição. 
    * Em geral os formatos de registo pré-definidos não permitem uma grande variabilidade de resultados. Diferentes _transcritores_ perante a mesma fonte produzem textos idênticos, se não fizerem erros de leitura.
    * O resultado da transcrição são ficheiros com a extensão `cli`. O conjunto dos ficheiros `cli` de um projecto constituti a _base factual_ (as fontes primárias) de um do estudo de uma comunidade.

2. O _tradutor_ gere o processo de tradução das fontes transcritas. 

    * Esta fase é feita por um programa informático que incorpora uma série de decisões prévias sobre a forma de representar a fonte (a sua _estrutura_ ou _formato_) e também um conjunto de _regras de inferência_ de informação implícita na fonte. 
    * As regras de inferência permitem aliviar o trabalho de transcrição ao inferirem atirbutos como o _género_, _estado civil_, assim como _relações de parentesco_ e outras, a partir das funções com que pessoas e outras entidades ocorrem nos actos.
    * Cabe ao _tradutor_ aferir se o formato usado para a transcrição da fonte encapsula o máximo de informação relevante sem custo exagerado de transcrição.
    * Cabe também ao _tradutor_ determinar as regras de inferência aplicáveis a cada tipo de fonte, seguindo o princípio minimalista de não inferir o que pode ser ambíguo ou sujeito a discussão. As regras de inferência visam sobretudo evitar transcrição de informação redudante pelos _transcritores_.
   		 * Por exemplo, num batismo não vale a pena registar o sexo da mãe e do pai, nem a relação de parentesco entre pais e criança batizada - tudo isso pode ser inferido automaticamente).
    * Finalmente o processo de tradução gera identificadores únicos para cada entidade (pessoa, bem, etc.) referida na fonte, identificadores esses que são necessários para a posterior identificação das ocorrências das mesmas entidades nas fontes.
    	* A geração de identificadores é um processo automático mas o _tradutor_ pode definir alguns parâmetros que regulam o processo: quais os elementos da fonte que terão ids gerados automaticamente e quais os que requerem a atribuição de um id pelo _transcritor_ e ainda
    		se os ids num dados ficheiro devem ser prefixados automaticamente com uma sequência de caracteres.
    * O resultado do processo de tradução são diferentes ficheiros, com o mesmo nome que o ficheiro com a transcrião da fonte e com diferentes extensões:
        * `xml`contêm os dados retirados do ficheiro `cli` num formato adequado para importação na base de dados.
        * `rpt` contêm relatórios de tradução para deteção de erros ou situações que necessitam cuidado(_warnings_).
        * `err` contém o número de erros e avisos gerados pela tradução
        * `cli` o ficheiro `cli` original é regravado com uma formatação estruturada para melhor legibilidade e com os identificadores únicos de cada entidade referida incluídos sempre que necessário para que futuras re-traduções e importações não invalidem identificações feitas com base nos identificadores gerados na tradução.
    * Adicionalmente, o resultado de uma tradução é determinado por dois tipos de ficheiros  que controlam o comportamento do tradutor e que tipicamente são os mesmos em todas as transcrições de um projeto.
        * O ficheiro de extensão `str` (normalmente `gacto2.str`) que define o formato de transcrição da fonte (que tipo de actos, qual a informação associada a cada um e que tipo de actores participam, com que funções).
        * O ficheiro `inferences.pl`com as regras de inferência da informação implícita na transcrição.
    * Assim, o resultado final da tradução das fontes é dado pelo conjunto dos ficheiros `.cli`, `.rpt`, `.err`, `.xml` e pelos ficheiros `gacto2.str` e `inferences.pl`.

3. O `importador` incorpora o resultado da tradução numa base de dados que vai permitir a identificação das pessoas. 
    * A base de dados permite navegar de forma eficaz os dados contidos nos ficheiros `xml` gerados pelo _tradutor_. 
    * É importante entender que no `Timelink`a informação importada é imutável. Não existe modo através do interface da base de dados de alterar os dados importados. 
    * Quando um erro é detectado na base de dados a correção tem de ser feita na transcrição original, que é re-traduzida e reimportada. Este princípio garante a transparência da informação usada no projeto e a sua acessibilidade na forma de transcrição de fonte.
    * Assim a fase de importação não adiciona informação à fase anterior. Apenas a transforma num formato mais acessível.
    * Esta fase pode ser representada por uma exportação em linguagem `sql` do conteúdo da base de dados e pelos ficheiros `.xrpt` com o relatório de importação e `.xerr`com o número de erros detectados no processo de importação.

4. O `identificador` (ou o _analista_, porque pode gerar também redes e grupos) toma decisões sobre quem é quem na informação recolhida e pode gerar entidades derivadas como redes e grupos. 
    * Na sua essência o processo de identificação regista decisões do tipo:  a pessoa X que ocorre no acto A é a mesma que a pessoa Y que ocorre no acto B. Além de pessoas é possível identificar outro tipos de entidades, como terras, objetos, documentos (numa investigação concreta as ações de uma companhia).
    * Essas decisões são registadas em tabelas específicas na base de dados e podem ser exportadas no formato `json` que facilita a troca com outras aplicações.
    * Como as identificações são feitas na base de dados elas também são incluídas em ficheiro de exportação da base de dados em formato `sql`.







