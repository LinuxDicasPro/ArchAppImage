<p align="center">
  <img src="logo.png" width="256">
</p>

<h1 align="center">ArchAppImage</h1>

<h3 align="center">
  Empacotador de AppImage Baseado no Projeto ArchImage (não é fork) que usa o
  Conteiner Junest para criar AppImage a partir de pacotes do Arch Linux.

</h3>

---

## 📜 Descrição

O **ArchAppImage** facilita o empacotamento de programas no no formato **AppImage** usando pacotes 
do Arch Linux. Ele automatiza a criação de pacotes e melhora a compatibilidade com o sistema, além
de contar com vários métodos de criação de AppImage e inclusão do **GLibC**.

## 🎯 Objetivo

O objetivo do **ArchAppImage** é oferecer uma solução simplificada para simplificar a criação de 
**AppImage** via Conteiner em qualquer sistema, reduzindo a complexidade do processo e
garantindo maior compatibilidade entre vários sistemas Linux.

## 💡 Motivação

- O formato **AppImage** permite rodar aplicativos de forma portátil sem necessidade de instalação.
No entanto, a criação de AppImage pode ser trabalhosa. O método convencional de empacotamento,
pode exigir muitos testes em várias distros **Linux** para garantir o máximo de compatibilidade possível.
Portanto, é muito difícil garantir que o AppImage vai funcionar na maioria das distros. 
- Para cobrir o problema de compatibilidade com o **GLibC**, o mais recomendado é a adição do 
próprio recurso ao AppImage, pois assim é possível usar o **ld-linux** para abrir os programas.
- O projeto **ArchImage** é uma excelente ferramenta de criação de AppImage. Mas, segundo meus testes,
o desempenho e o modo como ele funcionava, não era satisfatório e as vezes precisava esperar muito
tempo para saber se o empacotamento funcionou. Eu decidi que eu queria uma solução extremamente rápida
para saber se realmente deu certo ou não as configurações antes de empacotar o AppImage.
- A ideia de empacotar por **Conteiner** funciona bem, mas nem todos os programas precisam ser
empacotados como conteiner, então é necessário um modo de empacotamento que criasse o AppImage, sem
precisar de conteiner. Soluções como bwrap, podem falhar em sistemas com restrições de **namespaces**
e não funcionarão. Uma solução é o proot, que é um pouco mais lento para iniciar o programa no
conteiner, mas totalmente funcional. 
- Trabalhar com AppImage, também é uma forma de entender como o **Sistema Linux** funciona.

## 🚀 Características e Recursos

- O Projeto conta com uma interface de linha de comando para a configuração mais básica. Os ajustes
mais refinados devem ser feitos no script de construção normalmente conforme a necessidade.
- Um script de contrução até o momento: **APP-ArchAppImage**.
- São quatro tipos de **AppRun** até o momento: **Padrão**, **Junest**, **bwrap**, **proot**. 
- Não há a necessidade de separar os projetos em diretórios.
- Pode ser usado o mesmo conteiner para empacotar vários AppImages diferentes,
economizando espaço em disco.
- Também pode-se usar um conteiner sepadado para: **mutilib**, **ChaoticAUR**, **ArchLinuxCN** e **AUR**.
- Se for preciso, pode ser criado um conteiner só para uma aplicação específica da mesma forma que
 no **ArchImage** e escolher se vai ter **mutilib**, **ChaoticAUR**, **ArchLinuxCN** ou **AUR**.
- Possui resolução automática de dependências, podendo ser ajustado usando diferentes níveis de busca
por dependências.
- Em programas binários, pode ser habilitado uma busca por dlls, que pode ajudar a executar o
programa usando menos níveis de busca por dependências, o que pode reduzir o tamanho do AppImage.
- Você pode ativar a autointegração na área de trabalho e a autointegração de autoinicialização
durante a execução do AppImage.
- Possui uma forma alternativa para configurar a detecção correta do idioma de forma definitiva em
caso de programas que não detectam o idioma de imediato.
- O método padrão conta com um método automático para resolver o cache do gdk-pixbuf2 para 
programas que usam gtk.

## 🛠️ Instalação

Não há a necessidade de instalação, basta clonar o repositório e, se quiser, colocar em
algum local no sistema e linkar no `/bin` ou em algum local para ser adicionado na
variável `PATH`.

