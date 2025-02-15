 # Diretório `extra`

O diretório `extra` é destinado a armazenar scripts e utilitários que não estão diretamente
vinculados ao núcleo do projeto, mas que podem ser úteis para tarefas auxiliares. Ou seja,
os scripts inseridos aqui, não fazem diferença para o projeto, a menos que o utilizador
do projeto decisa usá-lo para auxiliar na criação de programas em **AppImage**.



Projetos indiretamente ligados ao projeto principal também podem ser migrados do diretório `third` para cá. Aqui, você pode adicionar scripts para:

- **Automação de tarefas**
- **Geração de relatórios ou logs**
- **Conversão ou manipulação de arquivos**
- **Qualquer outra funcionalidade complementar**

## Como organizar?

Os scripts devem seguir uma estrutura organizada para facilitar a manutenção e o uso:

```
extra/
├── utils/      # Scripts de utilidades gerais
│   ├── limpeza_cache.sh  # Exemplo de script de limpeza
│   ├── gerar_log.py      # Exemplo de script de geração de logs
├── conversores/  # Scripts para conversão de arquivos
│   ├── pdf_para_txt.py  # Conversor de PDF para texto
│   ├── imagem_para_png.sh  # Conversor de imagens
└── automação/   # Scripts de automação
    ├── backup.sh   # Script de backup automático
    ├── deploy.sh   # Script de deploy
```

## Execução dos scripts

Para executar os scripts, utilize os comandos adequados para cada tipo de arquivo. Exemplo:

```sh
# Para um script Shell
bash extra/utils/limpeza_cache.sh

# Para um script Python
python3 extra/utils/gerar_log.py
```

Caso os scripts exijam permissões de execução, utilize:

```sh
chmod +x extra/caminho/do/script.sh
```

## Considerações

- 

Este diretório permite armazenar ferramentas auxiliares não vinculados
diretamente com o projeto principal.


