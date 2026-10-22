Hidráulica de Tuberías en Serie · Calculadora Integral v2.0
Herramienta de cálculo, diseño y diagnóstico de sistemas de tuberías a presión.
Un solo archivo HTML, sin instalación, sin servidor y sin conexión a internet: todo el cálculo hidráulico se ejecuta en el navegador con ecuaciones explícitas y solución numérica verificada.

Aplicación de ingeniería desarrollada a partir del texto guía Mecánica de fluidos (Sandoval, 2018, Universidad de América), madurada como herramienta de uso profesional: balances de energía, Darcy–Weisbach con Colebrook–White exacto, método de longitud equivalente de Crane, NPSH, curvas de bomba y leyes de semejanza.

Tabla de contenido
Qué resuelve
Para quién es
Módulos de cálculo
Inicio rápido: tres escenarios reales
Fundamento físico y modelos implementados
Base de datos técnica
Precisión, validación y trazabilidad
Buenas prácticas de uso
Interfaz y flujo de trabajo
Datos, privacidad y persistencia
Estructura del archivo y extensión
Limitaciones y uso responsable
Hoja de ruta
Glosario de símbolos
Cómo citar
Créditos y licencia
1. Qué resuelve
Los cuatro problemas clásicos del flujo en conductos cerrados, más el diagnóstico completo de la instalación:

Problema	Se conoce	Se busca	Aplicación típica
Clase I	Caudal, geometría, presiones y cotas	Carga de bomba y potencia	Sustitución o especificación de equipos de bombeo
Clase II	Energía disponible (presión + cota + bomba)	Caudal circulante	Verificación de instalaciones existentes, auditorías energéticas
Clase III	Caudal exigido y pérdida admisible	Diámetro mínimo y selección comercial	Diseño de líneas nuevas, ampliaciones, re-potenciación
NPSH	Instalación de aspiración y NPSH<sub>r</sub>	Margen de cavitación y caudal límite	Diagnóstico de ruido, vibración y erosión de rodetes
A ello se suman dos módulos de apoyo (curva de bomba con leyes de semejanza y utilidades de válvulas/capacidad) y un módulo de datos técnicos con el ábaco de Moody generado numéricamente.

Valor diferencial: no es una calculadora de una línea. Modela trenes de tubería en serie con N tramos (cada uno con diámetro, longitud, material y accesorios propios), entrega el desglose completo de pérdidas, las presiones en bridas de succión y descarga, las líneas de energía y piezométrica, y un análisis técnico con semáforos que señala riesgos de cavitación, erosión, sedimentación, sobredimensionamiento y régimen incierto.

2. Para quién es
Ingeniería de diseño (mecánica, civil, química, ambiental, agroindustrial): dimensionamiento de líneas de impulsión, redes de proceso, sistemas contra incendio, riego, HVAC y agua potable.
Ingeniería de planta y mantenimiento: verificación de bombas y líneas existentes, diagnóstico de cavitación, evaluación de ampliaciones de caudal o cambios de fluido.
Auditoría energética: cuantificación de la potencia absorbida, reparto fricción/accesorios, diámetro económico y efecto de variar velocidad de giro o recortar rodete.
Docencia y formación: los cuatro módulos reproducen paso a paso el cálculo de cursos de mecánica de fluidos e hidráulica, con la trazabilidad completa (Re, f, Le/D, ΣK, h<sub>f</sub>, h<sub>m</sub>) y bibliografía de cada correlación.
Interventoría y revisión de diseños: contraste rápido e independiente de memorias de cálculo y de la selección de equipos.
Sectores: agua y saneamiento, procesos químicos y alimentarios, petróleo y derivados, minería, generación, edificación e infraestructura.

3. Módulos de cálculo
3.1 Clase I — Potencia de bombeo
Balance de energía entre la fuente y el destino; multitramo en succión y descarga.

Salidas: h<sub>A</sub>, pérdida total Σh<sub>L</sub> (fricción y locales por separado), potencia hidráulica, al freno, eléctrica y con margen de diseño, presión en bridas, NPSH<sub>a</sub> estimado, régimen y Re, tamaño comercial de motor sugerido.
Gráficas: esquema del sistema y EGL/HGL en función de la longitud desarrollada.
Análisis automático: velocidades, vacío en succión, NPSH, reparto de pérdidas, erosión (> 5 m/s) y motor normalizado.
3.2 Clase II — Caudal circulante
Iguala la energía disponible con las pérdidas y resuelve H_bomba(Q) = ΔH_estático + Σh_L(Q).

