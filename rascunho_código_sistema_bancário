from datetime import datetime

class ContaBancaria:
    def __init__(self, titular, saldo=0):
        self.titular = titular
        self.saldo = saldo
        self.transacoes = []
        self.saque_diario = 0
        self.data_ultimo_saque = None

    def depositar(self, valor):
        if valor > 0:
            self.saldo += valor
            self.transacoes.append(f'Depósito: +R${valor}')
            print(f'Depósito de R${valor} realizado com sucesso.')
        else:
            print('Valor de depósito inválido.')

    def sacar(self, valor):
        data_atual = datetime.now().date()
        if self.data_ultimo_saque != data_atual:
            self.saque_diario = 0
            self.data_ultimo_saque = data_atual

        if valor > 0 and valor <= self.saldo and valor <= 500:
            if self.saque_diario < 3:
                self.saldo -= valor
                self.transacoes.append(f'Saque: -R${valor}')
                self.saque_diario += 1
                print(f'Saque de R${valor} realizado com sucesso.')
            else:
                print('Limite de 3 saques diários já foi atingido.')
        else:
            print('Valor de saque inválido, saldo insuficiente ou valor acima do limite de R$500.')

    def extrato(self):
        print(f'Extrato de {self.titular}:')
        for transacao in self.transacoes:
            print(transacao)
        print(f'Saldo atual: R${self.saldo}')

# Exemplo de uso:
conta_da_ana = ContaBancaria('Ana')
conta_da_ana.depositar(1000)
conta_da_ana.sacar(100)
conta_da_ana.sacar(200)
conta_da_ana.sacar(100)
conta_da_ana.sacar(50)  # Este saque não será permitido, pois excede o limite de saques diários.
conta_da_ana.extrato()
