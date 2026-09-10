# Espejo de Corriente NMOS – Electrónica 2

## Descripción

Este repositorio contiene las simulaciones realizadas en **LTspice** correspondientes al análisis de un **espejo de corriente NMOS**, incluyendo el circuito base y diferentes configuraciones mediante el escalamiento de la relación **W/L** de los transistores.

El objetivo es analizar el comportamiento de las corrientes de salida y la resistencia de salida del espejo de corriente, comparando los resultados teóricos con los obtenidos mediante simulación.

---

## Parámetros utilizados

Los circuitos fueron diseñados utilizando los siguientes parámetros:

| Parámetro  |               Valor |
| ---------- | ------------------: |
| Tecnología | CMOS – NMOS Nivel 1 |
| VTH        |               0.7 V |
| Kp = μnCox |           200 μA/V² |
| λ          |            0.02 V⁻¹ |
| VDD        |               3.3 V |
| IREF       |               50 μA |
| Rs         |                1 kΩ |

Estos parámetros corresponden al modelo utilizado para realizar los cálculos teóricos del espejo de corriente.

---

# 4.2 – Espejo NMOS base (1×)

En la primera configuración se utiliza un espejo de corriente NMOS con una relación:

**(W/L)₂ = (W/L)₁**

Para el transistor de referencia se utilizan:

* **W₁ = 10 μm**
* **L₁ = 1 μm**
* **(W/L)₁ = 10**
* **IREF = 50 μA**
* **Rs = 1 kΩ**

El cálculo teórico proporciona:

* **VOV₁ ≈ 0.2236 V**
* **VGS₁ ≈ 0.9236 V**
* **VS₁ = 0.050 V**
* **VG ≈ 0.9736 V**

La transconductancia obtenida es aproximadamente:

**gm₁ ≈ 447.2 μS**

La resistencia intrínseca del transistor es:

**ro₁ ≈ 1 MΩ**

Considerando la resistencia de degeneración de fuente, se obtiene una resistencia de salida aproximada:

**Ro ≈ 1.448 MΩ**

Mientras que la simulación realizada en LTspice presenta aproximadamente:

**Ro(simulado) ≈ 1.488 MΩ**

Los resultados muestran una buena correspondencia entre el análisis teórico y la simulación.

---

# 4.2.2 – Espejo de corriente 2×

Para obtener una corriente de salida aproximadamente dos veces mayor que la corriente de referencia, se realiza un escalamiento de la relación W/L:

**(W/L)₂ = 2(W/L)₁**

Por lo tanto:

* **W₂ = 20 μm**
* **L₂ = 1 μm**
* **(W/L)₂ = 20**
* **Rs₂ = 500 Ω**

El escalamiento permite obtener idealmente:

**ID₂ = 2IREF**

Para:

**IREF = 50 μA**

se espera:

**ID₂ = 100 μA**

La simulación proporciona:

**ID₂(simulado) ≈ 100.71 μA**

La resistencia de salida calculada teóricamente es aproximadamente:

**Ro₂ ≈ 723.6 kΩ**

Mientras que la simulación entrega:

**Ro₂(simulado) ≈ 743.9 kΩ**

El resultado confirma el comportamiento esperado de un espejo de corriente con relación **2×**.

---

# 4.2.3 – Espejo de corriente 3×

En esta configuración se agrega una tercera rama al espejo de corriente, utilizando:

**(W/L)₃ = 3(W/L)₁**

Los valores utilizados son:

* **W₃ = 30 μm**
* **L₃ = 1 μm**
* **(W/L)₃ = 30**
* **Rs₃ ≈ 333.33 Ω**

La corriente esperada es:

**ID₃ = 3IREF**

Para una corriente de referencia de **50 μA**:

**ID₃ = 150 μA**

La simulación en LTspice entrega:

**ID₃(simulado) ≈ 151.07 μA**

El factor de multiplicación obtenido mediante simulación es:

**ID₃ / IREF ≈ 3.021 ≈ 3**

Por lo tanto, el circuito presenta el comportamiento esperado para un espejo de corriente con relación **3×**.

---

# Archivos del repositorio

En este repositorio se encuentran los archivos de simulación correspondientes a las diferentes configuraciones:

```text
4_2_Espejo_Corriente_MOS.asc
4_2_2_Espejo_Corriente_MOS.asc
4_2_3_Espejo_Corriente_MOS.asc
MOS_current_mirror.pdf
README.md
```

## Descripción de los archivos

### `4_2_Espejo_Corriente_MOS.asc`

Archivo de LTspice correspondiente a la simulación del **espejo de corriente NMOS base (1×)**.

### `4_2_2_Espejo_Corriente_MOS.asc`

Archivo de LTspice correspondiente a la configuración del espejo de corriente con **escalamiento 2×**.

### `4_2_3_Espejo_Corriente_MOS.asc`

Archivo de LTspice correspondiente a la configuración del espejo de corriente con **escalamiento 3×**.

### `MOS_current_mirror.pdf`

Documento que contiene el análisis, desarrollo matemático y cálculos teóricos utilizados para estudiar las diferentes configuraciones del espejo de corriente.

---

# Comparación de resultados

| Configuración | Corriente teórica | Corriente simulada |
| ------------- | ----------------: | -----------------: |
| 1×            |             50 μA |            ≈ 50 μA |
| 2×            |            100 μA |          100.71 μA |
| 3×            |            150 μA |          151.07 μA |

Los resultados obtenidos mediante LTspice presentan diferencias pequeñas respecto a los valores teóricos y mantienen las relaciones de corriente esperadas.

---

# Análisis

El comportamiento del circuito demuestra que es posible controlar la corriente de salida mediante el escalamiento de las dimensiones de los transistores.

Para la configuración **1×**, la corriente de salida mantiene aproximadamente el mismo valor que la corriente de referencia.

Para la configuración **2×**, el escalamiento de la relación W/L permite obtener una corriente de salida cercana al doble de la corriente de referencia.

Para la configuración **3×**, la tercera rama permite obtener una corriente cercana al triple de la corriente de referencia.

La utilización de resistencias de degeneración de fuente permite mantener la condición necesaria para que las diferentes ramas trabajen con tensiones de fuente adecuadas y contribuye al aumento de la resistencia de salida.

---

# Conclusiones

1. El espejo de corriente NMOS permite copiar una corriente de referencia hacia una o varias ramas de salida.

2. El escalamiento de la relación **W/L** permite controlar la magnitud de la corriente de salida.

3. Para la configuración **1×**, se obtiene una corriente de referencia de aproximadamente **50 μA**.

4. Para la configuración **2×**, se obtuvo una corriente simulada de aproximadamente **100.71 μA**, cercana al valor teórico de **100 μA**.

5. Para la configuración **3×**, se obtuvo una corriente simulada de aproximadamente **151.07 μA**, cercana al valor teórico de **150 μA**.

6. La degeneración de fuente mediante resistencias permite incrementar la resistencia de salida del espejo de corriente.

7. Los resultados obtenidos en LTspice presentan una buena concordancia con los cálculos teóricos.

---

# Software utilizado

* **LTspice**
* Modelo MOSFET de Nivel 1
* Análisis teórico de circuitos electrónicos

---

# Autores

**Miguel Angel Duarte Fajardo**
**David Wilches**

**Ingeniería Electrónica**
**Universidad Distrital**

---

## Nota

Los archivos `.asc` pueden abrirse directamente con **LTspice** para revisar el montaje, los componentes, los parámetros de los transistores y las simulaciones realizadas.
