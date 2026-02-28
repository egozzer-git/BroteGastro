# Especificación calculadora 2x2 (v3)

## Entrada
- Dataset: `attendee_survey_cases_controls.csv`
- Variables:
  - `case_status`: "Caso" / "Control"
  - Exposición seleccionada (p.ej., `beverage_tent_consumption`)
  - Valor considerado "expuesto" (p.ej., "Sí"; o "Limitado" para `handwashing_access`)

## Salida (mínima)
1. Tabla 2x2: a, b, c, d
   - a = casos expuestos
   - b = casos no expuestos
   - c = controles expuestos
   - d = controles no expuestos
2. OR (odds ratio) y 95% CI
3. p-valor exacto de Fisher (si es posible)

## Manejo de celdas cero (OBLIGATORIO)
Si cualquier celda es 0, usar corrección de **Haldane–Anscombe**:
- a' = a + 0.5; b' = b + 0.5; c' = c + 0.5; d' = d + 0.5
- OR = (a'·d') / (b'·c')

## 95% CI (log OR)
- SE = sqrt(1/a' + 1/b' + 1/c' + 1/d')
- CI95 = exp( ln(OR) ± 1.96·SE )

## Validación en el juego (modo individual)
Para completar la Fase 3:
- El/la jugador(a) debe calcular la 2x2 para **carpa/barra** y reportar:
  - a,b,c,d (o una captura/registro que el motor pueda leer)
  - OR (con corrección si aplica)
  - Interpretación (1–2 líneas)

El motor de puntaje puede validar:
- que la exposición elegida es la correcta (carpa/barra)
- que el OR reportado cae dentro de un rango tolerado (±10%) del OR esperado en `expected_2x2_results.json`