Bomba opcional, con dos modelos: cabeza constante o curva H = H₀[1 − (Q/Q_máx)²].
Salidas: Q en 4 unidades, verificación del residuo |Δh|, velocidades, f, Re e iteraciones.
Gráfica: curva del sistema, curva de la bomba y punto de operación.
3.3 Clase III — Diseño de diámetro
Bisección sobre D para la pérdida admisible, con selección comercial razonada.

Salidas: D mínimo teórico, velocidad y régimen a ese diámetro, D económico por criterio de velocidad, tabla de alternativas comerciales (V, Re, h<sub>L</sub>, % de uso de la pérdida admisible y estado), notas de selección (opción inferior que no cumple, clase de presión, material).
Gráfica: h<sub>L</sub>(D) contra la pérdida admisible.
3.4 NPSH — Cavitación
NPSHa = (p_atm + p_tanque)/γ + (Z_a − Z_b) − h_L,succión − p_v/γ, comparado con NPSH<sub>r</sub> × factor de seguridad.

Salidas: NPSHa, margen, caudal máximo admisible, balance de succión pieza por pieza.
Propuestas correctivas cuantificadas (elevar tanque, presurizar, aumentar Ø, descender bomba, simplificar accesorios, enfriar fluido, limitar caudal, cambiar bomba).
Gráficas: esquema de aspiración y curva NPSH<sub>a</sub>(Q) con el objetivo.
3.5 Bomba & Sistema (nuevo)
Punto de operación bomba–sistema, η en el punto, potencia absorbida, posición respecto al BEP.
Velocidad específica N<sub>s</sub> = 3.65·n·√Q / H<sup>0.75</sup> (n en rpm, Q en m³/s, H en m) y clasificación de la máquina.
Leyes de semejanza con nueva velocidad de giro y recorte de rodete; además del punto homólogo, calcula el nuevo punto de operación real sobre la curva del sistema (el error conceptual más común al aplicar afinidad).
Curvas H(Q) de la bomba original y modificada, sistema y carga estática.
3.6 Herramientas de diseño (nuevo)
Pérdida local de un accesorio (K o Le/D, h<sub>m</sub>, Δp en kPa/psi).
Longitud equivalente de un conjunto de accesorios (Le y ΣK).
Capacidad y diámetro económico por servicio (succión, descarga, gravedad, proceso, larga conducción) con tabla comercial.
Conversor de unidades en 10 magnitudes.
3.7 Datos técnicos
Ábaco de Moody calculado (no imagen) con ubicación del punto de operación; catálogo de accesorios con buscador; tabla de materiales; propiedades de fluidos; familias comerciales de tubería con pestañas; criterios de velocidad recomendados.

4. Inicio rápido: tres escenarios reales
Escenario A — «Tengo una bomba: ¿qué caudal entrega y se va a cavitar?»
Panel de fluido: seleccione el fluido real (ρ, μ y P<sub>v</sub> quedan cargados).
Clase II: introduzca presiones, cotas y el tren de tuberías (tramos + accesorios); active la bomba con su curva (H₀ y Q a H = 0, tomados del catálogo).
Calcular caudal → Q de operación, velocidad y f por tramo, curva del sistema.
Copie ese Q en NPSH → margen de cavitación y caudal máximo admisible.
Si el margen es negativo, el módulo entrega la lista de acciones con el valor exacto que resuelve el déficit.
Escenario B — «Necesito una línea nueva para X m³/h con pérdida admisible Y m»
Clase III: caudal, presiones/cotas extremas y la pérdida admisible (se calcula sola).
Elija familia comercial (acero Sch 40, PVC PN16, cobre K…) y material.
Calcular diámetro → D mínimo teórico + tabla de alternativas con V, h<sub>L</sub> y estado.
Use Herramientas → capacidad para contrastar con el criterio de velocidad del servicio.
Con el diámetro elegido, pase a Clase I para dimensionar la bomba y el motor.
Escenario C — «Quiero reducir el consumo energético de una instalación existente»
Clase I con la instalación actual: observe el reparto fricción/accesorios y la potencia.
Bomba & Sistema: mueva la velocidad de giro (variador) o el recorte de rodete y lea el nuevo punto de operación y la potencia (P ∝ n³).
Clase III con el nuevo caudal: evalúe el diámetro que minimiza el costo total (menor fricción frente a mayor inversión).
Exporte cada variante en CSV para el expediente.
Atajo: todos los campos aceptan unidades en línea (L/s, m³/h, GPM, psi, bar, m c.a., in, mm…). Escriba el valor, elija la unidad y continúe; internamente todo se convierte a SI.

