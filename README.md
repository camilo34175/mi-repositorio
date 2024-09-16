# mi-repositorio
class CuentaBancaria:
    def __init__(self, nombre, saldo_inicial=0):
        self.nombre = nombre
        self.saldo = saldo_inicial

    def depositar(self, monto):
        if monto > 0:
            self.saldo += monto
            print(f"Deposito exitoso: ${monto}. Saldo actual: ${self.saldo}")
        else:
            print("Monto a depositar debe ser positivo.")

    def retirar(self, monto):
        if 0 < monto <= self.saldo:
            self.saldo -= monto
            print(f"Retiro exitoso: ${monto}. Saldo actual: ${self.saldo}")
        else:
            print("Fondos insuficientes o monto inválido.")

    def mostrar_saldo(self):
        print(f"Saldo de {self.nombre}: ${self.saldo}")

class SistemaBancario:
    def __init__(self):
        self.cuentas = {}

    def crear_cuenta(self, nombre, saldo_inicial=0):
        if nombre not in self.cuentas:
            self.cuentas[nombre] = CuentaBancaria(nombre, saldo_inicial)
            print(f"Cuenta creada para {nombre} con saldo inicial ${saldo_inicial}.")
        else:
            print("La cuenta ya existe.")

    def depositar(self, nombre, monto):
        if nombre in self.cuentas:
            self.cuentas[nombre].depositar(monto)
        else:
            print("La cuenta no existe.")

    def retirar(self, nombre, monto):
        if nombre in self.cuentas:
            self.cuentas[nombre].retirar(monto)
        else:
            print("La cuenta no existe.")

    def mostrar_saldo(self, nombre):
        if nombre in self.cuentas:
            self.cuentas[nombre].mostrar_saldo()
        else:
            print("La cuenta no existe.")

# Ejemplo de uso
sistema = SistemaBancario()

# Crear cuentas
sistema.crear_cuenta("Juan", 100)
sistema.crear_cuenta("Ana")

# Realizar operaciones
sistema.depositar("Juan", 50)
sistema.retirar("Ana", 20)  # Fondos insuficientes
sistema.depositar("Ana", 200)
sistema.retirar("Ana", 20)

# Mostrar saldo
sistema.mostrar_saldo("Juan")
sistema.mostrar_saldo("Ana")

