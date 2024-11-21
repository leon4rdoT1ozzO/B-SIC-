
# Sistema básico de Gerenciamento de Clientes

class Cliente:
    def __init__(self, nome, email, telefone):
        self.nome = nome
        self.email = email
        self.telefone = telefone

    def __str__(self):
        return f"Cliente: {self.nome} | Email: {self.email} | Telefone: {self.telefone}"


class SistemaGerenciamento:
    def __init__(self):
        self.clientes = []

    def adicionar_cliente(self, nome, email, telefone):
        cliente = Cliente(nome, email, telefone)
        self.clientes.append(cliente)
        print(f"✅ Cliente {nome} adicionado com sucesso!")

    def listar_clientes(self):
        if not self.clientes:
            print("❌ Nenhum cliente cadastrado.")
        else:
            print("📋 Lista de Clientes:")
            for i, cliente in enumerate(self.clientes, 1):
                print(f"{i}. {cliente}")

    def remover_cliente(self, nome):
        for cliente in self.clientes:
            if cliente.nome.lower() == nome.lower():
                self.clientes.remove(cliente)
                print(f"✅ Cliente {nome} removido com sucesso!")
                return
        print(f"❌ Cliente {nome} não encontrado.")

    def buscar_cliente(self, nome):
        for cliente in self.clientes:
            if cliente.nome.lower() == nome.lower():
                print(f"🔎 Cliente encontrado: {cliente}")
                return
        print(f"❌ Cliente {nome} não encontrado.")


# Função principal
def menu():
    sistema = SistemaGerenciamento()

    while True:
        print("\n=== Menu ===")
        print("1. Adicionar Cliente")
        print("2. Listar Clientes")
        print("3. Buscar Cliente")
        print("4. Remover Cliente")
        print("5. Sair")

        opcao = input("Escolha uma opção: ")
        if opcao == "1":
            nome = input("Nome do cliente: ")
            email = input("Email do cliente: ")
            telefone = input("Telefone do cliente: ")
            sistema.adicionar_cliente(nome, email, telefone)
        elif opcao == "2":
            sistema.listar_clientes()
        elif opcao == "3":
            nome = input("Digite o nome do cliente: ")
            sistema.buscar_cliente(nome)
        elif opcao == "4":
            nome = input("Digite o nome do cliente a ser removido: ")
            sistema.remover_cliente(nome)
        elif opcao == "5":
            print("👋 Saindo do sistema. Até mais!")
            break
        else:
            print("❌ Opção inválida. Tente novamente!")


# Executar o sistema
if __name__ == "__main__":
    me
