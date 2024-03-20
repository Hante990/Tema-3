# Tema-3
Realizado por:
  <li>Diego Alonso Fernández Delagadillo</li>
  <li> Antonio Guerrero Lazcano</li>
  <li>Miguel Angel Flores Lopez</li>
  <li>Xavier Valle Dorantes</li>
<h2 align = "center"> <font color = "darkorange" size = "+6"  font face = "bauhaus 93">  Indice </font> </h2>
<header> <font color = "red" size="+1" font face = "aharoni">
                <nav class="navegacion">
                    <ul class="Indice">
                       <li> <a href="#Descripción del Problemario"> Descripción del Problemario </a> <br> </li>
                        <li> <a href="#SOBRE LA MATERIA"> Sobre la materia </a> <br> </li>
                            <ul class="subindice"> 
                                <li> <a href="#Competencia de la Asignatura"> Competencia de la Asignatura </a> </li>
                                <li> <a href="#Competencia del TEMA"> Competencia del TEMA </a> </li>
                                <li> <a href="#TEMARIO"> Temario </a> </li>  
                            </ul>
     <li> <a href="#Métodos numéricos para encontrar las raíces de ecuaciones que se encuentran en nuestro repositorio"> Métodos numéricos para encontrar las raíces </a> <br> </li>
                            <ul class="subindice"> 
                                <li> <a href="#Método de Bisección"> Método de Bisección. </a> </li>
                                <li> <a href="#Método de la Falsa Posición"> Método de la Falsa Posición. </a> </li>
                                <li> <a href="#Método de la Secante"> Método de la Secante. </a> </li> 
                                <li> <a href="#Método de Newton-Raphson"> Método de Newton-Raphson. </a> </li> 
                            </ul>
                    </ul>
                </nav>
            </font> </header>

# Descripción
En este documento vamos a ver varios ejercicios sobre los distintos metodos como lo son:
  <li>1.-Biseccion</li>
  <li>2.-Falsa posición</li>
  <li>3.-De la secante</li>
  <li>4.-Newton</li>
  
# Sobre la materia 
<h2 align = "center"> <font  size = "+6" > Competencia de la asignatura</font> </h2>
Aplica los métodos numéricos para resolver problemas científicos y de ingeniería utilizando la computadora.
<h2 align = "center"> <font size = "+6"  > Competencia del tema</font> </h2>
Aplica los métodos numéricos con el objeto de solucionar ecuaciones mediante los métodos de intervalo e interpolación apoyada de un lenguaje de programación.  


<h3> <font font face = "forte"> <a name="TEMARIO"> TEMARIO  </a> </h3>
   
   2.1 Método de bisección.
   
  2.2 Método de falsa posicion.  
  
  2.3 Método de la secante.   

  2.4 Método de newton.
   
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
<h1 align = "center"> <font  font face = "bauhaus 93">  Métodos para enontrar las raíces de una ecuacion </font> </h1>

<h2 align = "center"> <font font face = "forte">  1. Bisección </h2>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

El método de bisección es un algoritmo utilizado para encontrar las raíces de una función en un intervalo dado. Consiste en dividir repetidamente el intervalo a la mitad y seleccionar el subintervalo que contiene la raíz. Este proceso se repite hasta que se alcanza la precisión deseada. Los pasos principales son los siguientes:

<h3> <font font face = "arial">Pasos del Método de Bisección:</h3>
<h5>Inicio del Intervalo:</h5> Se elige un intervalo inicial donde se sospecha que se encuentra la raíz.
<h5>Cálculo del Punto Medio:</h5> Se calcula el punto medio del intervalo.
<h5>Evaluación de la Función:</h5> Se evalúa la función en el punto medio para determinar en qué subintervalo se encuentra la raíz.
<h5>Selección del Nuevo Intervalo:</h5> Se selecciona el nuevo intervalo basado en la evaluación de la función en el punto medio.
<h5>Iteración:</h5> Se repiten los pasos anteriores hasta que se alcance la precisión deseada, es decir, hasta que el intervalo sea lo suficientemente pequeño.
   
<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>

  import java.util.Scanner;

public class Main {  
    
