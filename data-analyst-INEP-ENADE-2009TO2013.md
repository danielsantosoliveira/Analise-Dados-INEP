```python
''' @author: Daniel
    Análise de dados INEP/ENAD: Evolução dos negros (Pretos e Pardos) ingressantes em Universidades Públicas do Brasil;
    Anos de referência: 2009 até 2013;
    Dados extraídos do site:
    http://portal.inep.gov.br/microdados #ENADE
'''
```


```python
#import das bibliotecas necessárias para o desenvolvimento do EP
import pandas as pd
import matplotlib.pyplot as plt
```


```python
#configurações iniciais
low_memory=False
pd.options.display.max_columns = 80
pd.options.display.max_rows = 90
```


```python
#declaração variáveis
d = './Dados/'
pN = 'DM_ALUNO_' 
anos = ['2009', '2010', '2011', '2012', '2013'] 
e = '.CSV'
dm = 'DM.CSV'
dados = []
dadosFe = []
dadosEs = []
dadosMu = []
```


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


![png](output_5_0.png)



```python
#organização dos dados em tabelas, para melhor visualização dos dados
consolidacao = {
'2009': [dadosFe[0], dadosEs[0], dadosMu[0], dados[0]],
'2010': [dadosFe[1], dadosEs[1], dadosMu[1], dados[1]],
'2011': [dadosFe[2], dadosEs[2], dadosMu[2], dados[2]],
'2012': [dadosFe[3], dadosEs[3], dadosMu[3], dados[3]],
'2013': [dadosFe[4], dadosEs[4], dadosMu[4], dados[4]],
}
df_DC = pd.DataFrame(consolidacao, columns=anos, index=['Federal','Estadual','Municipal','Total'])
df_DC
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>2009</th>
      <th>2010</th>
      <th>2011</th>
      <th>2012</th>
      <th>2013</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Federal</td>
      <td>166132</td>
      <td>202088</td>
      <td>238883</td>
      <td>275255</td>
      <td>328839</td>
    </tr>
    <tr>
      <td>Estadual</td>
      <td>40901</td>
      <td>74408</td>
      <td>91476</td>
      <td>107063</td>
      <td>126693</td>
    </tr>
    <tr>
      <td>Municipal</td>
      <td>5704</td>
      <td>6820</td>
      <td>7608</td>
      <td>6115</td>
      <td>8427</td>
    </tr>
    <tr>
      <td>Total</td>
      <td>212737</td>
      <td>283316</td>
      <td>337967</td>
      <td>388433</td>
      <td>463959</td>
    </tr>
  </tbody>
</table>
</div>


