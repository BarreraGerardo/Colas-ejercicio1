class NodoCola:
    def __init__(self, dato):
        self.dato = dato
        self.siguiente = None

class Cola:
    def __init__(self):
        self.frente = None
        self.final = None

    def encolar(self, dato):
        nuevo_nodo = NodoCola(dato)
        if self.final is None:
            self.frente = nuevo_nodo
        else:
            self.final.siguiente = nuevo_nodo
        self.final = nuevo_nodo

    def desencolar(self):
        if self.frente is None:
            return None
        dato = self.frente.dato
        self.frente = self.frente.siguiente
        if self.frente is None:
            self.final = None
        return dato

    def esta_vacia(self):
        return self.frente is None

def sumar_colas(cola_a, cola_b):
    cola_resultado = Cola()

    while not cola_a.esta_vacia() and not cola_b.esta_vacia():
        suma = cola_a.desencolar() + cola_b.desencolar()
        cola_resultado.encolar(suma)

    return cola_resultado

def crear_colas():
    # Crear colas vacías
    cola_1 = Cola()
    cola_2 = Cola()
    cola_resultado = Cola()

    # Solicitar cantidad de valores para las colas 1 y 2
    cantidad_valores = int(input("Ingrese la cantidad de valores para las colas 1 y 2: "))

    # Solicitar los valores para la cola 1
    print("Ingrese los valores para la cola 1:")
    for _ in range(cantidad_valores):
        valor = int(input("Ingrese un valor: "))
        cola_1.encolar(valor)

    # Solicitar los valores para la cola 2
    print("Ingrese los valores para la cola 2:")
    for _ in range(cantidad_valores):
        valor = int(input("Ingrese un valor: "))
        cola_2.encolar(valor)

    # Sumar las colas 1 y 2 y guardar el resultado en la cola resultado
    cola_resultado = sumar_colas(cola_1, cola_2)

    return cola_1, cola_2, cola_resultado

# Crear las colas
cola_1, cola_2, cola_resultado = crear_colas()

# Imprimir las colas
print("\nCola 1:")
while not cola_1.esta_vacia():
    print(cola_1.desencolar(), end="\t")
print()

print("\nCola 2:")
while not cola_2.esta_vacia():
    print(cola_2.desencolar(), end="\t")
print()

print("\nCola Resultado:")
while not cola_resultado.esta_vacia():
    print(cola_resultado.desencolar(), end="\t")
print()
