# tarea
## ejercicios: 
### 1.- Filtar y manipular bases de datos   
Supongamos que tienes el siguiente data frame con información de especies:

especies <- data.frame(
  especie = c("Ajolote", "Rana", "Serpiente", "Tortuga"),
  habitat = c("Lago", "Río", "Bosque", "Lago"),
  tamano = c(30, 10, 150, 50),
  peso = c(150, 25, 1000, 500)
)
 Reto: - Filtrar todas las especies que viven en un lago.
- Ordenar los resultados por tamaño (de mayor a menor).
- ![image](https://github.com/user-attachments/assets/79f0b9cb-2196-418a-86a4-3477edf2f599)


   Carga la librería dplyr library(dplyr)
  # Crea el data frame
especies <- data.frame(
  especie = c("Ajolote", "Rana", "Serpiente", "Tortuga"),
  habitat = c("Lago", "Río", "Bosque", "Lago"),
  tamano = c(30, 10, 150, 50),
  peso = c(150, 25, 1000, 500)
)

# Filtra las especies que viven en un lago y ordena por tamaño
resultados <- especies %>%
  filter(habitat == "Lago") %>%
  arrange(desc(tamano))

  # 2. Generación de gráficos
  ### Reto:
- Crear un gráfico de dispersión entre Sepal.Length y Sepal.Width, y colorear los puntos según la especie.
- library(ggplot2)

ggplot(iris, aes(x = Sepal.Length, y = Sepal.Width, color = Species)) +
  geom_point(size = 3) +
  labs(title = "Relación entre Largo y Ancho de Sépalo",
       x = "Largo del Sépalo",
       y = "Ancho del Sépalo") +
  theme_minimal() +
  scale_color_manual(values = c("setosa" = " #C1FFC1", "versicolor" = "#FFF68F", "virginica" = "#D1EEEE"))
  ![image](https://github.com/user-attachments/assets/b616355e-c675-4d82-b575-417fc8441d13)

# 3.-Agrupar datos y realizar cálculos agregados
Supongamos que tienes un data frame con las calificaciones de estudiantes en diferentes asignaturas:

calificaciones <- data.frame(
  estudiante = c("Ana", "Carlos", "Lucía", "Jorge", "Ana", "Carlos", "Lucía", "Jorge"),
  asignatura = c("Matemáticas", "Matemáticas", "Matemáticas", "Matemáticas", "Historia", "Historia", "Historia", "Historia"),
  calificacion = c(95, 85, 92, 88, 78, 82, 85, 90)
)

# Reto:
 Agrupar las calificaciones por estudiante y calcular el promedio de calificación por cada uno.
Carga la librería dplyr
library(dplyr)

# Crea el data frame
calificaciones <- data.frame(
  estudiante = c("Ana", "Carlos", "Lucía", "Jorge", "Ana", "Carlos", "Lucía", "Jorge"),
  asignatura = c("Matemáticas", "Matemáticas", "Matemáticas", "Matemáticas", "Historia", "Historia", "Historia", "Historia"),
  calificacion = c(95, 85, 92, 88, 78, 82, 85, 90)
)

# Agrupa las calificaciones por estudiante y calcula el promedio
promedios <- calificaciones %>%
  group_by(estudiante) %>%
  summarise(promedio = mean(calificacion))

  # 4.- Transformación de datos y crear nuevas variables
### Reto:
 Crear una nueva columna con las alturas en metros y mostrar el nuevo data frame.
alturas <- data.frame(
  nombre = c("Laura", "Pedro", "Sara", "Miguel"),
  altura_cm = c(160, 175, 150, 180)
)
#crear el data frame #
alturas <- data.frame(
nombre = c("Laura", "Pedro", "Sara", "Miguel"),
altura_cm = c(160, 175, 150, 180)
)
#Crear una nueva columna con las alturas en metros.#
alturas$altura_m = alturas$altura_cm / 100

# 5.- Generación de gráficos de barras
#Crear un gráfico de barras para visualizar las ventas mensuales.
ventas <- data.frame(
  mes = c("Enero", "Febrero", "Marzo", "Abril", "Mayo", "Junio"),
  ventas = c(12000, 15000, 13000, 16000, 17500, 14000)
)
ggplot(ventas, aes(x = mes, y = ventas, fill = mes)) +
     geom_bar(stat = "identity") +
     labs(title = "Ventas Mensuales",
          x = "Mes",
          y = "Ventas") +
     theme_minimal() +
    scale_fill_brewer(palette = "Set2") 
ggplot(ventas, aes(x = mes, y = ventas, fill = mes)) +
   geom_bar(stat = "identity") +
     labs(title = "Ventas Mensuales",
          x = "Mes",
         y = "Ventas") +
     theme_minimal() +
     scale_fill_brewer(palette = "Set5")
 ![image](https://github.com/user-attachments/assets/3befd247-0111-475b-b288-4c453e3456dc)

  # 6.-Lectura y escritura de archivos CSV
  Crear un data frame de ejemplo
productos <- data.frame(
  producto = c("A", "B", "C", "D"),
  precio = c(20, 35, 50, 10),
  cantidad_vendida = c(100, 200, 150, 250)
)
 Reto:
 Calcular el total de ingresos por producto (precio * cantidad vendida) y agregarlo como una nueva columna.
 #Crear el data frame de productos 
productos <- data.frame(
  producto = c("A", "B", "C", "D"),
  precio = c(20, 35, 50, 10),
  cantidad_vendida = c(100, 200, 150, 250)
)

#Calcular el total de ingresos y agregarlo como una nueva columna
productos <- productos %>%
  mutate(ingreso_total = precio * cantidad_vendida)

#Escribir el archivo CSV
write.csv(productos, "productos_con_ingresos.csv", row.names = FALSE)
print(productos)
#  Gráfico de caja (boxplot)
 Reto:
Crear un gráfico de caja (boxplot) que muestre la distribución de millas por galón (mpg) en función del número de cilindros (cyl).
ggplot(mtcars, aes(x = factor(cyl), y = mpg, fill = factor(cyl))) +
+     geom_boxplot() +
+     labs(title = "Distribución de MPG según el Número de Cilindros",
+          x = "Número de Cilindros",
+          y = "Millas por Galón (MPG)") +
+     scale_fill_manual(values = c("8" = "darkolivegreen3", "6" = "cadetblue1", "4" = "#FFB6C1")) + 
+     theme_minimal()
+ ![image](https://github.com/user-attachments/assets/38d7c378-330d-47d5-8f4a-c6a9c78c9b0b)