    public static void main(String[] args) {
      
        Scanner input = new Scanner(System.in);
        
        System.out.print("Ingrese el límite inferior: ");
        double a = input.nextDouble();

        System.out.print("Ingrese el límite superior: ");
        double b = input.nextDouble();

        System.out.print("Ingrese el máximo de iteraciones: ");
        int maxIterations = input.nextInt();

        System.out.print("Ingrese el error permitido: ");
        double error = input.nextDouble();

        double root = bisection(a, b, maxIterations, error);
        System.out.println("La raíz de la función es: " + root);
    }

    public static double bisection(double a, double b, int maxIterations, double error) {
        double fa = f(a);
        double fb = f(b);

        if (fa * fb > 0) {
            System.out.println("No se puede garantizar la existencia de una raíz en el intervalo dado.");
            return Double.NaN;
        }

        for (int i = 0; i < maxIterations; i++) {
            double c = (a + b) / 2;
            double fc = f(c);

            if (Math.abs(fc) < error) {
                return c;
            }

            if (fa * fc < 0) {
                b = c;
                fb = fc;
            } else {
                a = c;
                fa = fc;
            }
        }

        return (a + b) / 2;
    }

    public static double f(double x) {
    
        return x*x - 4; 
    }}
    
<h2 align = "center"> <font font face = "forte">  2.- Falsa posición </h2>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

El método de la falsa posición, también conocido como método de la regla falsa o regula falsi, es un algoritmo para encontrar las raíces de una función. A diferencia del método de bisección, que divide el intervalo por la mitad, el método de la falsa posición utiliza una línea recta para aproximar la función en el intervalo y encontrar la raíz.

<h3> <font font face = "arial">Pasos del Método de falsa posición: </h3>
<h5>Selección del intervalo inicial:</h5> Se elige un intervalo [a, b] donde se sospecha que se encuentra la raíz.
<h5>Cálculo del punto de intersección:</h5> Se calcula el punto c utilizando la fórmula: c = b - f(b) * (a - b) / (f(a) - f(b)).
<h5>Evaluación de la función:</h5>Se evalúa la función en c para determinar en qué subintervalo se encuentra la raíz.
<h5>Selección del nuevo intervalo:</h5> Se selecciona el nuevo intervalo basado en la evaluación de la función en c.
<h5>Iteración:</h5> Se repiten los pasos anteriores hasta que se alcance la precisión deseada, es decir, hasta que el intervalo sea lo suficientemente pequeño.
   
<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>

import java.util.Scanner;
public class Main {
   
    public static void main(String[] args) {
        
        Scanner input = new Scanner(System.in);

        System.out.print("Ingrese el límite inferior: ");
        double a = input.nextDouble();

        System.out.print("Ingrese el límite superior: ");
        double b = input.nextDouble();

        System.out.print("Ingrese el máximo de iteraciones: ");
        int maxIterations = input.nextInt();

        System.out.print("Ingrese el error permitido: ");
        double error = input.nextDouble();

        double root = falsePosition(a, b, maxIterations, error);
        System.out.println("La raíz de la función es: " + root);
    }

    public static double falsePosition(double a, double b, int maxIterations, double error) {
        double fa = f(a);
        double fb = f(b);

        if (fa * fb > 0) {
            System.out.println("No se puede garantizar la existencia de una raíz en el intervalo dado.");
            return Double.NaN;
        }

        for (int i = 0; i < maxIterations; i++) {
            double c = (a * fb - b * fa) / (fb - fa);
            double fc = f(c);

            if (Math.abs(fc) < error) {
                return c;
            }

            if (fa * fc < 0) {
                b = c;
                fb = fc;
            } else {
                a = c;
                fa = fc;
            }
        }

        return (a * fb - b * fa) / (fb - fa);
    }

    public static double f(double x) {
        // Definir aquí la función para la cual se desea encontrar la raíz
        return x*x - 4; // Ejemplo: x^2 - 4
    }}
    
<h2 align = "center"> <font font face = "forte">  3.- De la secante </h2>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

