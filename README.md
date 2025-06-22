# Sistema-de-Reservas-de-Hotel
# sistema_reservas_hotel.py

# Clase que representa una habitación del hotel
class Habitacion:
    def __init__(self, numero, tipo, precio):
        self.numero = numero
        self.tipo = tipo
        self.precio = precio
        self.esta_reservada = False

    def reservar(self):
        self.esta_reservada = True

    def liberar(self):
        self.esta_reservada = False

    def mostrar_info(self):
        estado = "Reservada" if self.esta_reservada else "Disponible"
        print(f"Habitación {self.numero} | Tipo: {self.tipo} | Precio: ${self.precio} | Estado: {estado}")


# Clase que representa a un cliente
class Cliente:
    def __init__(self, nombre, cedula):
        self.nombre = nombre
        self.cedula = cedula

    def mostrar_info(self):
        print(f"Cliente: {self.nombre} | Cédula: {self.cedula}")


# Clase que representa una reserva
class Reserva:
    def __init__(self, cliente, habitacion):
        self.cliente = cliente
        self.habitacion = habitacion

    def confirmar_reserva(self):
        if not self.habitacion.esta_reservada:
            self.habitacion.reservar()
            print(f"Reserva confirmada para {self.cliente.nombre} en la habitación {self.habitacion.numero}.")
        else:
            print(f"La habitación {self.habitacion.numero} ya está reservada.")


# Crear algunas habitaciones
habitacion1 = Habitacion(101, "Individual", 40)
habitacion2 = Habitacion(102, "Doble", 70)

# Mostrar información inicial
habitacion1.mostrar_info()
habitacion2.mostrar_info()

# Crear un cliente
cliente1 = Cliente("Carlos Pérez", "1234567890")

# Mostrar información del cliente
cliente1.mostrar_info()

# Intentar hacer una reserva
reserva1 = Reserva(cliente1, habitacion1)
reserva1.confirmar_reserva()

# Verificar el estado de la habitación después de la reserva
habitacion1.mostrar_info()

# Intentar reservar la misma habitación otra vez
cliente2 = Cliente("Ana López", "0987654321")
reserva2 = Reserva(cliente2, habitacion1)
reserva2.confirmar_reserva()
