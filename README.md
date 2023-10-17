import os
import shutil

def organizar_documentos(diretorio_origem, diretorio_destino):
    setores = ['marketing', 'financeiro', 'producao', 'administracao', 'recursos_humanos']

    # Cria os subdiretórios se não existirem
    for setor in setores:
        caminho_setor = os.path.join(diretorio_destino, setor)
        os.makedirs(caminho_setor, exist_ok=True)

    # Percorre os arquivos no diretório de origem
    for arquivo in os.listdir(diretorio_origem):
        caminho_arquivo = os.path.join(diretorio_origem, arquivo)

        # Adapte aqui para reconhecer a que setor pertence o arquivo
        # Pode ser por nome, por metadados, etc.
        setor = determinar_setor(arquivo)

        if setor in setores:
            # Move o arquivo para o diretório correspondente
            shutil.move(caminho_arquivo, os.path.join(diretorio_destino, setor, arquivo))
        else:
            print(f"Arquivo '{arquivo}' não pertence a nenhum setor conhecido.")

def determinar_setor(arquivo):
    # Adapte esta função para determinar a que setor pertence o arquivo
    # Pode ser feito por análise de nome, conteúdo, extensão, etc.
    if 'marketing' in arquivo.lower():
        return 'marketing'
    elif 'financeiro' in arquivo.lower():
        return 'financeiro'
    # Adicione mais lógica para outros setores

    # Se não for reconhecido, retorna None
    return None

if __name__ == "__main__":
    diretorio_origem = "/caminho/para/seus/documentos"
    diretorio_destino = "/caminho/para/organizar/documentos"

    organizar_documentos(diretorio_origem, diretorio_destino)

