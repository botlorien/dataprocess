# dataprocess

**dataprocess** é um pacote Python que oferece utilitários simples e eficientes para o processamento e a limpeza de dados.

## Recursos

- **Processamento de dados**: Transforme dados utilizando funções dedicadas.
- **Limpeza de dados**: Remova valores nulos e prepare dados para análise.
- Estrutura modular para fácil extensão.

## Instalação

Instale o pacote diretamente do repositório GitHub:

```bash
pip install etl-dataprocess
```
ou
``` bash
git clone https://github.com/botlorien/dataprocess.git
cd dataprocess
pip install .
```

## Exemplo de uso

```python
from dataprocess import dataprocessing as hd


if __name__ == '__main__':

    def process_something_here():
        """Only a single example to use dataprocess"""
        # handle importation files verifying if .xlsx, .csv, .xls, .json, .txt
        # and returning its content as 'DataFrame' to (.xlsx, .csv, .xls), 'dict' to (.json) and 'str' to .txt
        # if only the directory folder was passed as argument it get the first file in that folder
        table = hd.import_file(PATH_DOWNLOADS)

        # clear all table removing white spaces and another trashes
        # and return a 'DataFrame' with all columns astype('str')
        table = hd.clear_table(table)

        # Now after the cleaning convert the columns to the apropriate types
        # it accepts a mapping argument "dtypes" to list columns to be cast to
        # 'datetime' and 'time'. Another common types as 'int', 'float' and 'str' are
        # handled automatically analysing its values.
        dtype = {
            'datetime':[
                'date_name_column' # replace it with the name of the column to be cast do 'datetime'
            ],
            'time':[
                'hour_and_minute_name_column' # replace it with the name of the column to be cast do 'time'
            ]
        }
        table = hd.convert_table_types(
            table,
            dtypes=dtype
        )
        print(table)
        print(table.info())
        return table

    process_something_here()
```
