# ¿Qué hace este código?

Este código implementa una Transformada Discreta de Fourier (DFT), que es un algoritmo matemático fundamental utilizado para analizar las componentes de frecuencia de una señal digital. Convierte una señal del dominio del tiempo (muestras a lo largo del tiempo) al dominio de la frecuencia (magnitud de diferentes componentes frecuenciales).

# Aplicaciones Prácticas:

· Análisis espectral de audio y señales de voz
· Procesamiento de imágenes (análisis de patrones)
· Sistemas de comunicaciones digitales
· Análisis de vibraciones en ingeniería mecánica
· Síntesis de sonido y efectos de audio

## La Clase TransformadaFourier

_init_(self, señal: list) (Inicializador):

Propósito: Prepara la clase para trabajar con la señal de entrada.

## Variables que son clave:

self.señal: Guarda la lista de números de entrada.

self.N: Guarda la longitud de la señal (cuántos puntos tiene). Esto es crucial para la fórmula de la DFT.

self.transformada: Inicialmente es None. Aquí se guardará el resultado de la DFT

## El Método dft() 

Este método implementa la fórmula matemática de la Transformada Discreta de Fourier (DFT), que convierte la señal del dominio del tiempo al dominio de la frecuencia.

Propósito: Calcular los coeficientes de frecuencia de la señal.

Este método implementa la fórmula matemática de la Transformada Discreta de Fourier (DFT), que convierte la señal del dominio del tiempo al dominio de la frecuencia.

El método devuelve X, una lista de números complejos. Cada número complejo tiene una magnitud (cuánta energía hay en esa frecuencia) y una fase (cuál es el desplazamiento de esa frecuencia).

 ```python

import math
import cmath

class TransformadaFourier:
    def init(self, señal: list):
        """
        Inicializa la clase con una señal (lista de números).
        """
        self.señal = señal
        self.N = len(señal)
        self.transformada = None

    def dft(self) -> list:
        """
        Calcula la Transformada Discreta de Fourier (DFT) de la señal.
        """
        X = []
        for k in range(self.N):
            suma = 0
            for n in range(self.N):
                angulo = -2j * math.pi * k * n / self.N
                suma += self.señal[n] * cmath.exp(angulo)
            X.append(suma)
        self.transformada = X
        return X

    def abs_complejo_formula(z: complex) -> complex:
        """
        Calcula el valor absoluto de un número complejo y lo devuelve como complejo.
        """
        if isinstance(z, complex):
            a = z.real
            b = z.imag
            magnitud = math.sqrt(a*a + b*b)
            return complex(magnitud, 0)
        try:
            return complex(abs(z), 0)
        except Exception as e:
            raise TypeError(f"No se pudo calcular |z| para tipo {type(z)}: {e}")

  ```