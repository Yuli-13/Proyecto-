<div align="center">

# 📦 Inventario Descentralizado en Solana
### Sistema de control de almacén, productos y movimientos con cuentas relacionadas, PDAs y cierre condicionado

![Solana](https://img.shields.io/badge/Solana-Devnet-9945FF?style=for-the-badge&logo=solana&logoColor=white)
![Anchor](https://img.shields.io/badge/Anchor-Framework-14F195?style=for-the-badge&logo=rust&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-IDL%20Client-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Next.js](https://img.shields.io/badge/Frontend-Wallet%20Adapter-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)
![Ruta](https://img.shields.io/badge/Acreditaci%C3%B3n-Proyecto%20Propio-FF6B35?style=for-the-badge)

<br />

<!-- Reemplaza esta ruta con una captura real de tu portada / dashboard en Devnet -->
<img src="./assets/portada-inventario.png" alt="Vista general del Sistema de Inventario en Solana Devnet" width="820" />

<br />

> **Ruta elegida:** Proyecto propio · **Temática:** Gestión de inventario (`Almacen`, `Producto`, `Movimiento`)  
> **Red de prueba:** Solana Devnet · **Ejecución:** Local / GitHub Codespaces conectado a Devnet

</div>

---

## 🎯 Propósito y Caso de Uso

Este proyecto implementa una aplicación descentralizada (**dApp**) de **gestión de inventario** sobre **Solana**, diseñada para demostrar el dominio de cuentas relacionadas mediante **PDAs (*Program Derived Addresses*)**, validación estricta de permisos, lógica de negocio en Rust/Anchor y consumo desde un frontend conectado a *wallet* usando el **IDL** generado.

En lugar de utilizar un modelo de registro de ventas, el dominio modela un flujo operativo de inventario con tres cuentas encadenadas:

* 🏬 **`Almacen` (Cuenta raíz):** Pertenece a una wallet (`autoridad`), almacena el nombre del almacén y lleva el conteo de productos activos.
* 📦 **`Producto` (Cuenta vinculada al almacén):** Representa un artículo con `sku`, `nombre`, `stock_actual`, `precio_unitario` y contador de movimientos.
* 🔄 **`Movimiento` (Cuenta histórica por operación):** Registra cada entrada o salida de stock asociada a un producto, junto con su `cantidad` y `timestamp`.

---

## 🧩 Arquitectura de Cuentas y PDAs

```mermaid
├── programs/inventario_solana/src/lib.rs   # Programa en Rust (Anchor): PDAs, reglas y cierre
├── target/idl/inventario_solana.json       # IDL generado por Anchor
├── client/inventarioClient.ts              # Cliente TypeScript coherente con el IDL
├── components/InventarioDashboard.tsx      # Frontend con wallet adapter y manejo de errores
└── assets/                                 # Capturas de pantalla y evidencias visuales
