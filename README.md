# Diagnóstico de Pragas Agrícolas com BERT

Este projeto utiliza um modelo de **BERT** para diagnosticar pragas agrícolas com base nas respostas dos usuários sobre sintomas e condições de plantio. O backend é implementado em **Python** com **Flask**, e a API é hospedada no **Google Colab** usando **ngrok** para acesso externo. 

---
## Protótipo do Aplicativo

<div align="center">
  <strong>Acesse o protótipo do aplicativo no Figma:</strong><br>
  <a href="https://www.figma.com/proto/5MJSndRcf5vzjuyOpr34bC/Mobile-Dashboard-UI-(Community)?node-id=0-1&t=Kyf1DkGB5MBF07TB-1">
    Link para o Figma
  </a>
</div>

---
## Sumário

- [Sobre o Projeto](#sobre-o-projeto)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Instalação](#instalação)
- [Configuração](#configuração)
- [Uso](#uso)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Contribuição](#contribuição)
- [Licença](#licença)

---

## Sobre o Projeto

Este projeto visa fornecer uma ferramenta de diagnóstico para pragas agrícolas, ajudando produtores a identificar e tratar pragas com base nas culturas cultivadas, condições climáticas, e sintomas observados. Usamos um modelo BERT pré-treinado para processar as respostas e fornecer recomendações de diagnóstico e tratamento baseadas em dados extraídos de planilhas (`Base.xlsx` e `Culturas_e_pragas.xlsx`).


---

## Tecnologias Utilizadas

- **Python**: Linguagem de programação principal.
- **Flask**: Framework para criar a API.
- **Transformers (BERT)**: Para processamento de linguagem natural e embeddings.
- **pandas**: Manipulação e leitura de dados das planilhas.
- **ngrok**: Exposição da API Flask hospedada no Google Colab para acesso externo.
- **Google Colab**: Ambiente de execução para o modelo BERT e a API.

---

## Instalação

### 1. Clonar o Repositório
```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
cd seu-repositorio
```

### 2. Instalar Dependências
As dependências podem ser instaladas no Google Colab ou em um ambiente local.

Para instalação local, use:
```bash
pip install -r requirements.txt
```

Para instalação no Google Colab, rode:
```python
!pip install transformers torch flask flask-ngrok pandas
```

---

## Configuração

1. **Upload das Planilhas**: Carregue `Base.xlsx` e `Culturas_e_pragas.xlsx` diretamente no Google Colab usando o seguinte código:

   ```python
   from google.colab import files
   uploaded = files.upload()  # Faça o upload das planilhas
   ```

2. **Configuração do ngrok**: No Colab, utilize `flask-ngrok` para expor a API com o seguinte código:

   ```python
   from flask_ngrok import run_with_ngrok
   app = Flask(__name__)
   run_with_ngrok(app)  # Inicia o ngrok para exposição pública da API
   ```

---

## Uso

### Executar o Projeto no Google Colab

1. **Carregar as Planilhas**:
   - Use o `files.upload()` para fazer o upload das planilhas `Base.xlsx` e `Culturas_e_pragas.xlsx`.
   
2. **Rodar o Código da API**:
   - Inicie o Flask no Colab com o comando `app.run()`.

3. **Obter o Link do ngrok**:
   - Copie o link gerado pelo ngrok para acessar a API de qualquer lugar.

4. **Endpoints da API**:

   - **`/diagnostico`** (POST): Recebe as respostas do usuário e retorna um diagnóstico e recomendações de tratamento.
     - Exemplo de requisição:
       ```bash
       curl -X POST https://<ngrok-link>.ngrok.io/diagnostico \
       -H "Content-Type: application/json" \
       -d '{"respostas": ["Milho", "Folhas amareladas", "Seca prolongada"]}'
       ```

   - **`/perguntas`** (GET): Retorna as perguntas necessárias para o diagnóstico.

---

## Estrutura do Projeto

```
seu-repositorio/
│
├── main.py                   # Código principal da API em Flask
├── requirements.txt          # Lista de dependências do projeto
├── Base.xlsx                 # Planilha de perguntas e dados base
├── Culturas_e_pragas.xlsx    # Planilha com dados de pragas e tratamentos
├── README.md                 # Documentação do projeto
└── .gitignore                # Arquivos e diretórios ignorados pelo Git
```

---

## Contribuição

Contribuições são bem-vindas! Siga os passos abaixo para contribuir:

1. Faça um fork do projeto.
2. Crie uma branch para sua feature (`git checkout -b feature/NovaFeature`).
3. Faça commit de suas alterações (`git commit -m 'Adiciona NovaFeature'`).
4. Envie para a branch principal (`git push origin feature/NovaFeature`).
5. Abra um Pull Request.

---

## Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.
