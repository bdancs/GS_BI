# Global Solution - Business Intelligence e Startup Development

# Vídeo: https://youtu.be/yGcRUTpRwTY?si=WSF6DD1QewXbIrl3

# Integrantes
- Allan Von Ivanov - RM98705
- Arthur Candido de Abreu - RM98283
- Bianca Carvalho Dancs Firsoff - RM551645
- Giuliano Romaneto Marques - RM99694

# Sistema de Monitoramento de Risco de Lixo Espacial com Base no Dataset SpaceX
A aplicação utiliza técnicas de Machine Learning para a catalogação, análise e previsão do risco de colisão de objetos e cargas úteis na órbita baixa da Terra, utilizando dados oficiais extraídos da API da SpaceX.

# Contexto do Problema
O aumento acelerado de satélites comerciais, constelações de comunicação e fragmentos de foguetes antigos em órbita gerou uma crise de tráfego espacial. O acúmulo de detritos (lixo espacial) na Órbita Baixa da Terra (LEO) eleva exponencialmente o risco de colisões.

Como os impactos no espaço ocorrem em velocidades hipersônicas, uma colisão pode desencadear o efeito conhecido como Síndrome de Kessler. Esse fenômeno caracteriza-se por uma reação em cadeia onde uma única colisão gera milhares de novos fragmentos que, por sua vez, destroem outros satélites ativos. As consequências incluem a inviabilização de órbitas inteiras e a interrupção de serviços terrestres essenciais, tais como sistemas de posicionamento global (GPS), telecomunicações, previsão meteorológica e internet.

# Metodologia e Pipeline de Machine Learning
O projeto foi construído sobre um pipeline completo e automatizado de Ciência de Dados estruturado em Python:
- Obtenção e Limpeza de Dados: Requisição HTTP dos payloads da SpaceX com tratamento de valores ausentes e filtragem de objetos sem registros de telemetria.
- Engenharia de Atributos (Feature Engineering): Criação de novas variáveis físicas baseadas nas leis da mecânica orbital:
- Razão de Órbita: Proporção de achatamento calculada entre o Periastro e o Apoastro.
- Velocidade Média Estimada: Deduzida matematicamente através do raio médio (Eixo Semimaior) e do período orbital em minutos.
- Pré-processamento: Aplicação de padronização estatística padrão (StandardScaler) para alinhar a escala de variáveis de ordens de grandeza distintas (ex: Massa em kg vs. Excentricidade decimal).
- Definição da Variável Alvo (Target): Criação da classe preditiva (0 ou 1) que mapeia objetos abandonados (vida útil zerada) situados na zona orbital mais congestionada da Terra (entre 400 km e 1000 km de altitude).

# Modelos Testados e Resultados
Foram aplicadas e comparadas duas técnicas diferentes de Classificação estudadas ao longo do período letivo:

## Random Forest Classifier
- Abordagem: Modelo baseado em comitê (Ensemble por Bagging), gerando múltiplas árvores de decisão em paralelo.
- Características: Alta robustez a outliers e menor propensão ao sobreajuste (overfitting).

## XGBoost Classifier (Extreme Gradient Boosting)
- Abordagem: Modelo baseado em Boosting sequencial, onde cada nova árvore é construída com o objetivo de corrigir os erros residuais das estruturas anteriores.
- Características: Alta eficiência computacional e precisão em dados tabulares estruturados.

# Comparação de Desempenho
Os modelos foram validados utilizando uma base de dados de teste isolada (20% do volume total). O pipeline extrai as métricas de Precisão (Precision), Sensibilidade (Recall) e F1-Score para ambas as técnicas. O modelo XGBoost foi selecionado para a produção devido à sua capacidade superior de ajustar as fronteiras de decisão do tráfego orbital.
