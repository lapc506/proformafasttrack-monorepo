# **ProformaFastTrack**

## Agregador de Licitaciones de Proformas para Agencias Aduanales 🚀

Este proyecto es un **agregador de licitaciones** de facturas proforma para agencias aduanales, que conecta a comerciantes (importadores) con múltiples agencias aduanales. Permite a los comerciantes solicitar cotizaciones (licitaciones) de manera eficiente, y a las agencias aduanales responder con sus mejores ofertas. La plataforma está diseñada con una arquitectura modular y unificada, utilizando **Dart** para todo el *stack*.

---

### 1\. Arquitectura del Proyecto 🏛️

La arquitectura se compone de un solo *back-end* (aggregator) y tres *front-ends*, todos escritos en el lenguaje Dart para garantizar la consistencia y la reutilización de código. .

* **Backend (Aggregator):** Construido con **Alfred**, un *framework* web minimalista en Dart. Funciona como el cerebro del sistema, gestionando la lógica de negocio, el enrutamiento y la comunicación con la base de datos.  
* **Front-end para Importadores:** Un portal web desarrollado con **Flutter Web**, que permite a los comerciantes crear y enviar facturas proforma para licitación, además de supervisar el estado de sus solicitudes.  
* **Front-end para Agencias Aduanales:** Un portal web también en **Flutter Web**, donde las agencias reciben notificaciones de nuevas licitaciones, revisan los detalles de las proformas y envían sus ofertas.  
* **Front-end para Administración (CRUD):** Un panel de control desarrollado con **AngularDart**, diseñado para que los administradores puedan supervisar el flujo de trabajo, gestionar usuarios, y analizar el desempeño del sistema.

---

### 2\. Tecnologías Clave 🛠️

* **Lenguaje de Programación:** Dart  
* **Back-end Framework:** Alfred  
* **Bases de Datos:** MongoDB (NoSQL, ideal para JSON)  
* **Validación de Datos:** JSON Schema  
* **Front-end Frameworks:** Flutter Web y AngularDart

---

### 3\. Flujo de Trabajo 🔄

1. **Creación de Proforma (Importador):** El comerciante crea una nueva proforma rellenando un formulario en el portal de **Flutter Web**. La información se valida localmente y se envía como un objeto **JSON** al *back-end*.  
2. **Validación y Almacenamiento (Alfred):** El *back-end* de **Alfred** recibe el JSON, lo valida con un **JSON Schema** predefinido. Si la validación es exitosa, se añade un estado (`En Licitación`) y se guarda directamente en **MongoDB** sin necesidad de un ODM.  
3. **Licitación (Agencias Aduanales):** Las agencias aduanales son notificadas de la nueva licitación en su portal de **Flutter Web**. Consultan la información de la proforma y envían sus ofertas, que se almacenan en la base de datos.  
4. **Adjudicación y Monitoreo (Importador/Administrador):**  
   * El comerciante compara las ofertas recibidas en su portal y selecciona la mejor opción. El estado de la proforma cambia a `Adjudicada`.  
   * El administrador puede supervisar todo este flujo en tiempo real desde el panel **CRUD de AngularDart**, revisando el estado de cada proforma y las ofertas recibidas.

---

### 4\. Estructura de Proyectos 📂

El repositorio se organiza de la siguiente manera:

* `backend/`: Código fuente de la API de **Alfred**.  
* `importer_portal/`: Código fuente del *front-end* de comerciantes (**Flutter Web**).  
* `agency_portal/`: Código fuente del *front-end* de agencias (**Flutter Web**).  
* `admin_crud/`: Código fuente del *front-end* de administración (**AngularDart**).  
* `shared/`: Paquete Dart compartido que contiene los modelos de datos y las utilidades comunes para ser reutilizadas en todos los proyectos.

