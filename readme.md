
# ChatFebracis

#### Aluno: [Emerson Cerbino Doblas](https://github.com/emersondoblas/ChatFebracis)
#### Orientador: [Leonardo Forero Mendoza]

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

---

### Resumo

A Febracis é a maior escola de negócios da américa latina e fornece treinamentos de desenvolvimento humano e treinamentos empresariais. 
O método Cis é um dos treinamentos que a empresa oferece e também é o maior treinamento de inteligência emocional do mundo. É um treinamento que transforma a vida das pessoas em todas as áreas em tempo recorde. 

O desafio enfrentado pela empresa está relacionado ao tempo que um consultor comercial gasta para tirar as dúvidas do cliente, explicando o que é a empresa e o método. A empresa considera a venda desse curso como uma venda complexa, onde o cliente tem dificuldade de tangibilizar qual é o tipo de  melhora que ele terá em sua vida. 

A atividade proposta é um chat treinado para explicar ao cliente o que é o método, como funciona, quais são os ganhos e o todos os benefícios que ele oferece, além de saber explicar também sobre a Febracis. Assim, o primeiro atendimento é feito por um Chat com Inteligência Artificial. Além disso, esse chat pode ser usado internamente para treinar os novos consultores comerciais sobre o que é o Método que eles irão vender.



### Abstract 


Febracis is the largest business school in Latin America and provides both human development training and corporate training. 
The CIS Method is one of the trainings the company offers, and it is also the largest emotional intelligence training program in the world. It is a program that transforms people’s lives in every area in record time. 

The challenge faced by the company is related to the amount of time a sales consultant spends answering customer questions, explaining what the company and the method are. The company considers the sale of this course to be a complex sale, where the customer has difficulty grasping what kind of improvement they will actually experience in their life. 

The proposed activity is a trained chat designed to explain to the customer what the method is, how it works, what the gains are, and all the benefits it offers, as well as to explain about Febracis itself. Thus, the first service is provided by an Artificial Intelligence Chat. In addition, this chat can also be used internally to train new sales consultants about the Method they will be selling.



### 1. Introdução

A Febracis é a maior escola de negócios e de desenvolvimento humano da América Latina, fundada por Paulo Vieira, um dos maiores nomes do coaching e da inteligência emocional no mundo. Com atuação nacional e internacional, a instituição oferece treinamentos que unem ciência aplicada, ferramentas práticas e metodologia exclusiva, impactando milhões de pessoas e empresas ao redor do mundo.

O propósito da Febracis é promover transformação integral — pessoal, profissional e empresarial — ajudando indivíduos e organizações a alcançarem níveis extraordinários de desempenho, resultados financeiros e qualidade de vida.

Além dos treinamentos voltados ao desenvolvimento humano, a Febracis também é referência em consultoria e educação corporativa, apoiando líderes, empresários e gestores na construção de negócios mais lucrativos, sustentáveis e bem estruturados.

O Método CIS (Coaching Integral Sistêmico) é o maior treinamento de inteligência emocional do mundo. Criado por Paulo Vieira, o programa já impactou milhões de pessoas em mais de 70 países.

O treinamento é estruturado para gerar mudanças profundas e rápidas em todas as áreas da vida — relacionamentos, carreira, finanças, saúde e espiritualidade. Em apenas três dias intensos, os participantes aprendem a:

Desenvolver autoconsciência e controle emocional;

Quebrar padrões limitantes que impedem o crescimento;

Potencializar habilidades e competências para atingir metas;

Alinhar propósito de vida e alta performance;

Melhorar relacionamentos pessoais e profissionais.

O CIS é reconhecido por sua eficácia em tempo recorde, pois utiliza técnicas de coaching, psicologia positiva, neurociência e inteligência emocional aplicadas de forma prática e vivencial.



### 2. Modelagem

As informações utilizadas para treinar o chat foram extraídas de documentos oficiais da empresa, como apostilas, manuais, apresentações e panfletos digitais. Esses documentos foram compilados e unificados em apenas 2 arquivos. Um para Febracis e outro para Método CIS. E para isso, empregou-se a biblioteca PyMuPDF, responsável pela leitura de arquivos PDF. Após a extração, os textos foram divididos em trechos menores (chunks), garantindo que o sistema conseguisse recuperar apenas as partes mais relevantes de acordo com a pergunta. Cada trecho foi convertido em uma representação numérica (embedding) com o OpenAI Embeddings, possibilitando a comparação semântica entre perguntas e documentos. Os vetores foram armazenados em um banco vetorial, que permite localizar rapidamente os trechos mais próximos da pergunta do usuário. Duas bibliotecas foram testadas: FAISS e ChromaDB.Quando o usuário faz uma pergunta, o sistema busca os trechos mais relevantes no banco vetorial e os insere no prompt enviado ao modelo de linguagem (LLM)

