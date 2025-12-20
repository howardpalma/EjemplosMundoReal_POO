class Libro:
    def __init__(self, titulo, autor, isbn):
        self.titulo = titulo
        self.autor = autor
        self.isbn = isbn
        self.disponible = True
    
    def prestar(self):
        if self.disponible:
            self.disponible = False
            return True
        return False
    
    def devolver(self):
        self.disponible = True
    
    def __str__(self):
        estado = "Disponible" if self.disponible else "Prestado"
        return f"'{self.titulo}' - {self.autor} ({estado})"


class Usuario:
    def __init__(self, nombre, id_usuario):
        self.nombre = nombre
        self.id_usuario = id_usuario
        self.libros_prestados = []
    
    def tomar_prestado(self, libro):
        if libro.prestar():
            self.libros_prestados.append(libro)
            return True
        return False
    
    def devolver_libro(self, libro):
        if libro in self.libros_prestados:
            libro.devolver()
            self.libros_prestados.remove(libro)
            return True
        return False
    
    def mostrar_libros(self):
        if self.libros_prestados:
            print(f"Libros de {self.nombre}:")
            for libro in self.libros_prestados:
                print(f"  - {libro.titulo}")
        else:
            print(f"{self.nombre} no tiene libros prestados")


# Uso del sistema de biblioteca
if __name__ == "__main__":
    # Crear libros
    libro1 = Libro("Cien años de soledad", "Gabriel García Márquez", "12345")
    libro2 = Libro("1984", "George Orwell", "67890")
    
    # Crear usuarios
    usuario1 = Usuario("Ana", "U001")
    usuario2 = Usuario("Carlos", "U002")
    
    # Interacciones
    print("=== Sistema de Biblioteca ===")
    print(libro1)
    print(libro2)
    
    usuario1.tomar_prestado(libro1)
    print(f"\nDespués de préstamo:")
    print(libro1)
    usuario1.mostrar_libros()
    
    usuario1.devolver_libro(libro1)
    print(f"\nDespués de devolución:")
    print(libro1)