El método de la secante es un algoritmo numérico utilizado para encontrar las raíces de una función. A diferencia de los métodos de bisección y falsa posición, el método de la secante no requiere que la función cambie de signo en el intervalo inicial. En su lugar, utiliza una aproximación de la pendiente de la recta secante entre dos puntos cercanos para iterar hacia la raíz.

<h3> <font font face = "arial">Pasos del Método de Bisección:</h3>
<h5>Selección de dos puntos iniciales:</h5> Se eligen dos puntos iniciales cercanos a la raíz.
<h5>Cálculo del siguiente punto:</h5> Se calcula el siguiente punto utilizando la fórmula: x_{n+1} = x_n - f(x_n) * (x_n - x_{n-1}) / (f(x_n) - f(x_{n-1})).
<h5>Convergencia hacia la raíz:</h5> Se repite el paso anterior hasta que se alcance la precisión deseada o se cumpla un criterio de convergencia.
<h5>Actualización de los puntos:</h5> Se actualizan los puntos para continuar iterando hacia la raíz.
   
<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>

 import java.util.Scanner;

public class Main {
 
    public static void main(String[] args) {
      
        Scanner input = new Scanner(System.in);

        System.out.print("Ingrese el primer punto inicial: ");
        double x0 = input.nextDouble();

        System.out.print("Ingrese el segundo punto inicial: ");
        double x1 = input.nextDouble();

        System.out.print("Ingrese el máximo de iteraciones: ");
        int maxIterations = input.nextInt();

        System.out.print("Ingrese el error permitido: ");
        double error = input.nextDouble();

        double root = secant(x0, x1, maxIterations, error);
        System.out.println("La raíz de la función es: " + root);
    }

    public static double secant(double x0, double x1, int maxIterations, double error) {
        for (int i = 0; i < maxIterations; i++) {
            double fx0 = f(x0);
            double fx1 = f(x1);

            if (Math.abs(fx1 - fx0) < error) {
                return x1;
            }

            double x2 = x1 - (fx1 * (x1 - x0)) / (fx1 - fx0);

            x0 = x1;
            x1 = x2;
        }

        return x1;
    }

    public static double f(double x) {
        
        return x*x - 4; 
    }}
    
<h2 align = "center"> <font font face = "forte">  4. Newton </h2>

<h3> <font font face = "arial"> DESCRIPCIÓN: </h3>

El método de Newton, también conocido como método de Newton-Raphson, es un algoritmo utilizado para encontrar raíces de una función. Este método requiere conocer el valor de la primera derivada de la función en el punto de estudio. A continuación se detallan los pasos del método de Newton:

<h3> <font font face = "arial">Pasos del Método de Bisección:</h3>
<h5>Selección del punto inicial:</h5> Se elige un punto inicial cercano a la raíz deseada.
<h5>Cálculo de la pendiente:</h5> Se calcula la pendiente de la recta tangente a la curva en el punto seleccionado.
<h5>Determinación del siguiente punto:</h5> Se determina el siguiente punto de iteración utilizando la fórmula: x_{n+1} = x_n - f(x_n) / f'(x_n), donde f'(x) es la derivada de la función en x.
<h5>Convergencia hacia la raíz:</h5> Se repiten los pasos anteriores hasta alcanzar la precisión deseada o cumplir un criterio de convergencia.
   
<h5> <font font face = "arial"> <b> <i> Ejemplo en código. </i> </b> </h5>

public class MetodoNewton {

    public static double epsilon = 0.0001; 

    //  f(x) = cos(x) - x
    public static double funcion(double x) {
        return Math.cos(x) - x;
    }

    // Calculamos la derivada de la función
    public static double derivada(double x) {
        return -Math.sin(x) - 1;
    }

   
    public static double metodoNewton(double xInicial) {
        double xActual = xInicial;
        double xSiguiente;

        do {
            xSiguiente = xActual - funcion(xActual) / derivada(xActual);
            xActual = xSiguiente;
        } while (Math.abs(funcion(xActual)) > epsilon);

        return xActual;
    }

    public static void main(String[] args) {
        double xInicial = 0.5; // Valor inicial de x
        double solucion = metodoNewton(xInicial);
        System.out.println("La solución aproximada es: " + solucion);
    }}

    


