# Import the necessary modules.
import os

# Clear the output.
os.system("clear")

# Define the GestaoResiduos class.
class GestaoResiduos:
    def _init_(self):
        self.residuos = {}
        self.economia = 0

    def adicionar_residuo(self, tipo, quantidade):
        if tipo in self.residuos:
            self.residuos[tipo] += quantidade
        else:
            self.residuos[tipo] = quantidade

    def relatorio_residuos(self):
        print("Relatório de Resíduos:")
        for tipo, quantidade in self.residuos.items():
            print(f"{tipo}: {quantidade}kg")

    def recomendacoes(self):
        print("\nRecomendações para destinação dos resíduos:")
        for tipo in self.residuos:
            if tipo == "concreto":
                print("- Concreto: Pode ser triturado e reutilizado como base para pavimentação.")
            elif tipo == "madeira":
                print("- Madeira: Pode ser reciclada ou utilizada para geração de energia.")
            elif tipo == "metal":
                print("- Metal: Deve ser enviado para reciclagem.")
            elif tipo == "vidro":
                print("- Vidro: Pode ser reciclado e reutilizado em produtos de vidro.")
            elif tipo == "plastico":
                print("- Plástico: Deve ser reciclado e reutilizado em produtos de plástico.")
            elif tipo == "papel":
                print("- Papel: Pode ser reciclado e reutilizado em produtos de papel.")
            elif tipo == "orgânico":
                print("- Orgânico: Pode ser compostado e utilizado como adubo.")
            else:
                print(f"- {tipo}: Verificar regulamentações locais para destinação adequada.")

    def calcular_economia(self):
        self.economia = 0
        for tipo, quantidade in self.residuos.items():
            if tipo == "concreto":
                self.economia += quantidade * 0.5  # economia de 50% ao reutilizar concreto
            elif tipo == "madeira":
                self.economia += quantidade * 0.3  # economia de 30% ao reciclar madeira
            elif tipo == "metal":
                self.economia += quantidade * 0.7  # economia de 70% ao reciclar metal
            elif tipo == "vidro":
                self.economia += quantidade * 0.4  # economia de 40% ao reciclar vidro
            elif tipo == "plastico":
                self.economia += quantidade * 0.2  # economia de 20% ao reciclar plástico
            elif tipo == "papel":
                self.economia += quantidade * 0.1  # economia de 10% ao reciclar papel
            elif tipo == "orgânico":
                self.economia += quantidade * 0.6  # economia de 60% ao compostar orgânico
        print(f"\nEconomia total: R$ {self.economia:.2f}")

# Define the main function.
def main():
    gestao = GestaoResiduos()
    while True:
        print("\nGestão de Resíduos na Engenharia Civil")
        tipo = input("Digite o tipo de resíduo (ou 'air' para encerrar): ").lower()
        if tipo == 'air':
            break
        quantidade = float(input(f"Digite a quantidade de {tipo} em kg: "))
        gestao.adicionar_residuo(tipo, quantidade)

    gestao.relatorio_residuos()
    gestao.recomendacoes()
    gestao.calcular_economia()

# Run the main function.
if __name__ == "_main_":
    main()
