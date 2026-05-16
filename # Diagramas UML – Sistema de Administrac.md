# Diagramas UML – Sistema de Administración de Salones de Belleza y Barberías

## 1. Diagrama de Casos de Uso

```mermaid
flowchart LR
    A[Cliente] --> B((Solicitar servicio))
    A --> C((Consultar precios))
    A --> D((Pagar servicio))

    E[Empleado] --> F((Registrar servicio))
    E --> G((Gestionar inventario))
    E --> H((Actualizar precios))

    I[Administrador] --> J((Administrar empleados))
    I --> G
    I --> H
    I --> K((Generar reportes))
```

---

## 2. Diagrama de Clases

```mermaid
classDiagram

class Cliente {
  -idCliente
  -nombre
  -telefono
  +solicitarServicio()
  +realizarPago()
}

class Servicio {
  -idServicio
  -nombre
  -precio
  +mostrarPrecio()
}

class Empleado {
  -idEmpleado
  -nombre
  -cargo
  +registrarServicio()
  +gestionarInventario()
}

class Inventario {
  -idProducto
  -nombreProducto
  -cantidad
  +agregarProducto()
  +actualizarCantidad()
}

class Pago {
  -idPago
  -monto
  -fecha
  +procesarPago()
}

Cliente --> Servicio : solicita
Empleado --> Servicio : realiza
Empleado --> Inventario : administra
Cliente --> Pago : realiza
Pago --> Servicio : corresponde
```

---

## 3. Diagrama de Actividad

```mermaid
flowchart TD
    A[Inicio] --> B[Cliente llega al salón/barbería]
    B --> C[Consulta servicios y precios]
    C --> D[Selecciona servicio]
    D --> E[Empleado realiza servicio]
    E --> F[Registrar pago]
    F --> G[Actualizar inventario]
    G --> H[Fin]
```

---

## 4. Diagrama de Secuencia

```mermaid
sequenceDiagram
    participant Cliente
    participant Empleado
    participant Sistema
    participant Inventario

    Cliente->>Empleado: Solicita servicio
    Empleado->>Sistema: Registrar servicio
    Sistema->>Inventario: Verificar productos
    Inventario-->>Sistema: Productos disponibles
    Empleado->>Cliente: Realiza servicio
    Cliente->>Sistema: Realizar pago
    Sistema-->>Cliente: Confirmación de pago
```

---

## 5. Diagrama Entidad-Relación (ER)

```mermaid
erDiagram
    CLIENTE {
        int idCliente
        string nombre
        string telefono
    }

    SERVICIO {
        int idServicio
        string nombre
        float precio
    }

    EMPLEADO {
        int idEmpleado
        string nombre
        string cargo
    }

    INVENTARIO {
        int idProducto
        string nombreProducto
        int cantidad
    }

    PAGO {
        int idPago
        float monto
        date fecha
    }

    CLIENTE ||--o{ SERVICIO : solicita
    EMPLEADO ||--o{ SERVICIO : realiza
    EMPLEADO ||--o{ INVENTARIO : administra
    CLIENTE ||--o{ PAGO : realiza
```

---

## 6. Explicación General

Este sistema fue diseñado para ayudar en la administración de un salón de belleza y una barbería, permitiendo organizar de manera más fácil los servicios, los clientes, el inventario y los pagos.

