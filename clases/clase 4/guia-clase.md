# Guía para explicar el ejemplo CSS en clase

## 1. Introducción al ejemplo

Comenzar mostrando el resultado final del ejemplo para que los estudiantes vean lo que van a crear. Explicar que este ejemplo integra todos los conceptos que aprenderán en la clase de hoy: selectores, formas de incorporar CSS, especificidad y atributos básicos.

## 2. Estructura de archivos

Mostrar la estructura de archivos necesaria:
- `index.html` - Documento HTML con la estructura y contenido
- `styles.css` - Hoja de estilos externa con todas las reglas CSS

## 3. Formas de incorporar CSS

### 3.1. CSS en línea
```html
<p>CSS nos permite dar <span style="color: red; font-weight: bold;">estilo</span> a nuestras páginas web.</p>
```

**Puntos clave:**
- Se aplica directamente a un elemento usando el atributo `style`
- Tiene la mayor especificidad
- No es reutilizable
- Mezcla contenido y presentación
- Útil para estilos únicos y específicos

### 3.2. CSS interno
```html
<head>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
        }
        
        h2 {
            color: purple;
        }
    </style>
</head>
```

**Puntos clave:**
- Se define dentro del documento HTML usando la etiqueta `<style>`
- Se aplica solo al documento actual
- Útil para páginas con estilos únicos
- Mejor que el CSS en línea, pero no ideal para sitios con múltiples páginas

### 3.3. CSS externo
```html
<head>
    <link rel="stylesheet" href="styles.css">
</head>
```

**Puntos clave:**
- Archivo separado que se vincula al HTML
- La mejor práctica para la mayoría de los sitios web
- Permite reutilizar estilos en múltiples páginas
- Mantiene separados el contenido y la presentación
- Facilita el mantenimiento del código

## 4. Selectores básicos

Mostrar ejemplos de cada tipo de selector en el archivo `styles.css`:

### 4.1. Selector universal
```css
* {
    box-sizing: border-box;
}
```

**Puntos clave:**
- Afecta a todos los elementos de la página
- Útil para restablecer estilos o aplicar propiedades globales
- Tiene la menor especificidad

### 4.2. Selector de etiqueta
```css
body {
    background-color: #f5f5f5;
    line-height: 1.6;
}

header {
    background-color: #3498db;
    color: white;
    padding: 20px;
    text-align: center;
}
```

**Puntos clave:**
- Selecciona todos los elementos de un tipo específico
- Cambia el estilo de manera consistente para ese tipo de elemento
- Especificidad baja

### 4.3. Selector de clase
```css
.destacado {
    background-color: #f1c40f;
    padding: 10px;
    border-radius: 5px;
    font-weight: bold;
}

.caja {
    background-color: white;
    border-radius: 8px;
    padding: 15px;
    margin: 20px auto;
    width: 80%;
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}
```

**Puntos clave:**
- Se indica con un punto `.` seguido del nombre de la clase
- Puede aplicarse a múltiples elementos
- Permite reutilizar estilos
- Mayor especificidad que los selectores de etiqueta

### 4.4. Selector de ID
```css
#titulo-principal {
    font-size: 2.5rem;
    color: #2c3e50;
    text-align: center;
    margin-top: 20px;
}
```

**Puntos clave:**
- Se indica con un numeral `#` seguido del ID
- Debe ser único en la página
- Tiene mayor especificidad que las clases
- Útil para elementos que solo aparecen una vez

### 4.5. Selectores combinados
```css
.seccion-principal h2 {
    color: #e74c3c;
    text-align: center;
    margin-bottom: 20px;
}

.nav-list a {
    text-decoration: none;
    color: white;
    font-weight: bold;
    padding: 5px 10px;
    border-radius: 3px;
    transition: background-color 0.3s;
}
```

**Puntos clave:**
- Seleccionan elementos basados en su relación con otros
- Aumentan la especificidad
- Permiten estilos más dirigidos sin necesidad de añadir clases adicionales

## 5. Especificidad, herencia y cascada

### 5.1. Especificidad
```css
/* Estilo general */
.caja {
    border: 1px solid #ddd;
}

/* Estilo más específico */
.seccion-principal .caja {
    border-left: 4px solid #3498db;
}
```

**Demostración:**
- Mostrar cómo la segunda regla, más específica, prevalece para el borde izquierdo
- Explicar la jerarquía: inline > ID > clase > etiqueta

### 5.2. Herencia
```css
main {
    color: #333;
    padding: 20px;
}
```

**Demostración:**
- Mostrar cómo todos los elementos dentro de `<main>` heredan el color de texto #333
- Explicar qué propiedades se heredan (color, font-family) y cuáles no (padding, margin)

### 5.3. Cascada
```css
/* Si hubiera dos reglas para el mismo selector */
h2 { color: blue; }
h2 { color: red; } /* Esta es la que se aplicaría */
```

**Puntos clave:**
- A igual especificidad, gana la última regla declarada
- Comparar con el CSS interno vs externo en el ejemplo (color purple vs #e74c3c para h2)

## 6. Atributos básicos de CSS

### 6.1. Color
```css
#titulo-principal {
    color: #2c3e50;
}

.destacado {
    background-color: #f1c40f;
}

/* Mostrar otros ejemplos */
.ejemplo-color {
    color: rgb(255, 0, 0);          /* RGB */
    background-color: rgba(0, 0, 255, 0.5); /* RGBA con transparencia */
}
```

**Puntos clave:**
- Diferentes formas de especificar colores: nombres, hex, rgb/rgba
- Diferencia entre `color` (texto) y `background-color` (fondo)

### 6.2. Tamaño y unidades de medida
```css
#titulo-principal {
    font-size: 2.5rem;  /* Relativo a la raíz */
}

.caja {
    width: 80%;         /* Porcentaje del padre */
    padding: 15px;      /* Píxeles (absolutos) */
}

.ancho {
    max-width: 800px;   /* Limitación máxima */
}
```

**Puntos clave:**
- Unidades absolutas: px, pt, cm
- Unidades relativas: %, em, rem, vh, vw
- Cuándo usar cada una (responsive design, accesibilidad)

## 7. Pseudoclases y efectos

```css
.nav-list a:hover {
    background-color: #2980b9;
}
```

**Demostración:**
- Mostrar cómo cambia el estilo de los enlaces al pasar el cursor
- Explicar otras pseudoclases comunes: `:active`, `:focus`, `:visited`

## 8. Modificación en vivo

Para demostrar el poder de CSS y cómo los cambios se reflejan instantáneamente:

1. Abrir las herramientas de desarrollo del navegador (F12)
2. Modificar algunos estilos en vivo:
   - Cambiar colores de fondo
   - Ajustar tamaños
   - Añadir bordes o sombras

## 9. Ejercicios prácticos

Dar a los estudiantes tiempo para experimentar con el código:

### Ejercicio 1:
- Cambiar el color de fondo del `header` a `#16a085`
- Modificar el color del texto del título principal a `#fff`

### Ejercicio 2:
- Añadir un borde inferior a los enlaces de navegación
- Cambiar el efecto hover para que modifique el color del texto en lugar del fondo

### Ejercicio 3:
- Crear una nueva clase `.importante` y aplicarla a un párrafo
- Darle un estilo distintivo con borde, color y padding

## 10. Conclusión

Resumir los conceptos clave aprendidos:
- Las tres formas de incorporar CSS
- Los cuatro selectores básicos
- Especificidad, herencia y cascada
- Atributos básicos de color y tamaño

Destacar la importancia de la práctica continua y animar a los estudiantes a experimentar con sus propios proyectos.