5. Fundamento físico y modelos implementados
5.1 Ecuación de gobierno
Balance de energía (Bernoulli generalizado) entre dos secciones, con pérdidas:

text

p₁/γ + Z₁ + α₁V₁²/(2g) + h_A = p₂/γ + Z₂ + α₂V₂²/(2g) + Σh_L
Con depósitos abiertos (α = 1, V₁ ≈ V₂ ≈ 0):

text

h_A = (p₂ − p₁)/γ + (Z₂ − Z₁) + Σh_L
En un sistema en serie el caudal es único y las pérdidas se suman:
Σh_L = Σ [ fᵢ·(Lᵢ/Dᵢ) + Kᵢ ]·Vᵢ²/(2g).

5.2 Pérdidas distribuidas — Darcy–Weisbach
text

h_f = f·(L/D)·V²/(2g)
Régimen	Modelo
Laminar (Re < 2 300)	f = 64/Re
Turbulento	Colebrook–White resuelta por Newton–Raphson: 1/√f = −2·log₁₀(ε/3.7D + 2.51/(Re√f))
Transición (2 300 < Re < 4 000)	Se calcula con Colebrook y se advierte la incertidumbre del modelo
Semilla: Swamee–Jain explícita; convergencia por diferencia finita analítica de la función, tolerancia 1×10⁻¹³ (residuo típico < 1×10⁻¹⁵).

5.3 Pérdidas localizadas — método de Crane (TP-410)
text

h_m = K·V²/(2g)          K = (Le/D)·f_T
f_T = 0.25·[log₁₀(ε/3.7D)]⁻²
f_T es el factor de tubería completamente rugosa del tramo (no el f de Colebrook del régimen real): es la base correcta del método de longitud equivalente. Los accesorios ingresados con K directo (entradas, salidas, instrumentos) se suman sin conversión.

5.4 NPSH y cavitación
text

NPSH_a = (p_atm + p_tanque)/γ + (Z_a − Z_b) − h_L,succión − p_v/γ
Criterio: NPSH_a ≥ NPSH_r · FS      (FS = 1.1 estándar; 1.3 fluidos volátiles; HI 9.6.1)
5.5 Bombas
text

H(Q) = H₀·[1 − (Q/Q_máx)²]        η(Q) = η_máx·[1 − 0.55·(Q/Q_BEP − 1)²]
P_h = ρgQH          P_freno = P_h/η
Afinidad:  Q ∝ n·D      H ∝ n²·D²      P ∝ n³·D³
Velocidad específica:  N_s = 3.65·n·√Q / H^0.75
5.6 Métodos numéricos
Incógnita	Método	Criterio
f (turbulento)	Newton–Raphson sobre Colebrook	|Δf| < 1×10⁻¹³
Q (Clase II)	Bisección sobre F(Q) = H_bomba(Q) − H_sistema(Q) con expansión de intervalo	200 iteraciones / |ΔQ| relativo < 1×10⁻¹²
D (Clase III)	Bisección sobre h_L(D) − h_permisible	200 iteraciones, D ∈ [1 mm, 12 m]
Q máximo por NPSH	Bisección sobre NPSH_a(Q) − objetivo	120 iteraciones
5.7 Propiedades del fluido
ρ, μ y P<sub>v</sub> por fluido; corrección opcional de μ por temperatura con la ecuación de Andrade:
μ(T) = μ₂₉₃·exp[B·(1/T − 1/293.15)], con B propio de cada fluido. Los resultados se recalculan con la viscosidad corregida (ν = μ/ρ).

5.8 Supuestos del modelo
Flujo permanente y unidimensional; fluido newtoniano e incompresible; conducto lleno y de sección constante en cada tramo; α = 1; accesorios sin interferencia mutua (sin efectos de proximidad); entrada y salida contabilizadas como accesorios (K); depósitos abiertos a la atmósfera salvo que se indique presión manométrica.

