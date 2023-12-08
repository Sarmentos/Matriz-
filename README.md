empresa = ['    Vale  ', '  Unimed  ' , '  PicPay  ']
cargos = ['  Programador Back-end  ', '  Programador Front-end  ', '  Programador Full-stack  ']

matriz = [[" " for _ in range(len(empresa))] for _ in range(len(cargos))]

def inserir_dados():
    for i in range(len(cargos)):  
        for j in range(len(empresa)):  
            while True:
                try:
                    elemento = int(input(f"Insira o número de candidatos para {cargos[i]} na {empresa[j]}: "))
                    matriz[i][j] = elemento
                    break
                except ValueError:
                    print("Por favor, insira um número inteiro.")

def visualizar_dados():
    print("    ".join(cargos))  
    for i in range(len(cargos)):
        print(empresa[i],end="       ")  
        for j in range(len(empresa)):
           
            print(f"[{matriz[i][j]:^10}]", end=" ")
        print("")

def pesquisar_dados():
    while True:
        try:
            valor_pesquisa = int(input("Digite o valor a ser pesquisado: "))
            break
        except ValueError:
            print("Por favor, insira um número inteiro.")

    encontrado = False
    for i in range(len(cargos)):
        for j in range(len(empresa)):
            if matriz[i][j] == valor_pesquisa:
                print(f"Valor encontrado para o cargo {cargos[i]} na empresa {empresa[j]}")
                encontrado = True
    if not encontrado:
        print("Valor não encontrado na matriz.")

def alterar_dados():
    while True:
        try:
            car = int(input("Digite o índice do cargo (0 para Programador Back-end, 1 para Programador Front-end, 2 para Programador Full-stack): "))
            emp = int(input("Digite o índice da empresa (0 para Vale, 1 para Unimed, 2 para PicPay): "))
            if emp not in range(len(empresa)) or car not in range(len(cargos)):
                raise IndexError
            novo_valor = int(input("Digite o novo valor: "))
            matriz[car][emp] = novo_valor
            print("Dado alterado com sucesso.")
            break
        except ValueError:

            print("Por favor, insira um número inteiro.")
        except IndexError:

            print("Índice inválido. Tente novamente.")

while True:
    try:
        print("-----------Início------------")
        print(" Programa desenvolvido por: Lucas Sarmento")
        print("-----------Menu-----------")
        print("1 - Inserir Dados")
        print("2 - Visualizar Dados")
        print("3 - Pesquisar Dados")
        print("4 - Alterar Dados")
        print("5 - Sair")
        opcao = int(input("Escolha uma opção: "))

        if opcao == 1:
            inserir_dados()
        elif opcao == 2:
            visualizar_dados()
        elif opcao == 3:
            pesquisar_dados()
        elif opcao == 4:
            alterar_dados()
        elif opcao == 5:
            break
        else:
            print("Opção inválida.")
    except ValueError:
        print("Por favor, insira um número para escolher uma opção.")

