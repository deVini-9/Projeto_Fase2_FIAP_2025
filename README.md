# Projeto_Fase2_FIAP_2025
Este repositório contém os artefatos do projeto da Fase 2 do PBL, desenvolvido pelos alunos do 1º Ano. O projeto abrange operações de banco de dados (DML, DQL) e o desenvolvimento de um algoritmo em Python para gerenciamento de produtos, além de uma proposta de programa de sustentabilidade.

## Equipe (Grupo 21)
    Hiago Cezar Ribeiro Fidalgo
    Isack Rafael Lagares Santos
    Nicole Lourival
    Tiphany Nemet Martins
    Vinícius Mugnes Ferreira Vitorino

# Visão Geral do Projeto
Este projeto demonstra a aplicação de comandos SQL (DML e DQL) para manipulação e consulta de dados em um banco de dados Oracle para a empresa fictícia "Melhores Compras". Adicionalmente, foi desenvolvido um script Python para cadastrar produtos, calcular ICMS e salvar as informações em formato JSON. Uma proposta de programa ESG também foi elaborada.

# Operações de Banco de Dados (SQL)
Foram executados comandos DML para inserir e atualizar dados, e comandos DQL para consultar informações no banco de dados. As evidências detalhadas da execução estão nos arquivos .docx.

# Comandos DML (Manipulação de Dados)
O script [1_2_comandos_DML.sql](https://github.com/deVini-9/Projeto_Fase2_FIAP_2025/blob/12ee7ce43105a646bb8c5632f98c82896364043d/PBL_1%C2%BA_Ano_Fase2_grupo_21/1_2_comandos_DML.sql) contém os comandos utilizados para popular e modificar as tabelas.

# Script DML:
    -- Resposta do Comando SQL
    --item a)
    --Cadastro Clientes
    INSERT INTO MC_CLIENTE (
        NM_CLIENTE,
        QT_ESTRELAS,
        VL_MEDIO_COMPRA,
        ST_CLIENTE,
        DS_EMAIL,
        NR_TELEFONE,
        NM_LOGIN,
        DS_SENHA)
    VALUES ('CLIENTE PESSOA FISICA', 3, 0, 'A', 'CLIENTEFISICA@GMAIL.COM', '(011)99855-6598', 'CLIENTEFISICA', '123456');
    COMMIT;
    
    INSERT INTO MC_CLIENTE (
        NM_CLIENTE,
        QT_ESTRELAS,
        VL_MEDIO_COMPRA,
        ST_CLIENTE,
        DS_EMAIL,
        NR_TELEFONE,
        NM_LOGIN,
        DS_SENHA)
    VALUES ('CLIENTE PESSOA JURIDICA', 2, 0, 'A', 'CLIENTEJURIDICA@GMAIL.COM', '(011)99844-6878', 'CLIENTEJURIDICA', '123456');
    COMMIT;
    
    --Cadastro Cliente Pessoa Fisica
    INSERT INTO MC_CLI_FISICA (
        NR_CLIENTE,
        DT_NASCIMENTO,
        FL_SEXO_BIOLOGICO,
        DS_GENERO,
        NR_CPF)
    VALUES(8, TO_DATE('23/11/1980','DD/MM/YYYY'), 'F', 'FEMININO',44271349801);
    COMMIT;
    
    
    --Cadastro Cliente Pessoa Juridica
    INSERT INTO MC_CLI_JURIDICA (
        NR_CLIENTE,
        DT_FUNDACAO,
        NR_CNPJ,
        NR_INSCR_EST)
    VALUES (9,TO_DATE('01/02/2020','DD/MM/YYYY'),  '590001980545','68885487');
    COMMIT;
    
    --Cadastro endereço Cliente Pessoa Fisica
    INSERT INTO MC_END_CLI (
        NR_CLIENTE,
        CD_LOGRADOURO_CLI,
        NR_END,
        DS_COMPLEMENTO_END,
        DT_INICIO,
        DT_TERMINO,
        ST_END)
    VALUES (8, 3, 710, null, to_date ('01/01/2025', 'dd/mm/yyyy'), null, 'A');
    COMMIT;
    
    --Cadastro endereço Cliente Pessoa Juridica
    INSERT INTO MC_END_CLI (
        NR_CLIENTE,
        CD_LOGRADOURO_CLI,
        NR_END,
        DS_COMPLEMENTO_END,
        DT_INICIO,
        DT_TERMINO,
        ST_END)
    VALUES (11, 5, 516, null, to_date ('01/02/2025', 'dd/mm/yyyy'), null, 'A');
    COMMIT;
    
    --Item b)
    --Cadastro Clientes
    INSERT INTO MC_CLIENTE (
        NM_CLIENTE,
        QT_ESTRELAS,
        VL_MEDIO_COMPRA,
        ST_CLIENTE,
        DS_EMAIL,
        NR_TELEFONE,
        NM_LOGIN,
        DS_SENHA)
    VALUES ('CLIENTE LOGIN EXISTENTE', 4, 0, 'A', 'CLIENTELOGINEXISTENTE@GMAIL.COM', '(011)99855-6598', 'CLIENTEFISICA', '123456');
    
    -- Item c)
    SELECT * FROM MC_FUNCIONARIO WHERE CD_FUNCIONARIO = 7;
    
    UPDATE MC_FUNCIONARIO
    SET DS_CARGO = 'Superintendente',
        VL_SALARIO = VL_SALARIO * 1.12
    WHERE CD_FUNCIONARIO = 7;
    
    --Item d)
    SELECT * FROM MC_END_CLI WHERE NR_CLIENTE = 11;
    
    UPDATE MC_END_CLI
    SET ST_END = 'I',
        DT_TERMINO = TO_DATE ('22/04/2025', 'DD/MM/YYYY')
    WHERE  NR_CLIENTE = 11;
    COMMIT;
    
    --Item e)
    DELETE FROM MC_ESTADO
    WHERE SG_ESTADO = 'SP';
    
    --Item f)
    SELECT * FROM MC_PRODUTO WHERE CD_PRODUTO = 3;
    
    UPDATE MC_PRODUTO
    SET ST_PRODUTO = 'X'
    WHERE CD_PRODUTO = 3;

