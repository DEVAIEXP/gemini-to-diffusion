# Gemini-To-Diffusion


## Sobre

Este projeto foi desenvolvido para o evento de <b>Imersão Inteligência Artificial 2ª Edição</b> promovido pela Alura em parceria com o Google. O Gemini-to-Diffusion tem por objetivo facilitar a criação de prompts para a geração de imagens em modelos de difusão estável. Basta o usuário perguntar no chat ao Gemini o que deseja gerar na imagem e o Gemini se encarregará de gerar um prompt rebuscado para a inferência em difusão estável. A imagem é gerada em tempo real possibilitando o download em arquivo. Para a geração da imagem, a aplicação enviará o prompt via REST API para um modelo de difusão hospedado na plataforma da <a href=https://huggingface.co/>HuggingFace</a>.

## Notebook Colab da aplicação
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](/notebook/colab-gemini-to-diffusion_pt_br.ipynb)

## Instalação local
Tenha o ambiente Python versão 3.10.* e o Python virtual environment instalado. 

Então execute o seguinte comando no prompt de comando:
```bash
git clone https://github.com/DEVAIEXP/gemini-to-diffusion.git
cd gemini-diffusion
(no linux  ) source install_linux.sh
(no windows) install_windows.bat
```
Alternativamente, caso queira instalar manualmente:
```bash
git clone https://github.com/DEVAIEXP/gemini-to-diffusion.git
cd gemini-diffusion
pip install -r requirements.txt
```

### Parâmetros adicionais para o script de instalação (Opcional):
Assumindo **T** para Verdadeiro e **F** para False:
* Informar T no primeiro parâmetro irá forçar a exclusão do Venv atual gerando uma instalação limpa.
```bash
(no linux  ) source install_linux.sh T
(no windows) install_windows.bat T
````
* Informar F no segundo parâmetro irá desabilitar o Venv durante a instalação. Utilize esta opção se não deseja utilizar seu próprio ambiente virtual.
```bash
(no linux  ) source install_linux.sh F F
(no windows) install_windows.bat F F
````
## Execução local
**Se você executou a instalação sem Venv, você precisará editar os arquivos de script e alterar a variável USE_VENV para o valor 0 antes de iniciar a execução da ferramenta. Para iniciar execute o comando:**

```bash
(for linux  ) source start.sh pt-BR
(for windows) start.bat pt-BR
```

# Parâmetros da interface
## Tab Chat
Nesta guia é onde a conversa com o modelo acontece, os seguintes campos estão disponíveis:

* `Questão`: Neste campo é digitado a pergunta para o modelo Gemini. Para gerar prompts para difusão você deve utilizar sempre o comando /imagine antes da pergunta. Se o comando for omitido o prompt não será gerado e a conversa será tratada como uma conversa de chat com o modelo Gemini.
* `Modelo do chat`: Lista das versões dos modelos 'Gemini' disponíveis.
* `Modelo de imagem`: Lista dos modelos de difusão estável disponíveis para uso na API.
* `Imagem Gerada`: A imagem gerada após a geração do prompt.

### Tab Configurações
Nesta guia os parâmetros para acionamento dos modelos e inferência são informados:

* `Google API Key`: Chave de API do Google AI Studio para utilização dos modelos Gemini. Obtenha sua chave aqui [Google API Key](https://aistudio.google.com/app/apikey/?utm_source=website&utm_medium=referral&utm_campaign=Alura&utm_content=).
* `Huggingface API Key`: Chave de API do Huggingface para utlização dos modelso de difusão. Obtenha sua chave aqui [Huggingface API Key](https://huggingface.co/settings/tokens). Registre-se e logue para obter a chave.
* `Temperature`: O parâmetro controla o grau de aleatoriedade na seleção do token. A temperatura é usada para amostragem durante a geração de resposta, o que ocorre quando top P e top K são aplicados. Temperaturas mais baixas são boas para comandos que exigem uma resposta mais determinista ou menos aberta, enquanto temperaturas mais altas podem levar a resultados mais diversos ou criativos. Uma temperatura de 0 é determinista, o que significa que a resposta de probabilidade mais alta é sempre selecionada.
* `Top P`: O parâmetro top P muda a forma como o modelo seleciona tokens para saída. Os tokens são selecionados do mais ao menos provável até que a soma das probabilidades seja igual ao valor de top P. Por exemplo, se os tokens A, B e C tiverem uma probabilidade de 0,3, 0,2 e 0,1 e o valor de top P for 0,5, o modelo selecionará A ou B como o próximo token usando a temperatura e excluirá C como candidato. O valor padrão de top P é 0,95..
* `Top K`: O parâmetro muda a forma como o modelo seleciona tokens para saída. O valor top K de 1 indica que o token selecionado é o mais provável entre todos no vocabulário do modelo (também chamado de decodificação gananciosa), enquanto top K de 3 significa que o próximo token é selecionado entre os três mais prováveis de usar a temperatura. Para cada etapa da seleção de tokens, são amostrados os tokens top K com as maiores probabilidades. Os tokens são filtrados ainda mais com base em top P com o token final selecionado por amostragem de temperatura..
* `Max output prompt tokens`: Especifica o número máximo de tokens que podem ser gerados para a resposta de prompt.
* `Max output tokens`: Especifica o número máximo de tokens que podem ser gerados nas respostas em geral.

## Problemas conhecidos
Durante a execução alguns problemas podem acontencer:
* Tela preta na imagem: Este é um problema do decodificador de difusão que pode ocorrer.
* Mensagem de erro "Ops! houve um erro ao gerar sua resposta...": Nem sempre a API de difusão do Hugginface está pronta para devolver uma resposta quando solicitada, existe um "cold start" do modelo que pode levar a um timeout, no entanto. Nesta situação basta tentar novamente após alguns segundos até que a API possa responder normalmente. 

## Exemplos gerados
### Um gato
<p align="center">
  <img src="docs/0 - a cat.PNG">
</p>

### O ursinho Pooh
<p align="center">
  <img src="docs/1 - pooh.PNG">
</p>

### Um pitbull
<p align="center">
  <img src="docs/2 - pitbull.PNG">
</p>

### Um menino
<p align="center">
  <img src="docs/3 - a boy.PNG">
</p>

## Licença
Este projeto está regido pela [MIT license](LICENSE).

## Contato
Se você tem alguma dúvida ou sugestão, sinta-se livre para enviar sua questão no e-mail: contato@devaiexp.com