# Analise-Dados-INEP
Análise de dados INEP ENAD, negros (Pretos e Pardos) ingressantes a faculdades públicas no BRASIL.

## Equipamento utilizado:
- Nome do Sistema Operacional: Microsoft Windows 7 Professional;
- Versão: 6.1.7601 Service Pack 1 Compilação 7601;
- Tipo do sistema: x64-based PC;
- Processador: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz, 2501 Mhz, 2 Núcleo(s), 4 Processador(es) Lógico(s);
- Memória Física (RAM) Instalada: 4,00 GB;
- Memória física total: 3,87 GB.

## Dependências para a execução da análise e apresentação das informações:
- Python:
  - Versão: python-3.7.4-amd64;
  - Download: [Link download Pyton](https://www.python.org/downloads/);
  - Instalação:
   - Na instalação, habilite a opção (**pip**) **Figura - 1**, pacote que permitirá a instalação de pacotes e suas dependências via prompt, e, habilite a opção **Add python to environment variables** **Figura - 2**, para que os comandos do Python sejam executar em qualquer diretório via prompt.
  
  ![Imagem de habilitar o PIP](/imagens/python_pip.png "Figura - 1")
  
  ![Imagem de habilitar o PATH](/imagens/python_environment.PNG "Figura - 2")
 
  -	Atualização pip:
   - Abra o prompt de comando:
    - Pressione **Tecla Windows + R**, **Figura - 3**;

 ![Imagem teclado](/imagens/teclado.PNG "Figura - 3")
 
   - Digite (**cmd**) e pressione enter, **Figura - 4**;
  
 ![Imagem janela executar](/imagens/executar.PNG "Figura - 4")
 
   - Digite o comando (**pip install --upgrade pip**) e pressione enter, aguarde a atualização, **Figura - 5**.
    
 ![Imagem cmd upgrade PIP](/imagens/cmd_upgrade_pip.PNG "Figura - 5")
 
  -	Instalação das bibliotecas e dependências:
    - Abra o prompt de comando:
     - Pressione Tecla **Windows + R**, **Figura - 6**;
    
 ![Imagem teclado](/imagens/teclado.PNG "Figura - 6")
 
   - Digite (**cmd**) e pressione enter, **Figura - 7**;
    
 ![Imagem janela executar](/imagens/executar.PNG "Figura - 7")
 
   - Digite o comando <pip install requests beautifulsoup4 spotipy pdfminer3k selenium twitter wbdata pandas matplotlib lxml tweepy uber-rides xlrd PyPDF2 pytrends seaborn numpy ipython jupyter twitter-scraper markovify folium> e pressione enter, aguarde a instalação dos pacotes, **Figura - 8**.
  
 ![Imagem cmd PIP instalação dependências](/imagens/cmd_install_dependencias.PNG "Figura - 8")

  - Preparação do ambiente para análise dos dados:
    - Crie um diretório, selecione o local que desejar. Neste trabalho utilizado o diretório (**C:\Analise-Dados-INEP>**);
    - Baixe os arquivos ‘.CSV’ para análise. Arquivos estão disponíveis em:
     - [Link download Dados](https://drive.google.com/file/d/1IOG8BEshJLGOQG2Eg84v8UMPeSATbiJ4/view?usp=sharing)
     - Neste trabalho serão analisados os anos de 2009 há 2013.
    - Extraia os arquivos dentro do diretório (**C:\Analise-Dados-INEP\Dados\**), **Figura - 9**;
  
  ![Imagem cmd dir Dados](/imagens/cmd_dir_dados.PNG "Figura - 9")


  - Executar Jupyter Notebook:
    - Abra o prompt de comando:
     - Pressione Tecla **Windows + R**, **Figura - 10**;
    
 ![Imagem teclado](/imagens/teclado.PNG "Figura - 10")
 
   - Digite (**cmd**) e pressione enter, **Figura - 11**;
    
 ![Imagem janela executar](/imagens/executar.PNG "Figura - 11")
 
   - Acesse o diretório (**C:\Analise-Dados-INEP\**), digite o comando (**cd C:\Analise-Dados-INEP>**) e pressione enter, **Figura - 12**;
  
 ![Imagem cmd cd Diretório execução Jupyter](/imagens/cmd_cd_Analise-Dados-INEP.PNG "Figura - 12")
 
   - Digite o comando (**jupyter notebook**), será executado em servidor de web com os recursos para a realização das análises, aguarde a execução do servidor e não feche o cmd, abrirá a janela do navegador padrão com o serviço Jupyter Notebook, **Figura - 13**.
 
![Imagem cmd run Jupyter Notebook](/imagens/cmd_run_Jupyter-Notebook.PNG "Figura - 13")

```
Obs. Caso não abra o navegador padrão com o acesso ao Jupyter Notebook,
copie e cole no navegador padrão e URL e de acesso, **Figura - 14**:
```

 ![Imagem copiar URL](/imagens/cmd_cp_URL.PNG "Figura - 14")
 
```
No computador gerou a URL “http://localhost:8888/?token=b0440a6dff3b806f3592b58797390fabdf6d1dddf645c957”,
copie a URL gerada e cole no navegador padrão e pressione enter que abrirá os recursos do Jupyter Notebook, **Figura - 15**:
```

 ![Imagem Browser - Pagina Inicial Jupyter](/imagens/browser_home-Jupyter.png "Figura - 15")
 
  - Iniciar a análise de dados:
    - Clique em (**New\Python 3**), **Figura - 16**:
  
 ![Imagem Browser - Novo arquivo Python 3](/imagens/browser_new-Python-3.png "Figura - 16")
 
   - Na nova janela que abrira renomeie o arquivo para o nome desejado, neste trabalho utilizado o nome “**data-analyst-INEP-ENADE-2009TO2013**”, **Figura - 17**:
  
 ![Imagem Browser - Renomear arquivo](/imagens/browser_rename-Project.png "Figura - 17")
 
   - Inserir as células e executá-las, para adicionar pressione o botão (**+**) e para executar pressione o botão (**>| Run**), da paleta de comandos, **Figura - 18**:
  
 ![Imagem Browser - Comandos](/imagens/browser_add-run.PNG "Figura - 18")
 
   - Import das bibliotecas:
  
```python
#import das bibliotecas necessárias para o desenvolvimento do EP
import pandas as pd
import matplotlib.pyplot as plt
```
 ![Imagem Browser - Input Import](/imagens/browser_input-import.PNG "Figura - 19")

```
Atenção: Caso apareça um asterisco entre colchetes, significa que o comando está em execução,
caso seja representado numericamente, significa que o comando foi executado, caso apareça em branco,
significa que os comandos contidos na célula não foram executados.
```

   - Configurações iniciais:
  
```python
#configurações iniciais
low_memory=False
pd.options.display.max_columns = 80
pd.options.display.max_rows = 90
```

![Imagem Browser - Input Configurações Iniciais](/imagens/browser_input-config-iniciais.png "Figura - 20")


   - Declaração das variáveis:
  
```python
#declaração variáveis
d = './Dados/'
pN = 'DM_ALUNO_' 
anos = ['2009', '2010', '2011', '2012', '2013'] 
e = '.CSV'
dados = []
dadosFe = []
dadosEs = []
dadosMu = []
```

![Imagem Browser - Input Declaração Variáveis](/imagens/browser_input-variaveis.png "Figura - 21")
 
 
   - Criação do Data Frame e Leitura dos arquivos, quantificando os dados e armazenando-os em suas respectivas listas:
  
```python
#criação do Data Frame e Leitura dos arquivos, contando os dados e armazená-los nas respectivas listas
for ano in anos:
    df = pd.read_csv(d+pN+ano+e, usecols=['CO_COR_RACA_ALUNO', 'CO_CATEGORIA_ADMINISTRATIVA'], delimiter = '|', encoding = 'iso-8859-1')
    #contabilização e consolidação das informações - Geral
    dados.append(df.query('(CO_COR_RACA_ALUNO == 2 or CO_COR_RACA_ALUNO == 3) and (CO_CATEGORIA_ADMINISTRATIVA == 1 | CO_CATEGORIA_ADMINISTRATIVA == 2 | CO_CATEGORIA_ADMINISTRATIVA == 3)')['CO_COR_RACA_ALUNO'].count()) 
    #contabilização e consolidação das inforamções - Federal
    dadosFe.append(df.query('(CO_COR_RACA_ALUNO == 2 or CO_COR_RACA_ALUNO == 3) and (CO_CATEGORIA_ADMINISTRATIVA == 1)')['CO_COR_RACA_ALUNO'].count()) 
    #contabilização e consolidação das informações - Estadual
    dadosEs.append(df.query('(CO_COR_RACA_ALUNO == 2 or CO_COR_RACA_ALUNO == 3) and (CO_CATEGORIA_ADMINISTRATIVA == 2)')['CO_COR_RACA_ALUNO'].count()) 
    #contabilização e consolidação das informações - Municipal
    dadosMu.append(df.query('(CO_COR_RACA_ALUNO == 2 or CO_COR_RACA_ALUNO == 3) and (CO_CATEGORIA_ADMINISTRATIVA == 3)')['CO_COR_RACA_ALUNO'].count())
```


 ![Imagem Browser - Input Data Frame](/imagens/browser_input-dataframe.png "Figura - 22")
 

  - Plotar dados sintéticos obtidos no gráfico:
  
```python
#plotar dados gráfico
fig, ax = plt.subplots()
plt.rcParams['figure.figsize'] = (10,8)
ax.plot(anos, dados, label='Total')
ax.plot(anos, dadosFe, label='Federal')
ax.plot(anos, dadosEs, label='Estadual')
ax.plot(anos, dadosMu, label='Municipal')
ax.grid()
plt.legend()
plt.title('Evolução: Negros (Pretos e Pardos) ingressantes em Universidades Públicas')
plt.xlabel('Anos')
plt.ylabel('Quantidade')
plt.show()
```


 ![Imagem Browser - Input Plotar Grafico](/imagens/browser_input-plotargraficos.png "Figura - 23")
 
 ![Imagem Browser - Plotar Grafico](/imagens/browser_graficos.png "Figura - 24")
 
 
   - Consolidação dos resultados:
  
```python
#organização dos dados em tabelas, para melhor visualização dos dados
consolidacao = {}
for x in range(5):    
    consolidacao.update({anos[x]: [dadosFe[x], dadosEs[x], dadosMu[x], dados[x]],})
df_DC = pd.DataFrame(consolidacao, columns=anos, index=['Federal','Estadual','Municipal','Total'])
df_DC
```

 ![Imagem Browser - Input e Tabela Resultados](/imagens/browser_input-tabela_resultados.png "Figura - 25")