Foram testadas diferentes configurações de temperatura, parâmetro que controla o nível de criatividade do modelo. Valores mais baixos (0–0,3) resultaram em respostas mais objetivas, enquanto valores mais altos (0,7–1,0) produziram explicações mais detalhadas e criativas. 

No modelo foram usadas algumas bibliotecas como a openai, faiss, numpy, langchain, PyMuPDF, pdfplumber, chromadb, para buscar um modelo de chat eficiente, além de indexador "embedding" e sistema com RAG (Retrieval-Augmented Generation) + LLM (Large Language Model) para uma melhor explicação do chat. 



### 3. Resultados

A implementação do modelo de chat inteligente apresentou resultados satisfatórios tanto no aspecto técnico quanto no impacto prático para a empresa. Do ponto de vista funcional, o sistema mostrou-se capaz de: Responder corretamente às perguntas mais frequentes sobre a Febracis e o Método CIS, utilizando exclusivamente informações provenientes dos documentos oficiais da instituição; Manter consistência nas respostas, evitando variações de linguagem entre diferentes interações e alinhando a comunicação com o discurso institucional da empresa; Reduzir o tempo de resposta em comparação ao atendimento humano inicial, fornecendo esclarecimentos imediatos ao cliente.

Durante os testes, foram avaliadas diferentes configurações de parâmetros do modelo. Observou-se que:
Com temperatura baixa (0–0,3), as respostas se mantiveram mais objetivas e próximas ao material original, sendo mais adequadas para dúvidas factuais, como definições ou informações históricas; Com temperatura intermediária (0,5–0,7), o chat produziu respostas completas e didáticas, equilibrando clareza e detalhamento; Com temperatura alta (0,8–1,0), o modelo apresentou maior criatividade na forma de explicar, útil em contextos mais motivacionais, mas com risco de se afastar do texto original.

A precisão na recuperação de documentos também se mostrou consistente. Ao variar o número de trechos recuperados (parâmetro k), identificou-se que valores entre 3 e 5 forneceram melhor equilíbrio entre contexto suficiente e foco na resposta. 

Do ponto de vista organizacional, o sistema apresentou duas contribuições principais: Apoio ao cliente, pois o chat se mostrou eficaz como primeiro ponto de contato, reduzindo a necessidade de o consultor comercial gastar tempo explicando informações básicas sobre a Febracis e o Método CIS e capacitação interna, pois o modelo foi validado como ferramenta de treinamento para novos colaboradores, garantindo que todos tenham acesso a informações padronizadas e confiáveis desde o início.

Em síntese, os resultados demonstram que a utilização de um modelo baseado em RAG (Retrieval-Augmented Generation) com LLM (Large Language Model) é viável e eficaz no contexto da Febracis. O sistema contribui para a padronização da comunicação, o ganho de eficiência no atendimento e a aceleração do processo de integração de novos consultores.



### 4. Conclusões

O presente trabalho teve como objetivo desenvolver um chat inteligente capaz de explicar de forma clara e padronizada o que é a Febracis e o Método CIS, reduzindo o tempo de atendimento inicial dos consultores comerciais e, ao mesmo tempo, servindo como ferramenta de capacitação para novos colaboradores.

A partir do uso de documentos oficiais da empresa como base de conhecimento e da aplicação de técnicas de processamento de linguagem natural aliadas a modelos de linguagem de última geração, foi possível construir um sistema que integra extração de dados, organização de informações e geração de respostas contextualizadas.

Os resultados demonstraram que o modelo atendeu aos objetivos propostos, oferecendo: Respostas consistentes e alinhadas com o discurso institucional da empresa; Rapidez e eficiência no primeiro contato com o cliente; Utilidade como ferramenta de treinamento interno, padronizando a forma como o Método CIS é apresentado.

Além disso, a aplicação prática mostrou que tecnologias como RAG (Retrieval-Augmented Generation) e LLMs (Large Language Models) podem ser adaptadas com sucesso para contextos empresariais, desde que se utilizem dados internos confiáveis e parâmetros ajustados de acordo com a finalidade.

Como perspectivas futuras, destaca-se a possibilidade de: Ampliar a base de conhecimento com novos materiais e atualizações constantes; Incorporar recursos multimodais (imagens, vídeos e áudios) para enriquecer a experiência do usuário; Integrar o chat diretamente aos canais de atendimento da empresa, como WhatsApp e site institucional, aumentando o alcance e a usabilidade da solução.

Em síntese, o trabalho evidencia como a união entre inteligência artificial e gestão empresarial pode gerar valor, otimizando processos, fortalecendo a comunicação e contribuindo para que a Febracis mantenha sua posição de referência em desenvolvimento humano e de negócios na América Latina.

---



Matrícula: 231.101.084

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*