```bash
$ git clone https://github.com/LinuxDicasPro/ArchAppImage.git
$ cd ArchAppImage
$ sudo ln -s ArchAppImageGen /usr/bin/ArchAppImageGen
```

## 🎮 Utilização Básica

1. A primeira coisa que você vai fazer, é abrir o utilitário via terminal:
   ```bash
   $ ArchAppImageGen
   ```
   Isso vai abrir uma ferramenta de configuração do script de construção do AppImage, que você
   pode configurar o local padrão do projeto pressionando `C` ou `Enter` para iniciar a configuração.
   Após a configuração, o script de construção será salvo no diretório padrão `~/ArchAppImage` ou no
   local que você configurou.

2. Depois você vai até o script gerado para a construção do AppImage no diretório do projeto que
   foi configurado, faça os ajustes e execute o script para criar o AppImage:
   ```bash
   $ cd ~/ArchAppImage
   $ kate package-ArchAppImage  # Faça os ajustes com o editor de sua preferência.
   $ ./package-ArchAppImage
   ```
   Se tudo der certo e o script já estiver configurado corretamente, o AppImage será criado.


## 📖 Documentação

Para mais detalhes sobre o uso e as funcionalidades do **ArchAppImage**,
consulte a documentação oficial:

📄 [Documentação Completa](https://github.com/LinuxDicasPro/ArchAppImage/wiki) ( Ainda não Escrito )

## 📷 Capturas de Tela

<p align="center">
  <img src="preview/1.png">  
  <img src="preview/2.png">
  <img src="preview/3.png">
</p>

## 📝 Próximas Implementações

- Suporte a **NVidia** no modo de Conteiner.
- Mais scripts alternativos de empacotamento.
- Ferramentas extras.
- Possível implementação com debootstrap.

## 🤝 Contribuindo

Contribuições são sempre **Bem-Vindas!** Se você deseja ajudar a melhorar este projeto,
siga as diretrizes abaixo para garantir um fluxo organizado e eficiente.

### 📌 Como contribuir

1. **Faça um fork do repositório**  
   - Clique no botão **"Fork"** para criar uma cópia do **ArchAppImage** na sua conta.

2. **Clone o repositório**  
   - No seu terminal, execute:
     ```bash
     git clone https://github.com/<seu-repositorio>/ArchAppImage.git
     cd ArchAppImage
     ```

3. **Crie um branch para sua modificação**  
   - Escolha um nome descritivo para o branch:
     ```bash
     git checkout -b my-contrib
     ```

4. **Faça as alterações e commit**  
   - Após editar os arquivos necessários, adicione suas mudanças:
     ```bash
     git add .
     git commit -m "description my contrib"
     ```

5. **Envie para o repositório remoto**  
   - Envie seu branch para o seu fork no GitHub:
     ```bash
     git push origin my-contrib
     ```

6. **Crie um Pull Request (PR)**  
   - Acesse o repositório original no GitHub e clique em **"New Pull Request"**.
   - Escolha o branch do seu fork e descreva suas alterações de forma clara.

### 📢 Dicas para um Pull Request bem-sucedido

✔️ **Explique suas mudanças:** Escreva um título e uma descrição detalhada do que foi alterado e por quê.  
✔️ **Siga o padrão do código:** Mantenha a consistência do projeto.  
✔️ **Faça commits pequenos e organizados:** Isso facilita a revisão.  
✔️ **Revise seu código antes de enviar:** Evite bugs e erros desnecessários.  

Agradecemos sua contribuição! 🚀✨

## 📜 Licença

Este projeto é distribuído sob os termos da **GNU General Public License version 3**.

Para mais detalhes sobre a licença, consulte o arquivo [LICENSE](LICENSE) ou acesse 
o texto completo da licença no site da Free Software Foundation:

🔗 https://www.gnu.org/licenses/gpl-3.0.html

## 📩 Contato

- 📧 Email: contatolinuxdicaspro@gmail.com
- 💬 **Telegram:** [LinuxDicasPro](https://t.me/LinuxDicasPro)  
- ▶️ **YouTube:** [LinuxDicasPro](https://www.youtube.com/@LinuxDicasPro)  
- 👥 **Reddit:** [r/LinuxDicasPro](https://www.reddit.com/r/LinuxDicasPro/)


