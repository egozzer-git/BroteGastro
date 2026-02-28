# Notas para el/la coder (v3 — incluye cálculos)

## Requisito nuevo
La Fase 3 **requiere** cálculos 2x2 y validación de resultados.

### Datos
- `data/attendee_survey_cases_controls.csv` contiene casos y controles.
- `expected_2x2_results.json` contiene a,b,c,d y OR esperado (con corrección) para exposiciones clave.

### Validación (recomendación)
1. El/la jugador(a) selecciona exposición y valor “expuesto”.
2. La app calcula a,b,c,d y OR (aplicando Haldane–Anscombe si hay ceros).
3. Al enviar Fase 3, el motor valida:
   - exposición correcta (beverage_tent_consumption == "Sí")
   - OR calculado dentro de ±10% del valor esperado.

### UI sugerida
- Selector de exposición
- Campo “valor expuesto” (por defecto "Sí"; para handwashing_access usar "Limitado")
- Tabla 2x2 renderizada + OR + CI95 + Fisher p
- Botón “Guardar en bitácora” que copia a,b,c,d y OR

## Archivos clave
- `game_config_individual.json`
- `clue_cards.json`
- `answer_key.json`
- `expected_2x2_results.json`
- `calculator_spec.md` (fórmulas y manejo de ceros)
