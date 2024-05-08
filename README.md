senha = "123"
login = "teste"

login_2 = input(str("Digite seu login:"))
senha_2 = input(str("Digite sua senha:"))

if (login_2 == login and senha_2 == senha):
    print("\nBem vinda ao banco H&K",)
else:
    print("Login e senha incorreto") 

menu = """ 
[1]Depositar
[2]Sacar
[3]Extrato 
[4]Sair

->"""

saldo = 0
limite = 600
extrato = ""
numero_saque = 0 
limite_saque = 3

while True:

    opcao = input(menu)
   
    if opcao == "1":
        valor = float(input("Informe o valor de deposito:"))
        
        if valor > 0:
            saldo += valor 
            extrato += f"Deposito: R${valor:.2f}\n"

        else:
            print("Operação falhou valor informado está invalido")

    elif opcao == "2":
        valor = float(input("Informe o valor de saque:"))

        excedeu_saldo = valor > saldo

        excedeu_limite = valor > limite

        excedeu_saque = numero_saque >= limite_saque

        if excedeu_saldo:
            print("Operação falhou, Seu saldo é insuficiente.")

        elif excedeu_limite:
            print("Operação falhou, Saque execede o limete diario")

        elif excedeu_saque: 
            print("Operação falhou valor informado está invalido")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:2f}\n"

        else:
            print("Operação falhou, Valor informado naão é valido.")   
                        
    elif opcao == "3":
        print("\n========== Extrato ==========")
        print("Não foraram realizadas nenhuma movimentação." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("=============================")

    elif opcao == "4":
        break

    else:
        print("Operação inválida, Por favor selecione novamente a opção desejada.")
