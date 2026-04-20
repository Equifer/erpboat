
# --- LÓGICA DE CONTROL NÁUTICO PRO V2 ---

input_text:
  motor_item_1_nombre:
    name: "Nombre Item Motor 1"
    initial: "Aceite Motor Volvo"
  motor_item_2_nombre:
    name: "Nombre Item Motor 2"
    initial: "Filtro Gasoil"
  motor_item_3_nombre:
    name: "Nombre Item Motor 3"
    initial: "Rodete Bomba"
  
  jarcia_item_1_nombre:
    name: "Nombre Cabo 1"
    initial: "Driza de Mayor"
  
  inv_item_1_nombre:
    name: "Nombre Item Stock 1"
    initial: "Bengalas Zona 2"

input_number:
  horas_motor_totales:
    name: "Horas Motor"
    min: 0
    max: 20000
    step: 0.1
    unit_of_measurement: "h"
  
  stock_item_1:
    name: "Cantidad Item 1"
    min: 0
    max: 100
    step: 1
  
  mantenimiento_progreso_1:
    name: "Progreso Item 1"
    min: 0
    max: 100
    unit_of_measurement: "%"

input_datetime:
  motor_item_1_fecha:
    name: "Fecha Mantenimiento 1"
    has_date: true
  inv_item_1_caducidad:
    name: "Fecha Caducidad 1"
    has_date: true

template:
  - sensor:
      - name: "Estado Stock Item 1"
        state: >
          {% if states('input_number.stock_item_1') | int < 2 %}
            REPONER
          {% else %}
            OK
          {% endif %}
