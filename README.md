# Registro de Ventas con PDAs · Solana Devnet

Aplicación descentralizada (dApp) full-stack desarrollada en **Rust + Anchor** (smart contract) y **TypeScript + React** (frontend), conectada mediante **Codama** para gestionar negocios, clientes y ventas independientes mediante Program Derived Addresses (PDAs) en **Solana Devnet**.

* **Program ID (Devnet):** `J8tHbYREWv2jWC9Dr3J5wHzmgLYYjBvcwdGUDrQjiUnD`

---

## 1. Ruta elegida

**Ruta Guiada con Extensión Propia** sobre la arquitectura base *Registro de Ventas con PDAs* del Solana Engineering Track: Advanced (WayLearn).

Se partió del modelo jerárquico de cuentas independientes (`Registro → Cliente → Venta`) y se extendió tanto en el contrato inteligente en Rust como en el cliente TypeScript y la interfaz React para completar el ciclo de vida de los clientes y añadir operaciones de descuento sobre ventas activas.

---

## 2. Propósito

* Eliminar la necesidad de almacenar colecciones pesadas dentro de una sola cuenta separando cada entidad (`Registro`, `Cliente`, `Venta`) en su propia cuenta PDA.
* Garantizar la pertenencia y autorización criptográfica desde el contexto de Anchor (`has_one = owner` y validación de `seeds`) sin recorridos costosos.
* Permitir la recuperación de renta (*lamports*) al cerrar cuentas que ya no están activas (`close = owner`), manteniendo la integridad referencial y la secuencia histórica de identificadores (`id_counter`).

---

## 3. Configuración

### Requisitos previos
* **Node.js 22.12+** y **npm** (o entorno preconfigurado en GitHub Codespaces).
* Wallet de navegador compatible con Solana (**Solflare**) configurada en red **Devnet** con SOL de prueba.
* **Solana Playground** (`beta.solpg.io`) para compilación, despliegue (`Upgrade`) y exportación del IDL del programa Rust.

### Sincronización del contrato (IDL y cliente Codama)
El repositorio mantiene sincronizados el programa fuente, el IDL y el cliente generado:
1. El código fuente del smart contract reside en `programa/src/lib.rs` y está desplegado en Devnet bajo el Program ID `J8tHbYREWv2jWC9Dr3J5wHzmgLYYjBvcwdGUDrQjiUnD`.
2. El archivo `idl.json` y `src/config/programa.json` vinculan el despliegue activo con la aplicación.
3. Si se modifica `idl.json`, el cliente tipado se regenera mediante:
   ```bash
   npm run configurar:idl -- ./tmp-idl/idl.json --program-id J8tHbYREWv2jWC9Dr3J5wHzmgLYYjBvcwdGUDrQjiUnD
   npm run cliente



<img width="960" height="822" alt="Captura de pantalla 2026-11-22 000934" src="https://github.com/user-attachments/assets/6e4721af-a9c9-41b0-9d55-ae4cff0286a5" />
<img width="955" height="831" alt="Captura de pantalla 2026-11-22 001125" src="https://github.com/user-attachments/assets/d91b73f8-1277-4ab2-bdcd-162d921b0b26" />
<img width="933" height="917" alt="Captura de pantalla 2026-11-22 001101" src="https://github.com/user-attachments/assets/0cee3577-71ec-4b04-9b02-b213fa4779c4" />
<img width="932" height="728" alt="Captura de pantalla 2026-11-22 001043" src="https://github.com/user-attachments/assets/6e95393f-0805-4b62-b8f5-34e14530a9c2" />
<img width="956" height="912" alt="Captura de pantalla 2026-11-22 001016" src="https://github.com/user-attachments/assets/e7674187-95a5-4957-913a-695d55f20c65" />




