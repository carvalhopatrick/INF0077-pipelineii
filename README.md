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

...