6. Base de datos técnica
Base	Contenido	Fuente
Tuberías	8 familias · 126 tamaños con DE, espesor y DI verificados (DI = DE − 2e)	ASME B36.10M, ASTM B88, AWWA C900, ISO 1452 / EN 12201
Accesorios	53 ítems en 7 categorías con Le/D o K, más K/Le-D personalizado	Crane TP-410, Mott, White
Materiales	18 rugosidades absolutas (acero, galvanizado, fundición, concreto, PVC, PE, PRFV, cobre, vidrio…)	Mott, White, Crane
Fluidos	20 fluidos con ρ, μ, P<sub>v</sub> y coeficiente B de Andrade (agua 10–100 °C, agua de mar, glicol, diésel, gasolina, keroseno, crudo, SAE 10/30, etanol, metanol, glicerina, leche, aire)	Perry, Incropera, tablas NIST
Criterios	Velocidades recomendadas por servicio y tamaños comerciales de motor (0.37–355 kW)	Práctica de diseño / HI
Familias de tubería incluidas: Acero Sch 40 · Acero Sch 80 · Hierro galvanizado Sch 40 · PVC-U PN16 · PVC-U PN10 · Cobre tipo K · Cobre tipo L · PE 100 SDR 11 (además de Personalizado).

7. Precisión, validación y trazabilidad
Prueba de reproducción manual. Caso de referencia: agua 20 °C, Q = 500 L/min, 2" Sch 40 (DI 52.48 mm), succión 5 m + descarga 20 m, Δz = 10 m, p₂ = 4 atm, 4 accesorios por línea, ε = 0.046 mm.

Magnitud	Resultado de la app	Comprobación
Velocidad en ambos tramos	3.85 m/s	V = Q/A = 0.00833/0.002163
h<sub>f</sub> succión + descarga	7.40 m	f·(L/D)·V²/2g, f = 0.0205
h<sub>m</sub> (locales)	3.61 m	ΣK·V²/2g con K = (Le/D)·f_T
Carga de bomba h<sub>A</sub>	62.41 m	51.40 m estáticos + 11.01 m de pérdidas
Potencia eléctrica con margen 10 %	8.30 kW	ρgQh_A/η_b/η_m × 1.10
Controles numéricos internos.

Residual de Colebrook–White < 1×10⁻¹⁵ en los puntos de verificación (Re 10⁴–10⁷, ε/D 0–0.05).
Laminar exacto: f = 64/Re (Re = 1 000 → f = 0.064000).
Solver de caudal: residuo típico |Δh| ≈ 1×10⁻¹¹ m en ~36 iteraciones.
Coherencia física: la pérdida crece monótonamente con Q y decrece con D; el NPSH<sub>a</sub> decrece con Q y con la rugosidad.
Pruebas automatizadas ejecutadas. Los 6 módulos y los casos límite (Q = 0, sin energía disponible, red sin tramos, bomba sin intersección, diámetro fuera de catálogo, régimen laminar con aceite viscoso, agua a 80 °C) devuelven resultados o mensajes de error controlados, sin valores NaN/Infinity y sin excepciones. Revisión visual en navegador a 1 440, 1 200 y 390 px.

Trazabilidad. Cada resultado se muestra con sus intermedios (f, f<sub>T</sub>, Re, Le/D, ΣK, h<sub>f</sub>, h<sub>m</sub>) y cada dato de tabla lleva su referencia; la sección Bibliografía del aplicativo lista las fuentes primarias.

