# Diretório `patches`

O diretório `patches` é destinado a armazenar correções específicas para compatibilidade 
dos programas em **AppImage**. Aqui, você pode adicionar patches que ajustam ou
melhoram funcionalidades relacionadas a:

- **Compatibilidade de idioma**
- **Correção de ícones**
- **Suporte ao `XDG_DATA_DIRS`**
- **Outros ajustes necessários para o funcionamento adequado do AppImage**

## Como organizar?

Os patches devem seguir a seguinte estrutura de nomenclatura:

```
pacote-versão-oquevaicorrigir.path
```

Exemplos:

```
gtk3-3_24_34-iconfix.path
vlc-3_0_18-xdgdatadirs.path
libreoffice-7_5_3-fix_locale.path
```

## Aplicação dos patches

Para aplicar os patches, utilize o comando adequado dependendo do programa:

```bash
patch -p1 < patches/nome-do-patch.path
```

Caso esteja utilizando um gerenciador de pacotes que suporte aplicação automática
de patches, configure para que os arquivos deste diretório sejam considerados no
processo de build.

## Considerações

- Certifique-se de que os patches são compatíveis com a versão do pacote que estão corrigindo.
- Teste cada patch antes de aplicá-lo para evitar problemas inesperados.
- Sempre mantenha uma cópia do pacote original antes da aplicação dos patches para
facilitar a reversão, se necessário.

Este diretório facilita a adaptação de programas para serem empacotador em **AppImage** usando
o modo padrão com inclusão do **GLIBC**, sem precisar de modificações diretas no
código-fonte principal. No modo de conteiner, dificilmente será necessário.