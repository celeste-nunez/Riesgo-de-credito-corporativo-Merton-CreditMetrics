# Riesgo-de-credito-corporativo-Merton-CreditMetrics
Riesgo de crédito de un portafolio corporativo internacional (Toyota, Alibaba, LVMH, BMW): Z de Altman, PD con modelo de Merton, EL, UL y CaR con y sin correlación, y CreditMetrics en Excel.

# Riesgo de crédito de un portafolio corporativo internacional

Medición del riesgo de crédito de un portafolio de deuda corporativa internacional mediante Z de Altman, modelo de Merton y CreditMetrics. Todo el modelo está construido en Excel con fórmulas.

## Empresas

Toyota Motor Corporation, Alibaba Group Holding Limited, LVMH Moët Hennessy Louis Vuitton SE y Bayerische Motoren Werke AG (BMW). Estados financieros de Yahoo Finance al 31/03/2026, convertidos a USD.

## Metodología

1. **Z de Altman.** Se calcula la Z de Altman con cinco razones financieras y se asigna una calificación crediticia equivalente con base en las tasas de incumplimiento de S&P Global Ratings (1981–2023).
2. **Modelo de Merton.** A partir de precios diarios de las acciones (desde abril de 2024), el valor de mercado del capital y el valor de los pasivos, se estiman el valor de los activos (V0), su volatilidad (σV) y la probabilidad de incumplimiento (PD).
3. **Medidas de riesgo.** Con la PD de Merton, LGD de 10% (Toyota), 15% (Alibaba), 12% (LVMH) y 17% (BMW), y la exposición igual al valor presente de la deuda, se calculan la Pérdida Esperada (EL) y la Pérdida No Esperada (UL) por emisor y para la cartera, con y sin correlación entre emisores (matriz de correlación de rendimientos logarítmicos de las acciones).
4. **CreditMetrics.** Portafolio de 3 bonos a 5 años con valor nominal de 100, calificados A- (cupón 7.5%), BBB- (cupón 9%) y B- (cupón 11%). Con la matriz de transición a un año y la curva de rendimientos del Treasury más spreads por calificación, se revalúa cada bono en cada posible calificación futura y se obtiene la distribución de su valor. Para el portafolio se construyen los 5,832 estados conjuntos (18 × 18 × 18).

## Resultados

### Z de Altman

| Empresa | Z Altman | Calidad Crediticia |
|---|---:|---|
| Toyota Motor | 1.82 | CCC |
| Alibaba Group | 7.24 | AAA |
| LVMH | 6.13 | BBB+ |
| BMW | 1.36 | CCC |

### Modelo de Merton

| | Toyota | Alibaba | LVMH | BMW |
|---|---:|---:|---:|---:|
| V0 (USD) | 608,906,703,628 | 428,020,092,878 | 266,181,245,107 | 181,756,279,878 |
| σV | 14.52% | 22.43% | 34.59% | 7.54% |
| PD | 0.03% | 0.03% | 0.03% | 0.03% |

### Medidas de riesgo

| | Toyota | Alibaba | LVMH | BMW |
|---|---:|---:|---:|---:|
| EL (USD) | 10,291,941 | 4,645,669 | 2,167,386 | 7,060,311 |
| UL (USD) | 594,116,359 | 268,177,599 | 125,115,338 | 407,566,114 |

| Cartera | ρ = 0 | ρ ≠ 0 |
|---|---:|---:|
| EL (USD) | 24,165,308 | 24,165,308 |
| ULP (USD) | 778,882,185 | 969,312,642 |
| CaR (USD) | 1,835,845,271 | 2,278,786,514 |

### CreditMetrics

| | A- | BBB- | B- |
|---|---:|---:|---:|
| Media | 104.85 | 123.20 | 96.08 |
| Desviación estándar | 4.80 | 10.41 | 27.94 |
| VaR Paramétrico (99.9%) | 14.83 | 32.18 | 86.34 |

| Portafolio | Valor |
|---|---:|
| VaR1-día | 235.77 |
| C-VaR1-día | 256.89 |
| VaR10-días | 745.57 |
| Capital | 2,236.71 |

## Estructura del archivo

| Hoja | Contenido |
|---|---|
| `3. Z Altman` | Razones financieras, Z de Altman y calificación equivalente |
| `3. Merton` | Valor y volatilidad de activos, PD y valor de la deuda |
| `3. comparación` | EL, UL y CaR de la cartera con y sin correlación |
| `6.Credit metrics` | Matriz de transición, revaluación de bonos y VaR del portafolio |

La presentación con los resultados está en `Presentacion-riesgo-de-credito.pdf`.

## Cómo usarlo

1. Descarga `Riesgo-de-credito-corporativo.xlsx`.
2. Ábrelo en Excel 365 (recomendado).

## Herramientas

Microsoft Excel (fórmulas matriciales, MMULT, distribución normal, CreditMetrics).

## Conclusiones y Recomendaciones

- Z Altman muestra resultados imprecisos para manufactureras.
- Las empresas muestran solidez según Merton.
- Asumir independencia subestima la exposición del fondo.
- Se debe mantener la reserva de capital de forma estricta para asegurar cobertura total en caso de crisis.
- Hedging: anticiparse a problemas reduciendo participación o comprando seguros para las empresas que el mercado percibe con mayor riesgo.
- Continua evaluación para poder reaccionar rápido al mercado.

## Autoría

Proyecto desarrollado por Celeste Núñez López, Kevin Rodríguez Pérez, Francisco Lince Domínguez y Alejandro Dorantes Quiroz.