8. Buenas prácticas de uso
Introduzca el fluido real. Viscosidad y presión de vapor cambian radicalmente el resultado (un aceite SAE 30 puede operar en laminar donde el agua es turbulenta; el agua a 80 °C reduce el NPSH disponible en metros).
Modele todos los accesorios de la succión. La aspiración es donde se define el NPSH y donde la pérdida local pesa más.
No use un solo diámetro por comodidad. Un tramo mayor en la descarga o en la succión suele ser la intervención con mejor retorno económico.
Deje margen de diseño (10–20 % en potencia) y recuerde el envejecimiento: la rugosidad crece con la incrustación y la pérdida con el cuadrado del caudal.
Contraste siempre dos criterios en el diámetro: pérdida admisible (Clase III) y velocidad recomendada (Herramientas). El óptimo económico está donde ambos coinciden.
NPSH: exija margen, no igualdad. NPSH<sub>a</sub> = NPSH<sub>r</sub> es operación al límite de cavitación, no un diseño.
Al variar la velocidad de giro o recortar el rodete, el punto de operación se desplaza sobre la curva del sistema: use el nuevo punto calculado, no solo la ley de afinidad aplicada al punto original.
Registre el caso. Guarde el archivo del caso (JSON) y exporte el CSV junto con la memoria de cálculo; así el resultado es reproducible y auditable.
9. Interfaz y flujo de trabajo
Barra lateral: navegación por módulos + panel de fluido global (ρ, μ, P<sub>v</sub>, p<sub>atm</sub>, corrección de μ por temperatura) con derivados en vivo (ν, γ, densidad relativa, P<sub>v</sub>/γ).
Barra superior: ruta de la sección, guardar/cargar caso, impresión y sello del modelo de pérdidas.
Tarjetas de tramo: cada tramo resume D · ε · L y Le/D · ΣK · n.º de accesorios; su lista de accesorios es buscable por categoría.
Resultados: cifra principal, verificaciones en formato monoespaciado, tablas de desglose, análisis con semáforos y gráficas vectoriales.
Acciones: Enter calcula, Esc cierra el menú móvil, Imprimir / PDF genera una hoja con estilos de impresión.
Responsive: diseño probado en escritorio, tableta y móvil (menú deslizante).
10. Datos, privacidad y persistencia
Cero telemetría y cero peticiones de red. No hay CDN, fuentes externas, analítica ni llamadas a servidores: el archivo funciona en un equipo aislado, en una USB o dentro de un iframe sin red.
Guardar caso escribe en localStorage del navegador (clave hidraulica-serie-v2); si el almacenamiento no está disponible, descarga un JSON del caso.
Cargar caso recupera de localStorage o abre un archivo JSON previamente guardado.
Exportar CSV genera el reporte del módulo activo (fluido, resumen de resultados y tabla de tramos) listo para Excel.
11. Estructura del archivo y extensión
El entregable es un único 
simulador-tuberias-serie-v2.html
 (≈ 220 kB) con cuatro bloques <script> y CSS propio:

text

├── <style>        sistema de diseño (sin frameworks)
├── HTML          9 secciones + barra lateral + panel de fluido
└── <script>  1   datos y utilidades: UNITS, FLUIDS, MATERIALS, PIPE_FAMILIES, ACCESSORIES,
                  darcyF(), fFullyRough(), pipeLoss(), getFluid()
            2   interfaz: navegación, tramos, accesorios, tablas, Moody, conversor, persistencia
            3   motor: Clase I / II / III + gráficas (esquema, EGL–HGL, curvas)
            4   motor: NPSH, bomba–sistema, herramientas e inicialización
Para ampliar la base de datos basta editar los arreglos de la capa 1 (no hay que tocar el motor):

JavaScript

// Añadir un fluido
FLUIDS.miFluido = { name:'Mi fluido (25 °C)', rho:1010, mu:1.5e-3, pv:3.2, B:2500 };

// Añadir un accesorio (Le/D o K)
ACCESSORIES.push({ cat:'Válvulas', name:'Mi válvula', type:'LeD', val:50, ref:'Proveedor' });

// Añadir una familia de tubería (DI en mm)
PIPE_FAMILIES.mifamilia = { label:'Mi familia', eps:0.03, list:[ { nom:'DN 50', od:63, wall:4.5, di:54 } ] };

// Añadir un material (ε en mm)
MATERIALS.push({ name:'Mi material', eps:0.05, fam:'Mi familia' });
12. Limitaciones y uso responsable
Fuera de alcance del modelo: flujo transitorio y golpe de ariete; fluidos compresibles (gas); flujo bifásico; lámina libre y canales; redes malladas con distribución de caudal (requiere solución de red, no serie); sedimentación y transporte de sólidos; cavitación distribuida a lo largo del tramo; efectos de proximidad entre accesorios y de entrada/salida no idealizada.

