# EjemplosMundoReal_POO
class Habitacion:
    def __init__(self, numero, tipo, precio):
        self.numero = numero
        self.tipo = tipo
        self.precio = precio
        self.disponible = True

    def reservar(self):
        if self.disponible:
            self.disponible = False
            return "Habitación reservada con éxito."
        else:
            return "La habitación no está disponible."

class Hotel:
    def __init__(self, nombre):
        self.nombre = nombre
        self.habitaciones = []

    def agregar_habitacion(self, habitacion):
        self.habitaciones.append(habitacion)

    def mostrar_disponibles(self):
        for h in self.habitaciones:
            if h.disponible:
                print(f"Habitación {h.numero} - {h.tipo} - ${h.precio}")

# Uso
hotel = Hotel("Hotel Central")
hotel.agregar_habitacion(Habitacion(101, "Simple", 30))
hotel.agregar_habitacion(Habitacion(102, "Doble", 50))

hotel.mostrar_disponibles()
print(hotel.habitaciones[0].reservar())


class Producto:
    def __init__(self, nombre, precio):
        self.nombre = nombre
        self.precio = precio

class Carrito:
    def __init__(self):
        self.productos = []

    def agregar_producto(self, producto):
        self.productos.append(producto)

    def total(self):
        return sum(p.precio for p in self.productos)

# Uso
p1 = Producto("Laptop", 800)
p2 = Producto("Mouse", 20)

carrito = Carrito()
carrito.agregar_producto(p1)
carrito.agregar_producto(p2)

print("Total a pagar: $", carrito.total())


class Estudiante:
    def __init__(self, nombre):
        self.nombre = nombre
        self.notas = []

    def agregar_nota(self, nota):
        self.notas.append(nota)

    def promedio(self):
        return sum(self.notas) / len(self.notas)

class Curso:
    def __init__(self, nombre):
        self.nombre = nombre
        self.estudiantes = []

    def matricular(self, estudiante):
        self.estudiantes.append(estudiante)

# Uso
e1 = Estudiante("Carlos")
e1.agregar_nota(8)
e1.agregar_nota(9)

curso = Curso("Programación")
curso.matricular(e1)

print("Promedio de", e1.nombre, ":", e1.promedio())
