# Motor OSINT de riesgo y origen de fondos para Wealth Services

Nota interna de producto · Zest Capital · Área de Wealth Services
Fecha de corte de los datos operativos: octubre de 2026.
Todas las cifras de esta nota son **estimaciones internas del área**, medidas sobre el proceso actual de
onboarding, no cifras de mercado ni proyecciones auditadas.

## El problema

En Wealth Services, cada cliente nuevo pasa por un due diligence manual antes de que se pueda abrir la cuenta.
El analista busca al cliente y a sus vinculados en listas de sanciones, registros públicos, prensa, registros
societarios y antecedentes judiciales; luego redacta el KYC y arma el expediente de origen de fondos.

- El expediente de KYC toma en promedio **3** horas de analista por cliente.
- El analista consulta a mano alrededor de **40** fuentes públicas distintas entre listas, registros y prensa.
- Los datos se vuelven a digitar al menos **2** veces: una en el expediente y otra al cargar el contrato.

El problema de fondo no es la velocidad. Es que, cuando llega una auditoría y pregunta por qué se aceptó el
origen de los fondos de un cliente, la respuesta depende de lo que el analista recuerde y de capturas de
pantalla sueltas, sin fecha ni cita verificable.

## La propuesta

Un motor de *Open Source Intelligence* que arma el expediente antes de que el analista lo abra:

1. **Recolección.** Rastrea las fuentes públicas por cliente y por cada vinculado relevante: listas de
   sanciones y PEP, registros societarios, boletines oficiales, procesos judiciales públicos y prensa.
2. **Evidencia fechada.** Cada hallazgo se guarda con su fuente, su fecha y su enlace. No hay afirmación sin
   cita: el expediente se puede defender línea por línea ante un auditor.
3. **Scoring de riesgo.** Un puntaje de riesgo explicable, con los factores que lo suben o lo bajan, al estilo
   de lo que Kueski, Yape, An Group o M-Pesa hicieron para crédito, pero aplicado a patrimonio.
4. **Coherencia de ingresos.** Contrasta el patrimonio y los ingresos declarados por el cliente contra la
   actividad económica que sí aparece en fuentes públicas, y marca las brechas que no tienen explicación.
5. **Integración.** El puntaje, los hallazgos y el expediente entran directo a **Salesforce** como campos del
   registro del cliente; si el caso aprueba, **DocuSign** dispara los contratos ya pre-rellenados desde esos
   mismos campos, sin que nadie vuelva a digitar un dato.

## El impacto esperado

- El expediente pasa de **3** horas a **15** minutos de revisión humana: el analista valida y firma en lugar
  de buscar.
- Con ese tiempo, el mismo equipo puede atender cerca de **5** veces más clientes sin contratar analistas.
- Y lo más importante: cada decisión queda con evidencia citada y fechada, lista para auditoría.

## Qué se busca

Socios y presupuesto para un piloto del motor sobre la cartera actual de Wealth Services, con las
integraciones de Salesforce y DocuSign incluidas en el alcance del piloto.

## Reglas del producto

- Solo fuentes de acceso público y lícito. Nada de datos obtenidos por acceso no autorizado.
- El motor propone; la decisión de aceptar o rechazar a un cliente siempre la toma una persona.
- Todo hallazgo sin fuente verificable no entra al expediente.
