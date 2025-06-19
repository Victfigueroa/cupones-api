# Cupones API

Este proyecto consiste en una API REST creada con **Flask** que aplica descuentos mediante cupones y calcula el precio final con impuestos. Se incorporaron pruebas automatizadas con `pytest` y un flujo CI/CD usando **GitHub Actions** para prevenir regresiones en el código.

## Integrantes del Grupo 5

- Juan Villaman  
- Cristóbal de Jesus  
- Victor Figueroa  

## Objetivo del Proyecto

Implementar una lógica central para cupones de descuento, exponerla vía una API REST y protegerla mediante pruebas automatizadas. Se simula una regresión y se demuestra cómo detectarla con testing automatizado.

## Preguntas de Reflexión

**1. ¿Por qué fue difícil detectar la regresión sin pruebas?**  
Porque al eliminar el cupón "BIENVENIDA" en `cupones.py`, el sistema siguió funcionando sin fallos visibles. Solo las pruebas automatizadas detectaron que el descuento ya no se aplicaba como debía.

**2. ¿Cómo te ayuda el testing automatizado a mantener calidad?**  
Permite verificar automáticamente que la lógica principal sigue funcionando tras cada cambio. Por ejemplo, al ejecutar `pytest`, notamos que al eliminar un cupón, una prueba falló, detectando una regresión de forma inmediata.

**3. ¿Qué otras partes del código deberías cubrir con pruebas?**  
Además de los cálculos de cupones, sería clave probar la API Flask (`api.py`), validando respuestas HTTP, errores por entrada inválida y escenarios límite, para asegurar una cobertura más robusta del sistema completo.

**4. ¿Cómo evitarías errores similares en el futuro?**  
Manteniendo pruebas automatizadas en GitHub Actions, como hicimos con el workflow YAML. Así, cada push ejecuta pruebas y alerta si algo rompe la lógica, evitando que errores pasen desapercibidos.

---

## ¿Cómo detectamos la regresión y cómo la evitaríamos en el futuro?

Detectamos la regresión eliminando accidentalmente el cupón "BIENVENIDA" en el archivo `cupones.py`. Al ejecutar las pruebas con `pytest`, una de ellas falló, lo que nos alertó del error. Para evitarlo en el futuro, configuramos un workflow en GitHub Actions que ejecuta automáticamente las pruebas en cada push o pull request, garantizando que cualquier cambio en el código sea validado antes de integrarse.
