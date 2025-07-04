# Restricciones de Estilo y Maquetación

Para mantener coherencia y facilitar el mantenimiento de los proyectos, se definen las siguientes restricciones de estilo:

---

## 1. **Evitar CSS Tradicional**

- **No escribir estilos CSS en archivos separados (`.css`) ni en etiquetas `<style>`.**
- **Evita usar clases personalizadas que requieran definir reglas CSS a mano.**

> **¿Por qué?**  
> El uso excesivo de CSS tradicional puede generar inconsistencias, dificultar el trabajo colaborativo y complicar la migración o escalabilidad de los componentes.

---

## 2. **Usar Tailwind CSS**

- **Prioriza siempre la utilización de Tailwind CSS para todos los estilos.**
- Utiliza las [clases utilitarias de Tailwind](https://tailwindcss.com/docs/utility-first) para la maquetación, espaciado, tipografía, colores y responsive design.

**Ejemplo:**

```jsx
<div className="bg-white rounded-xl p-4 shadow-md">
  <h2 className="text-xl font-bold mb-2">Título</h2>
  <p className="text-gray-600">Contenido aquí...</p>
</div>
```

## 3. Maquetación con Flexbox (Tailwind)
Utiliza Flexbox a través de las clases de Tailwind (flex, flex-row, flex-col, items-center, justify-between, etc.) para la disposición de elementos.

Ejemplo:

```html
<div className="flex items-center justify-between">
  <span>Elemento A</span>
  <span>Elemento B</span>
</div>
```

## 4. Resumen

    * ✅ SÍ: Tailwind + Flexbox con clases utilitarias.

    * ❌ NO: CSS tradicional, reglas custom en archivos .css o etiquetas <style>.

## 5. Recursos útiles
[Documentación oficial de Tailwind CSS](https://tailwindcss.com/docs/installation/using-vite)

[Guía de Flexbox con Tailwind](https://tailwindcss.com/docs/place-items)