# Evidências DML:

Inserção de Clientes: Foram inseridos clientes pessoa física e jurídica, juntamente com seus respectivos dados nas tabelas MC_CLI_FISICA e MC_CLI_JURIDICA, e endereços em MC_END_CLI.
![image](https://github.com/user-attachments/assets/ca69f435-c83b-4a7a-ab31-28d9616a0612)

![image](https://github.com/user-attachments/assets/3ed4ae80-b322-41a9-ba00-e4d43ac61d1a)

Teste de Constraint (Login Único): Tentativa de inserir um cliente com um login já existente (CLIENTEFISICA) resultou em erro, confirmando a funcionalidade da constraint UK_MC_CLIENTE_MM_LOGIN.
![image](https://github.com/user-attachments/assets/00abdd34-57b2-4972-8607-a081df51367d)

Atualização de Funcionário: O cargo e salário de um funcionário (ID 7) foram atualizados.
![image](https://github.com/user-attachments/assets/b268e873-5e3a-4474-a1b1-86664b7247c8)

Atualização de Endereço: O status do endereço de um cliente (ID 11) foi alterado para 'I' (Inativo) e uma data de término foi adicionada.
![image](https://github.com/user-attachments/assets/a881c2c3-dab0-46e6-aded-eed60c882414)

Teste de Constraint (Chave Estrangeira): Tentativa de deletar um estado ('SP') que possui cidades cadastradas falhou devido à restrição de chave estrangeira.
Teste de Constraint (Check): Tentativa de atualizar o status de um produto para 'X' falhou, pois a restrição check na coluna ST_PRODUTO permite apenas 'A' ou 'I'.
<br/>[1_2_comandos_DML.docx](https://github.com/deVini-9/Projeto_Fase2_FIAP_2025/blob/ffb5bbaef2f433e11cebcb50488b419cb12231d1/PBL_1%C2%BA_Ano_Fase2_grupo_21/1_2_comandos_DML.pdf)<br/>

# Comandos DQL (Consulta de Dados)
Foram realizadas consultas para extrair informações específicas do banco de dados.

Exemplos de Consultas (Execução em 1_3_comandos_DQL.docx):

Consulta Produtos por Categoria: Listagem de produtos agrupados por categoria.
![image](https://github.com/user-attachments/assets/98ec1599-acc5-4406-b672-5bdc42a21160)

Consulta Detalhada Cliente Pessoa Física: Exibição de dados do cliente, incluindo dia da semana do nascimento e idade.
![image](https://github.com/user-attachments/assets/30b6ee22-dfee-45bb-8555-a215880c1af3)

Consulta Visualizações de Vídeo: Tentativa de listar visualizações de vídeos de produtos (Observação: a tabela de visualizações não foi populada nos dados iniciais fornecidos).
![image](https://github.com/user-attachments/assets/f567367b-60c3-47f8-b320-75653f5f12b2)

(Consultas e resultados completos no arquivo [1_3_comandos_DQL.docx](https://github.com/deVini-9/Projeto_Fase2_FIAP_2025/blob/ffb5bbaef2f433e11cebcb50488b419cb12231d1/PBL_1%C2%BA_Ano_Fase2_grupo_21/1_3_comandos_DQL.pdf))

# Aplicação de Gerenciamento de Produtos (Python)
Foi desenvolvido um script em Python ([1_4_algoritmo_produto.py](https://github.com/deVini-9/Projeto_Fase2_FIAP_2025/blob/ffb5bbaef2f433e11cebcb50488b419cb12231d1/PBL_1%C2%BA_Ano_Fase2_grupo_21/1_4_algoritmo_produto.py)) para facilitar o cadastro de produtos, calcular o ICMS (18%) sobre o valor e salvar os dados em um arquivo JSON. O script garante que um mínimo de 5 produtos sejam cadastrados antes de gerar o arquivo.

Código Python:

    from typing import List, Dict
    import os
    import json
    
    
    COMANDO_LIMPAR_TERMINAL = "cls" if os.name == "nt" else "clear"
    ICMS_PERCENTUAL: float = 0.18
    MIN_PRODUTOS_SALVAR: int = 5
    NOME_ARQUIVO_JSON: str = "1_5_arquivo_produto.json"
    
    calcular_icms = lambda valor_produto: round(valor_produto * ICMS_PERCENTUAL, 2)
    
    
    def solicitar_input(
        mensagem: str, 
        tipo=str, 
        erro="Entrada Inválida", 
        validar=None
    ) -> float:
        """
        Solicita e valida a entrada do usuário.
    
        Args:
            mensagem (str): Mensagem para exibir ao usuário.
            tipo: Tipo do dado esperado.
            erro (str): Mensagem de erro se a entrada for inválida.
            validar: Função de validação se necessário.
    
        Returns:
            Valor: O valor validado e tratado
        """
        while True:
            try:
                valor = input(mensagem).strip()
    
                if not valor and tipo is str:
                    print("Erro: A entrada não pode estar vazia.")
                    continue
    
                valor = tipo(valor.replace(",", ".")) if tipo is float else valor
    
                if validar and not validar(valor):
                    continue
                return valor
            except ValueError:
                print(erro)
    
    
    def validar_numero(valor_produto):
        """
        Valida se o valor do produto é positivo.
    
        Returns:
            bool: True se o valor for positivo, False caso for negativo
        """
        if valor_produto < 0:
            print("Erro: O valor não pode ser menor que 0.")
            return False
        return True
    
    
    def perguntar_se_continua(mensagem: str = "\nDeseja continuar ? (Sim/Não) ") -> bool:
        """
        Pergunta ao usuário se deseja continuar a operação.
    
        Args:
            mensagem: Mensagem a ser exibida para o usuário.
    
        Returns:
            bool: True se a resposta for sim, False caso for não. 
        """
        while True:
            resposta = input(mensagem).strip().lower()
    
            if resposta in ["sim", "s"]:
                return True
            elif resposta in ["não", "nao", "n"]:
                return False
    
            print("Resposta Inválida! Digite 'Sim' ou 'Não'.")    
    
    
    def cadastrar_produto() -> Dict[str, float, str, float]:
        """
        Cadastra um novo produto.
    
        Returns:
            produto: Um dicionário com as entradas do usuário.
        """
        os.system(COMANDO_LIMPAR_TERMINAL)
    
        print("--- Cadastro de Produtos ---\n\n")
    
        descricao_produto = solicitar_input("Descrição do Produto: ")
        valor_produto = solicitar_input("Valor do Produto: R$ ", float, "Valor inválido", validar_numero)
        tipo_embalagem = solicitar_input("Tipo da Embalagem do Produto: ")
    
        produto = {
            "descricao_produto": descricao_produto,
            "valor_produto": valor_produto,
            "tipo_embalagem": tipo_embalagem,
            "icms_produto": calcular_icms(valor_produto)
        }
    
        os.system(COMANDO_LIMPAR_TERMINAL)
    
        return produto
    
    def salvar_json(produtos):
        """
        Salva os produtos cadastrados em um arquivo JSON.
    
        Args:
            produtos: Lista de produtos a serem salvos.
        """
        try:
            with open(NOME_ARQUIVO_JSON, "w", encoding="utf-8") as f:
                json.dump(produtos, f, ensure_ascii=False, indent=4)
            print("Arquivo gerado com sucesso!")
        except (IOError, Exception) as e:
            print("Erro ao salvar arquivo: {e}")
    
    def verificar_quantidade_produtos(produtos):
        """
        Verifica se o número de produtos cadastros atende a quantidade mínima.
    
        Args:
            produtos: Lista de produtos cadastrados.
    
        Returns:
            bool: True se o número de produtos atender a quantidade mínima, False caso não atender.
        """
        if len(produtos) < MIN_PRODUTOS_SALVAR:
            print(f"Você cadastrou apenas {len(produtos)} produto(s). É necessário ter no mínimo {MIN_PRODUTOS_SALVAR} produtos cadastrados para gerar o arquivo JSON.")
            return False
        return True
    
    
    def cadastro_produto() -> List[dict]:
        """
        Gerencia o cadastro dos produtos
    
        Returns:
            produtos: Lista de produtos cadastrados.
        """
        produtos: List[dict] = []
    
        while True:
            produto = cadastrar_produto()
            produtos.append(produto)
    
            print("\nProduto cadastrado com sucesso!")
    
            if not perguntar_se_continua("\n\nDeseja cadastrar outro produto ? (Sim/Não) "):
                break
        
        return produtos
    
    
    def main():
        os.system(COMANDO_LIMPAR_TERMINAL)
        produtos = cadastro_produto()
    
        
        while not verificar_quantidade_produtos(produtos):
            if perguntar_se_continua("\n\nSe prosseguir o arquivo não será gerado! Deseja encerrar o cadastro ? (Sim/Não) "):
                print("\nPrograma encerrado! Nenhum arquivo será gerado.")
                return
    
            produto = cadastrar_produto()
            produtos.append(produto)
        
        os.system(COMANDO_LIMPAR_TERMINAL)
        print("--- Salvando arquivo ---")
        salvar_json(produtos)
    
    
    if __name__ == "__main__":
        try: 
            main()
        except KeyboardInterrupt:
            print("\nCadastro interrompido!")

Exemplo de Saída JSON ([1_5_arquivo_produto.json](https://github.com/deVini-9/Projeto_Fase2_FIAP_2025/blob/ffb5bbaef2f433e11cebcb50488b419cb12231d1/PBL_1%C2%BA_Ano_Fase2_grupo_21/1_5_arquivo_produto.json))

# Programa de Sustentabilidade e Responsabilidade Social (ESG)
Como parte do projeto, foi desenvolvida uma proposta de implementação de práticas Ambientais, Sociais e de Governança (ESG) para a empresa Melhores Compras LTDA. O programa visa analisar o estado atual da empresa nessas áreas e definir metas e iniciativas para melhorar seu desempenho sustentável e socialmente responsável.

Principais Eixos do Programa (Detalhes completos da proposta nos arquivos [1_6_ProgramaSustentabilidade.docx](https://github.com/deVini-9/Projeto_Fase2_FIAP_2025/blob/ffb5bbaef2f433e11cebcb50488b419cb12231d1/PBL_1%C2%BA_Ano_Fase2_grupo_21/1_6_ProgramaSustentabilidade.pdf) e [1_6_ProgramaSustentabilidade.pdf](https://github.com/deVini-9/Projeto_Fase2_FIAP_2025/blob/ffb5bbaef2f433e11cebcb50488b419cb12231d1/PBL_1%C2%BA_Ano_Fase2_grupo_21/1_6_ProgramaSustentabilidade.pdf)):

Diagnóstico Inicial: Análise das condições de trabalho, diversidade, transparência, ética, gestão de resíduos, emissões e uso de recursos naturais.

Definição de Metas ESG: Estabelecimento de objetivos claros para aumentar a diversidade, investir em desenvolvimento comunitário, adotar políticas de transparência mais rigorosas, aumentar a reciclagem, usar embalagens sustentáveis e reduzir a pegada de carbono.

Implementação de Iniciativas: Parcerias com ONGs, treinamentos para funcionários, publicação de relatórios de sustentabilidade (GRI), adesão ao Pacto Global da ONU, programas de redução de lixo eletrônico e modernização de data centers.

Monitoramento e Relatórios: Desenvolvimento de KPIs, divulgação pública de resultados e auditorias periódicas.

Engajamento e Comunicação: Workshops, seminários e comunicação transparente das iniciativas e resultados.

Benefícios Esperados: Melhoria nas condições de trabalho, aumento da confiança dos stakeholders e redução do impacto ambiental.

# Conclusão
Este projeto integrou conhecimentos de banco de dados SQL, programação Python e conceitos de sustentabilidade (ESG), resultando em uma solução prática para gerenciamento de dados e uma proposta estratégica para a responsabilidade corporativa da Melhores Compras LTDA.
