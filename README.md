# SolarVised · catálogo de ofertas de luz

Catálogo público de ofertas de electricidad **2.0TD con autoconsumo** (España) que usa el
comparador de tarifas de SolarVised. Cada instalación descarga `offers.json` una vez al día.

- Precios **sin impuestos**, tal y como los publica cada comercializadora.
- Se revisa **el día 1 de cada mes** (y cuando hay cambios conocidos).
- Cada oferta lleva la fuente (`source_url`) y la fecha de los precios (`prices_date`).
- Confirma siempre las condiciones con la comercializadora antes de contratar.

## Formato

```json
{
  "version": "AAAA-MM-DD",          // cambia en cada publicación
  "updated": "AAAA-MM-DD",
  "offers": [
    {
      "id": "repsol-solar-fijo",     // estable: minúsculas, números y guiones
      "company": "Repsol", "name": "Solar Precio Fijo",
      "energy_kind": "fixed",        // fixed (precio único) | 3p (punta/llano/valle)
      "e1": 0.1399, "e2": 0.1399, "e3": 0.1399,   // €/kWh punta, llano, valle
      "p1": 0.090137, "p2": 0.090137,             // €/kW·día punta y valle
      "surplus_mode": "simplificada",             // simplificada | bateria
      "surplus_price": 0.06,                      // €/kWh compensado
      "surplus_fee": 0,                           // €/kWh descontado (venta a mercado)
      "monthly_fee": 0,                           // €/mes (servicios, batería virtual…)
      "notes": "", "source_url": "https://…", "prices_date": "AAAA-MM-DD"
    }
  ]
}
```

Rangos que acepta la app (si una oferta se sale, se ignora esa oferta): energía 0,02–0,6 €/kWh,
potencia 0,0005–0,4 €/kW·día, excedente 0–0,3 €/kWh, cuota 0–30 €/mes.

La tarifa regulada (PVPC) y la referencia de venta a mercado las calcula la propia app con los
precios horarios de Red Eléctrica; no van en este archivo.

## Historial

Ver `CHANGELOG.md`.
