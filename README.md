# Projeto INF-0077


## Instalação
### Passo 0 - Ferramentas
- Instalar o miniconda para ter um ambiente Python
- https://docs.conda.io/projects/miniconda/en/latest/
- Versão utilizada: Latest - Conda 23.10.0 Python 3.11.5 released November 16, 2023

### Passo 1 - Criação do Ambiente
- Montar um ambiente para o projeto (apesar do Conda usar por padrão o 3.11, usamos o Python 3.9 no nosso ambiente para evitar problemas de dependências nas bibliotecas de ML)
`conda create --name="mlops-pipelineii" python=3.9`

### Passo 2 - Instalação módulos/libs
- Ative o ambiente
`conda activate mlops-pipelineii`

Módulos necessários:
 - *tensorflow*  (vai instalar uma penca de dependências -> 300 MB !!!)
 - *pillow* (PIL image)
 - *scipy*  (? > 50 Mb)

O projeto conta com um `requirements.txt` com uma versão congelada de todas as dependências utilizadas na criação do repo;

Opção 1 - Instalar dependências com última versão disponível no pip :
 `pip install tensorflow pillow scipy`
Opção 2 - Usar requirements:
 `pip install -r requirements.txt`
 
 Pronto, já podemos rodar o script principal. Próximo passo: obter o dataset.
 
### Passo 3 - Dataset
Por padrão o dataset não fica salvo no repositório Github, apenas links.

#### Instalação do gerenciador
`pip install dvc`

#### Criação do ambiente
`dvc init`
`dvc remote add -d DS-gdrive gdrive://<<folder_id>>`

#### Extração e versionamento do DS
- Descompactar o zip com o dataset pasta `ds`
- Impedir o versionamento do DS pelo git:
`echo "/ds" >> .gitignore`
- Adicionar a pasta `ds` para gerenciamento do DVC
`dvc add .\ds\`
- Adicionar o arquivo de configuração do ds no git
`git add ds.dvc`
- Versionar DS
- `dvc push` 


### T2
### Passo 1 - criação do dvc.yaml e params.yaml
- Instalar as dependencias `pip install -r requirements.txt` apresentadas na monitória
- Associar o DVC.yaml com o params.yaml por meio do **_params:- params.yaml_**
- Adicionar `/model.keras` no .gitignore
- Modificar o model.py e incluir o módulo Live() e callback
- Executar o model.py para criar um modelo "model.keras" e o diretório dvclive com as métricas de avaliação; Loss e acurácia

### Passo 2 - Experimento e DVC
- Executar o comando `dvc exp run --name v_0` para noemar o experimento como "v_0" e rodar o experimento
- Executar os comandos `git push origin main`, `dvc push` e `dvc exp push origin v0`
- Adicionar o projeto do Github no https://studio.iterative.ai/ para 

### Passo 3 - Criando um pipeline
- Criar um diretório `.gihub/workflows` e criar um arquivo `pipeline.yaml` para criar o pipeline com todas as configurações e atualizações
- o pipeline vai executar todas as vezes que ocorrer um `push`
