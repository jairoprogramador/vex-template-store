# Vex Template Store

Registro centralizado de plantillas para el ecosistema **vex**. Funciona como una base de datos liviana que mapea cada combinación de **nivel de arquitectura** y **nivel de costo** al repositorio **git** correspondiente.

## Propósito

Cuando **vex** necesita generar o inicializar un proyecto, consulta este repositorio para determinar qué plantilla utilizar en función de dos criterios:

| Criterio | Descripción |
|----------|-------------|
| **arquitectura** | Nivel de complejidad estructural. |
| **costo** | Nivel de presupuesto que influye en las variantes de la plantilla. |

De esta forma, cada proyecto arranca con la plantilla y configuraciones correctas según su escala.

## Estructura

El repositorio contiene un único archivo de datos:

```
templates.json   ← Mapa de plantillas
```

### Esquema de `templates.json`

```json
[
  {
    "level": 0,
    "cost": -1,
    "template": "https://github.com/user/repo"
  }
]
```

| Campo | Tipo | Valores | Descripción |
|-------|------|---------|-------------|
| `level` | `number` | `0`, `1`, `2` | Nivel de arquitectura. A mayor nivel, mayor complejidad estructural. |
| `cost` | `number` | `-1`, `0`, `1` | Variante de costo. `-1` bajo, `0` medio, `1` alto. |
| `template` | `string` | URL | URL del repositorio Git que contiene la plantilla a seguir. |

### Niveles de arquitectura

| Level | Descripción de arquitectura |
|-------|-------------|
| **0** | Básica — proyectos pequeños o prototipos. |
| **1** | Comercial — proyectos con estructura aceptable para pequeñas empresas. |
| **2** | Crítica — proyectos con estructura completa y alta escalabilidad. |

## Uso

**Vex** consume este archivo directamente desde el repositorio remoto. Para resolver la plantilla adecuada, realiza una búsqueda por `level` y `cost` y obtiene la URL del repositorio que debe clonarse como base del nuevo proyecto.


## Contribución

**Mejorar una plantilla existente:** Todos los repositorios de plantillas son públicos. Visita la URL de la plantilla que quieras mejorar, y abre un Pull Request directamente en ese repositorio. Cualquier mejora es bienvenida.


## Licencia

Este proyecto está bajo la licencia incluida en el archivo [LICENSE](LICENSE).
