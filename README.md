# YoTypeScriptQuinta {#yotypescriptquinta}

Yo:TypeScript

J.C. Lama

Esta página se ha dejado en blanco intencionalmente.

José Carlos Lama Ponce

Quinta edición: mayo 2016

Versión TypeScript: 1.8.10

_A mis padres, mis hermanos y mi pareja._

Esta página se ha dejado en blanco intencionalmente.

[0.Introducción 11](export/anexo_i_arrays/introduccion.md)

[0.1 ¿A quién va dirigido este libro? 11](export/introduccion/a_quien_va_dirigido_este_libro.md)

[0.2 JavaScript 11](export/introduccion/javascript.md)

[0.2.1Historia 11](export/introduccion/javascript.md#historia)

[0.2.2Ámbito de ejecución 11](export/introduccion/javascript.md#mbito-de-ejecuci-n)

[0.2.3Compatibilidad con navegadores 12](export/introduccion/javascript.md#compatibilidad-con-navegadores)

[0.3 TypeScript 12](export/introduccion/typescript.md)

[0.3.1¿Por qué TypeSript? 12](export/introduccion/typescript.md#por-qu-typesript)

[0.3.2Qué es y no es TypeScript 13](export/introduccion/typescript.md#qu-es-y-no-es-typescript)

[0.3.3TS es JS 13](export/introduccion/typescript.md#ts-es-js)

0.3.4Requisitos 14

[1.Generalidades 15](export/generalidades/README.md)

1.1 Sentencias 15

1.2 Sensible a las mayúsculas 15

1.3 Palabras reservadas 15

1.4 Unicode 15

1.5 Comentarios 16

2.Cómo empezar 17

[2.1 Introducción 17](export/anexo_i_arrays/introduccion.md)

[2.2 Editores 18](export/como_empezar/editores.md)

[3.Visual Studio Code 19](export/visual_studio_code/README.md)

[3.1 El editor de Microsoft 19](export/visual_studio_code/el_editor_de_microsoft.md)

[3.2 Dividir el proyecto 24](export/visual_studio_code/dividir_el_proyecto.md)

[3.3 Librerías externas 26](export/visual_studio_code/librerias_externas.md)

[3.4 Compilar JS 26](export/visual_studio_code/compilar_js.md)

[4.Depuración 27](export/depuracion/README.md)

[4.1 Introducción 27](export/anexo_i_arrays/introduccion.md)

[4.2 La consola 27](export/depuracion/la_consola.md)

4.3 Depurando TS 28

[4.4 Puntos de ruptura 29](export/depuracion/puntos_de_ruptura.md)

[4.5 Evaluador de expresiones 30](export/depuracion/evaluador_de_expresiones.md)

[5.Variables 32](export/variables/README.md)

5.1 Introducción 32

5.2 Nombres de variables 32

5.3 Inicialización 32

5.4 Ámbito de una variable 33

5.5 Constantes 33

6.Tipos 35

[6.1 Variables con tipo 35](export/tipos/variables_con_tipo.md)

6.2 Tipos primitivos y tipos objeto 35

6.2.1Inicialización literal 36

[6.2.2Template Strings (cadenas plantilla) 37](export/tipos/tipos_primitivos_y_tipos_objeto.md#template-strings-cadenas-plantilla)

[6.2.3¿Primitivo u objeto? ¿Cuál usar? 38](export/tipos/tipos_primitivos_y_tipos_objeto.md#primitivo-u-objeto-cu-l-usar)

6.3 Otros tipos 39

6.3.1Void 39

6.3.2Null 39

6.3.3Undefined 40

6.3.4Enum 40

6.3.5Function 40

6.3.6Array 40

6.3.7Object 41

6.3.8Symbols 41

[6.3.9Tipos Alias. (Alias Types) 42](export/tipos/otros_tipos.md#tipos-alias-alias-types)

[6.3.10Tuple Types (Tipos tupla) 42](export/tipos/otros_tipos.md#tuple-types-tipos-tupla)

6.3.11Tipos Unión (Union Types) 43

[6.3.12Tipos Intersección (Intersection Types) 43](export/tipos/otros_tipos.md#tipos-intersecci-n-intersection-types)

[6.3.13Tipos Locales (Local Types) 44](export/tipos/otros_tipos.md#tipos-locales-local-types)

[6.3.14Tipos de cadenas literales (String Literal Types) 45](export/tipos/otros_tipos.md#tipos-de-cadenas-literales-string-literal-types)

[6.3.15Guarda de tipos (Type Guards) 45](export/tipos/otros_tipos.md#guarda-de-tipos-type-guards)

[6.3.16Guardas propias 47](export/tipos/otros_tipos.md#guardas-propias)

6.4 Tipos nombrados y referencia 48

6.5 Inferencia de tipos 48

6.5.1Inferencia básica 48

6.5.2Expresiones tipadas por el contexto 48

6.6 El mejor tipo común 49

[6.6.1Any como tipo general 49](export/tipos/el_mejor_tipo_comun.md#any-como-tipo-general)

[6.6.2{} 49](export/tipos/el_mejor_tipo_comun.md#)

[6.6.3Entre primitivos 50](export/tipos/el_mejor_tipo_comun.md#entre-primitivos)

[6.6.4Entre primitivos y objetos 50](export/tipos/el_mejor_tipo_comun.md#entre-primitivos-y-objetos)

[6.6.5Entre tipos referencia 50](export/tipos/el_mejor_tipo_comun.md#entre-tipos-referencia)

6.7 typeof 51

6.8 Destructuring (deconstrucción) 52

[6.8.1Arrays 52](export/tipos/destructuring_deconstruccion.md#arrays)

[6.8.2Objetos 52](export/objetos/README.md)

[6.8.3En los parámetros de una función 53](export/tipos/destructuring_deconstruccion.md#en-los-par-metros-de-una-funci-n)

[7.Operadores 54](export/operadores/operadores_binarios.md#operadores)

7.1 Operadores unarios 54

7.1.1Operadores ++ y -- 54

7.1.2Operadores +, – 55

7.1.3Operador ~ 55

7.1.4Operador ! 55

7.1.5Operador delete 56

7.1.6Operador void 56

[7.1.7Operador … (spread) 56](export/operadores/operadores_unarios.md#operador-spread)

7.2 Operadores binarios 57

7.2.1Operador de asignación 57

7.2.2Operadores lógicos 57

[7.2.2.1 false en TS 58](export/operadores/operadores_binarios.md#false-en-ts)

[7.2.2.2 Operador AND 58](export/operadores/operadores_binarios.md#operador-and)

[7.2.2.3 Operador OR 59](export/operadores/operadores_binarios.md#operador-or)

7.2.3Operadores aritméticos 59

[7.2.3.1 Operadores + y - 60](export/operadores/operadores_binarios.md#operadores-y)

[7.2.3.2 Operadores * y / 60](export/operadores/operadores_binarios.md#operadores-y-0)

[7.2.3.3 Operador % 60](export/operadores/operadores_binarios.md#operador)

[7.2.3.4 Operador ** 60](export/operadores/operadores_binarios.md#operador-0)

7.2.4Operadores de bits 61

[7.2.4.1 Operadores lógicos bit a bit 61](export/operadores/operadores_binarios.md#operadores-l-gicos-bit-a-bit)

[7.2.4.2 Operadores << y >> 61](export/operadores/operadores_binarios.md#operadores-y-1)

7.2.5Operadores relacionales 62

[7.2.5.1 Operadores <, >, <=, >=, 62](export/operadores/operadores_binarios.md#operadores)

[7.2.5.2 Operadores == y != 62](export/operadores/operadores_binarios.md#operadores-y-2)

[7.2.5.3 Operadores === y !== 63](export/operadores/operadores_binarios.md#operadores-y-3)

7.2.6Operador + de concatenación 64

7.2.7Operador in 64

7.2.8Operador condicional terciario 65

[8.Control del flujo 66](export/control_del_flujo/README.md)

8.1 Introducción 66

8.2 Selectivas 66

8.2.1if 66

8.2.2switch 67

8.3 Iterativas 68

8.3.1while 68

8.3.2do-while 68

8.3.3for 68

8.3.4for-in 69

[8.3.5for-of 69](export/control_del_flujo/iterativas.md#for-of)

8.4 Sentencias útiles para los bucles 70

[8.4.1break 70](export/control_del_flujo/sentencias_utiles_para_los_bucles.md#break)

[8.4.2continue 70](export/control_del_flujo/sentencias_utiles_para_los_bucles.md#continue)

[8.4.3return 70](export/control_del_flujo/sentencias_utiles_para_los_bucles.md#return)

[8.5 Código inalcanzable 71](export/control_del_flujo/codigo_inalcanzable.md)

9.Objetos 72

[9.1 Introducción 72](export/anexo_i_arrays/introduccion.md)

[9.2 Propiedades computadas (Computed properties) 72](export/objetos/propiedades_computadas_computed_properties.md)

9.2.1Propiedades Symbol 73

[9.3 Tipo objeto literal (Object type literal) 73](export/objetos/tipo_objeto_literal_object_type_literal.md)

[9.4 Exceso de propiedades 74](export/objetos/exceso_de_propiedades.md)

[9.5 Propiedades opcionales 75](export/objetos/propiedades_opcionales.md)

[9.6 Relación con las interfaces 76](export/objetos/relacion_con_las_interfaces.md)

[10.Funciones 78](export/modulos/fusionando_modulos_con_funciones_y_enums.md#funciones)

10.1 Introducción 78

10.2 Declaración 78

10.3 Parámetros de una función 78

10.3.1Parámetros opcionales y por defecto 79

10.3.2Más parámetros 79

10.3.3Parámetros por valor o por referencia 80

[10.3.3.1 Por valor 80](export/funciones/parametros_de_una_funcion.md#por-valor)

[10.3.3.2 Por referencia 81](export/funciones/parametros_de_una_funcion.md#por-referencia)

10.4 Valores de retorno 81

10.5 Invocando funciones 82

10.6 Sobrecarga 82

10.7 Funciones anónimas 83

10.7.1Expresiones lambda (funciones flecha) 84

10.7.2Tipado literal de una función 84

10.7.3Tipado mediante objetos literales 85

10.7.4Definición de función por parámetro 86

[10.7.5Contexto 86](export/clases/estado_y_comportamiento.md#contexto)

[10.7.6Funciones anónimas autoejecutables 87](export/funciones/funciones_anonimas.md#funciones-an-nimas-autoejecutables)

[10.8 Funciones que devuelven funciones 87](export/funciones/funciones_que_devuelven_funciones.md)

10.9 Funciones especializadas 87

10.10 Comparando funciones 88

11.Clases 90

11.1 Qué es una clase 90

11.2 Creación de clases 90

[11.2.1Declaración 90](export/clases/creacion_de_clases.md#declaraci-n)

[11.2.2Expresión 91](export/clases/creacion_de_clases.md#expresi-n)

[11.3 Instanciación 91](export/clases/instanciacion.md)

11.4 Constructores 91

11.5 Estado y comportamiento 92

11.5.1El estado 92

[11.5.1.1 Otra forma de declarar atributos 93](export/clases/estado_y_comportamiento.md#otra-forma-de-declarar-atributos)

11.5.2El comportamiento 93

11.5.3Operador this 94

[11.5.3.1 Contexto 95](export/clases/estado_y_comportamiento.md#contexto)

[11.5.3.2 this polimórfico 96](export/clases/estado_y_comportamiento.md#this-polim-rfico)

11.6 Encapsulamiento 98

11.6.1Getters y setter implícitos (accesors) 99

11.7 Herencia 101

[11.7.1Herencia mediante expresiones 101](export/clases/herencia.md#herencia-mediante-expresiones)

11.7.2El operador super 103

11.7.3Sobreescritura 104

[11.7.3.1 Sobreescritura de métodos 105](export/clases/herencia.md#sobreescritura-de-m-todos)

[11.7.4Mixins 105](export/clases/herencia.md#mixins)

11.8 Agregación y composición 105

11.9 Polimorfismo 106

11.10 Confirmaciones de tipo ( Type Assertions ) 107

11.11 Ligadura dinámica 108

11.12 instanceOf 109

11.13 Estáticos 110

[11.14 Las partes de una clase 111](export/clases/las_partes_de_una_clase.md)

11.15 Objetos dinámicos 112

[11.16 Clases abstractas 113](export/clases/clases_abstractas.md)

12.Interfaces 116

12.1 Introducción 116

12.2 Declaración e implementación 116

12.3 Herencia 117

12.4 Interfaces como funciones 118

12.5 Fusionando interfaces 118

[12.6 Comprobar si una clase implementa una interfaz 119](export/interfaces/comprobar_si_una_clase_implementa_una_interfaz.md)

[13.Enumerados 120](export/enumerados/README.md)

13.1 Introducción 120

13.2 Obteniendo el nombre del valor 120

13.3 Const enums 121

14.Genéricos 122

14.1 Introducción 122

14.2 Restricciones en los parámetros 123

14.3 Genéricos en interfaces 124

14.4 Funciones genéricas 125

14.5 Comparando genéricos 125

[15.Tipado estructural 127](export/tipado_estructural/README.md)

15.1 Más sobre la comparación de objetos 127

15.2 Comparando clases 127

15.3 Comparando interfaces 128

15.4 Clases implementando otras clases 129

15.5 Interfaces herendando de clases 130

16.Control de errores 131

16.1 Introducción 131

16.2 Tipos de errores 131

16.3 Lanzando errores 132

16.4 Lanzando errores manualmente 133

16.5 Finally 133

17.DOM 135

[17.1 Introducción 135](export/anexo_i_arrays/introduccion.md)

[17.2 Document 135](export/dom/document.md)

[17.2.1Seleccionar elementos 135](export/dom/document.md#seleccionar-elementos)

[17.2.1.1 getElementById() 135](export/dom/document.md#getelementbyid)

[17.2.1.2 getElementsByTagName() 136](export/dom/document.md#getelementsbytagname)

[17.3 Crear elementos 136](export/dom/crear_elementos.md)

[17.4 Eliminar elementos 136](export/dom/eliminar_elementos.md)

[17.5 Acceso a los atributos 137](export/dom/acceso_a_los_atributos.md)

[18.Eventos 138](export/eventos/README.md)

18.1 Introducción 138

[18.2 Eventos visuales 138](export/eventos/eventos_visuales.md)

18.2.1Fase de captura 138

18.2.2Fase de objetivo 139

18.2.3Fase de burbuja 139

18.2.4Añadir respuesta a los eventos. 139

18.2.5Parámetros de los handlers 140

[18.2.6Target y currentTarget 140](export/eventos/eventos_visuales.md#target-y-currenttarget)

[18.2.7El uso del this 141](export/eventos/eventos_visuales.md#el-uso-del-this)

[18.2.8Parar la propagación de un evento 141](export/eventos/eventos_visuales.md#parar-la-propagaci-n-de-un-evento)

[18.2.9Parar la propagación hacia otros listeners del mismo elemento y evento 142](export/eventos/eventos_visuales.md#parar-la-propagaci-n-hacia-otros-listeners-del-mismo-elemento-y-evento)

[18.3 Eventos no visuales 143](export/eventos/eventos_no_visuales.md)

[19.Ajax 144](export/ajax/README.md)

19.1 Introducción 144

[19.2 Clase de utilidad 144](export/ajax/clase_de_utilidad.md)

[19.3 Estados de la petición y respuesta del servidor 146](export/ajax/estados_de_la_peticion_y_respuesta_del_servidor.md)

20.Módulos 147

20.1 Introducción 147

20.2 Partes de un módulo 148

[20.3 Importar tipos 148](export/modulos/importar_tipos.md)

20.4 Un mismo módulo en distintos archivos 149

20.5 Fusionando módulos con funciones y enums 150

[20.5.1Funciones 150](export/modulos/fusionando_modulos_con_funciones_y_enums.md#funciones)

[20.5.2Enums 150](export/modulos/fusionando_modulos_con_funciones_y_enums.md#enums)

20.6 Módulos externos 151

[20.6.1Exportando 151](export/modulos/modulos_externos.md#exportando)

[20.6.2Importando 152](export/modulos/modulos_externos.md#importando)

[20.6.3Cómo generarlos 153](export/modulos/modulos_externos.md#c-mo-generarlos)

[20.6.4Compatibilidad con la antigua sintaxis 153](export/modulos/modulos_externos.md#compatibilidad-con-la-antigua-sintaxis)

20.7 Trabajando con librerías externas 154

20.7.1Archivos de definiciones 155

20.8 Evitar que una clase pueda ser superclase 155

21.Iteradores 157

[21.1 Introducción 157](export/anexo_i_arrays/introduccion.md)

[21.2 La importancia de Symbol 157](export/iteradores/la_importancia_de_symbol.md)

[21.3 Iteradores propios 157](export/iteradores/iteradores_propios.md)

[22.Generadores 160](export/generadores/README.md)

[22.1 Introducción 160](export/anexo_i_arrays/introduccion.md)

[22.2 Recursión 162](export/generadores/recursion.md)

[23.Funciones asíncronas 165](export/funciones_asincronas/README.md)

[23.1 Introducción 165](export/anexo_i_arrays/introduccion.md)

[23.2 Async y await. 165](export/funciones_asincronas/async_y_await.md)

[23.3 Await*. 167](export/funciones_asincronas/await.md)

[24.Decoradores 169](export/decoradores/README.md)

[24.1 Introducción 169](export/anexo_i_arrays/introduccion.md)

[24.2 Decorador de clase 169](export/decoradores/decorador_de_clase.md)

[24.3 Decorador de atributo 170](export/decoradores/decorador_de_atributo.md)

[24.4 Decorador de método 171](export/decoradores/decorador_de_metodo.md)

[24.5 Decorador de parámetro 171](export/decoradores/decorador_de_parametro.md)

[24.6 this en los decoradores 172](export/decoradores/this_en_los_decoradores.md)

[24.7 Precedencia de los decoradores 172](export/decoradores/precedencia_de_los_decoradores.md)

[24.8 Parámetros en los decoradores 173](export/decoradores/parametros_en_los_decoradores.md)

[25.Anexo I. Arrays 174](export/anexo_i_arrays/README.md)

25.1 Introducción 174

25.2 Atributos 174

25.2.1Length 174

25.3 Métodos 175

25.3.1concat 175

25.3.2every 175

25.3.3some 175

25.3.4filter 176

25.3.5foreach 176

25.3.6indexOf 177

25.3.7lastIndexOf 177

25.3.8join 178

25.3.9map 178

25.3.10shift 178

25.3.11pop 178

25.3.12push 179

25.3.13unshift 179

25.3.14reduce 179

25.3.15reduceright 180

25.3.16reverse 181

25.3.17slice 181

25.3.18sort 181

25.3.19splice 182

25.3.20toString 182

[26.Anexo II Strings 183](export/anexo_ii_strings/README.md)

26.1 Atributos 183

26.1.1length 183

26.2 Métodos 183

26.2.1charAt 183

26.2.2charCodeAt 183

26.2.3concat 183

26.2.4indexOf 184

26.2.5lastIndexOf 184

26.2.6match 184

26.2.7replace 185

26.2.8search 185

26.2.9slice 185

26.2.10split 186

26.2.11substr 186

26.2.12substring 186

26.2.13toLowerCase 186

26.2.14toUpperCase 186

26.2.15trim 187

[27.Anexo III. JSON 188](export/anexo_iii_json/README.md)

[27.1 La clase JSON 188](export/anexo_iii_json/la_clase_json.md)

[27.1.1De JSON a JS 188](export/anexo_iii_json/la_clase_json.md#de-json-a-js)

[27.1.2De JS a JSON 189](export/anexo_iii_json/la_clase_json.md#de-js-a-json)

28.Anexo IV. tsconfig.json 190

[29.Anexo V. TS => ECMAScript 195](export/anexo_v_ts_=_ecmascript.md)

[30.Novedades de la edición 197](export/novedades_de_la_edicion.md)