Advertencias técnicas: en régimen laminar el método Le/D es aproximado (K laminar ≈ 1.4·K turbulento); en la zona de transición el factor de fricción es incierto por naturaleza; las curvas de bomba son parabólicas, por lo que conviene ajustar H₀ y Q<sub>máx</sub> a la curva real del fabricante antes de decidir una compra.

Uso responsable: la herramienta ejecuta y documenta el cálculo, pero no sustituye la verificación de un ingeniero competente ni el cumplimiento de normas, códigos locales, clases de presión, requisitos sísmicos, de montaje o de instrumentación. Los resultados deben respaldarse con la memoria de cálculo y con los catálogos de los equipos.

13. Hoja de ruta
Redes ramificadas y malladas (método de Hardy Cross / gradiente global).
Lectura de curvas de bomba reales por puntos tabulados y ajuste polinómico.
Catálogo de bombas del fabricante con selección automática por punto de operación.
Análisis de sensibilidad en lote (barrido de diámetros, caudales y velocidades de giro).
Módulo de golpe de ariete (celda de características) y de cavitación distribuida.
Exportación a PDF con formato de memoria de cálculo y a IFC/Hydraulic JSON.
Empaquetado como PWA instalable y versión de escritorio (Tauri/Electron).
14. Glosario de símbolos
Símbolo	Significado	Unidad
Q	Caudal volumétrico	m³/s
V	Velocidad media	m/s
D, L	Diámetro interior y longitud	m
ε	Rugosidad absoluta	m (tablas en mm)
Re	Número de Reynolds, ρVD/μ	—
f, f<sub>T</sub>	Factor de fricción Darcy; de tubería rugosa	—
K, Le/D	Coeficiente local; longitud equivalente	—
h<sub>f</sub>, h<sub>m</sub>, h<sub>L</sub>	Pérdida distribuida, local y total	m
h<sub>A</sub>	Carga de la bomba	m
γ	Peso específico, ρg	N/m³
ν	Viscosidad cinemática, μ/ρ	m²/s
P<sub>v</sub>	Presión de vapor	Pa (tablas en kPa)
NPSH<sub>a</sub>, NPSH<sub>r</sub>	Carga neta positiva de succión disponible / requerida	m
H₀, Q<sub>máx</sub>	Altura a cierre y caudal a H = 0	m, m³/s
N<sub>s</sub>	Velocidad específica	(m, m³/s, rpm)
η	Rendimiento	—
15. Cómo citar
APA 7

Sandoval Herrera, J. (2026). Hidráulica de tuberías en serie: calculadora integral de mecánica de fluidos (v2.0) [Software]. Universidad de América.

BibTeX

bibtex

@software{sandoval2026hidraulica,
  author       = {Sandoval Herrera, Juan},
  title        = {Hidr{\'a}ulica de tuber{\'i}as en serie: calculadora integral de mec{\'a}nica de fluidos},
  version      = {2.0},
  year         = {2026},
  organization = {Universidad de Am{\'e}rica},
  note         = {Herramienta de c{\'a}lculo en un solo archivo HTML, sin dependencias externas}
}
16. Créditos y licencia
Autoría y dirección técnica: Prof. Ph.D. Juan Sandoval Herrera — Universidad de América. Texto guía: Sandoval, J. (Ed.). (2018). Mecánica de fluidos. Publicaciones Universidad de América. https://doi.org/10.29097/9789588517360

Fuentes de correlaciones y datos: Crane Co. (1988) TP-410; Mott & Untener (2015) Applied Fluid Mechanics; White (2016) Fluid Mechanics; Fox, McDonald & Pritchard (2011); Çengel & Cimbala (2018); Karassik et al. (2008) Pump Handbook; Hydraulic Institute ANSI/HI 9.6.1; ASME B36.10M; ASTM B88; AWWA C900; Perry & Green (2008); Incropera & DeWitt (2011).

Documentos del proyecto

Archivo	Contenido

simulador-tuberias-serie-v2.html
Aplicación completa (un solo archivo, offline)

README.md
Este documento: alcance, fundamentos, validación y guía de uso

REVISION-Y-CAMBIOS-V2.md
Informe de revisión técnica: errores corregidos, ampliaciones y verificación
Licencia: uso educativo e institucional. Para uso comercial, distribución en productos de ingeniería o incorporación en plataformas de terceros, contacte al autor. Se solicita citar la fuente y el texto guía en trabajos académicos y memorias de cálculo derivadas.


