# Ejercicio - Binding de Formularios en Vue

## Objetivo
Construir un formulario interactivo que muestre **two-way binding** con `v-model` en inputs, textarea, checkbox, radio y select.

---

## Decisiones técnicas

- `v-model.trim` en nombre  
- `v-model.number` en edad (0–120)  
- `v-model.lazy` en biografía  
- Radios → propiedad única `nivel`  
- Checkboxes → arreglo `intereses`  
- Select simple → objeto `{ code, name }`  
- Select múltiple → arreglo `tecnologias`  
- Validación mínima con `computed`  
- Vista previa en tiempo real + contador de caracteres  
- Envío → `alert(JSON.stringify(form))`


## Cómo correr el proyecto

1. Clonar el repositorio:
   ```bash
   git clone git@github.com:mauricio-chirino/binding-formulario.git
   cd binding-formulario