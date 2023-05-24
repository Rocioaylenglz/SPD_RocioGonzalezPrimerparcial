# SPD_RocioGonzalezPrimerparcial

* Rocio González 1B

## Proyecto : Montacargas, parcial

* Funcionnamiento Integral
<pre lang="cpp">
#define sube A2
#define pausa A1
#define baja A0
#define LED_VERDE 13
#define LED_ROJO 12

#define SEG_A 4
#define SEG_B 5
#define SEG_C A3
#define SEG_D A4
#define SEG_E A5
#define SEG_F 3
#define SEG_G 2

int tiempo = 1500;
int estadosubo;
int estadoparo;
int estadobajo;

int pisoActual = 0;
</pre>
Defino las variables y declaro tanto el tiempo como el estado de los botones y el contador para los pisos
<pre lang="cpp">
void setup()
{
    pinMode(sube, INPUT_PULLUP);
    pinMode(pausa, INPUT_PULLUP);
    pinMode(baja, INPUT_PULLUP);
    pinMode(LED_VERDE, OUTPUT);
    pinMode(LED_ROJO, OUTPUT);
    pinMode(SEG_A, OUTPUT);
    pinMode(SEG_B, OUTPUT);
    pinMode(SEG_C, OUTPUT);
    pinMode(SEG_D, OUTPUT);
    pinMode(SEG_E, OUTPUT);
    pinMode(SEG_F, OUTPUT);
    pinMode(SEG_G, OUTPUT);
    Serial.begin(9600);
}
</pre>
configuro los pines como entradas o salidas, además de iniciar la comunicación serial a una velocidad de 9600 baudios.
<pre lang="cpp">
void loop()
{
    estadosubo = digitalRead(sube);
    estadoparo = digitalRead(pausa);
    estadobajo = digitalRead(baja);

    // Botón de subir presionado
    if (estadosubo == LOW)
    {
       encenderApagar(LED_VERDE, LED_ROJO);      
       subirPiso();
      
    }      


    if (estadobajo == LOW )
    {
		encenderApagar(LED_VERDE, LED_ROJO);
        bajarPiso();

    }
  
  if (estadoparo == LOW )
    {
       encenderApagar(LED_ROJO, LED_VERDE);       
        mostrarPiso(pisoActual);
    }

    
    mostrarPiso(pisoActual);
}
</pre>
En el loop, ejecuto llamando las funciones que hice en el programa 
<pre lang="cpp">
void mostrarPiso(int piso)
{
    switch (piso)
    {
        case 1:
            subirUno(SEG_A, SEG_B, SEG_G, SEG_C, SEG_D, SEG_E, SEG_F);
            break;
        case 2:
            subirDos(SEG_A, SEG_B, SEG_G, SEG_C, SEG_D, SEG_E, SEG_F);
            break;
        case 3:
            subirTres(SEG_A, SEG_B, SEG_G, SEG_C, SEG_D, SEG_E, SEG_F);
            break;
        case 4:
            subirCuatro(SEG_A, SEG_B, SEG_G, SEG_C, SEG_D, SEG_E, SEG_F);
            break;
        case 5:
            subirCinco(SEG_A, SEG_B, SEG_G, SEG_C, SEG_D, SEG_E, SEG_F);
            break;
        default:
      		llegar(SEG_A, SEG_B, SEG_G, SEG_C, SEG_D, SEG_E, SEG_F);
            break;
    }
}
</pre>
La función mostrarPiso() se encarga de mostrar el piso actual en un display de siete segmentos. Dependiendo del valor de piso, se llama a diferentes funciones como subirUno(), subirDos(), etc., que encienden o apagan los segmentos del display para mostrar el número correspondiente.
<pre lang="cpp">
void subirPiso()
{	
 
    pisoActual++;

    // Realizar el proceso de subir al siguiente piso
    Serial.print("Montacargas subiendo al piso ");
    Serial.println(pisoActual);
    delay(tiempo);

    // Llegar al piso deseado
    Serial.print("Llego al piso ");
    Serial.println(pisoActual);
}
void bajarPiso()
{
  
    pisoActual--;

    // Realizar el proceso de bajar al siguiente piso
    Serial.print("Montacargas bajando al piso ");
    Serial.println(pisoActual);
    delay(tiempo);

    // Llegar al piso deseado
    Serial.print("Llego al piso ");
    Serial.println(pisoActual);
}

</pre>
Las funciones subirPiso() y bajarPiso() actualizan el valor de pisoActual, imprimen mensajes en el monitor serial simulando el proceso de subir o bajar al siguiente piso, y luego detienen el movimiento y apagan el LED verde.
<pre lang="cpp">

void encenderApagar(int leduno, int ledos)
{
    digitalWrite(leduno, HIGH);
    delay(1000);
    digitalWrite(ledos, LOW);
    delay(1000);
}

</pre>
La función encenderApagar, controla el funcionamiento del encendido y apagado de los leds en los casos de subida o bajada del montacargas
<pre lang="cpp">
void llegar(int A,int B, int G, int C ,int D,int E, int F){
    digitalWrite(A,1);
    digitalWrite(B,1);
    digitalWrite(C,1);
    digitalWrite(G,0);
    digitalWrite(D,1);
    digitalWrite(E,1);
    digitalWrite(F,1);
}


void subirUno(int A,int B, int G, int C ,int D,int E, int F){
    digitalWrite(A,0);
    digitalWrite(B,1);
    digitalWrite(C,1);
    digitalWrite(G,0);
    digitalWrite(D,0);
    digitalWrite(E,0);
    digitalWrite(F,0);
}



</pre>
Por último, hay varias funciones (llegar, subirUno, subirDos, etc.) que se utilizan para encender o apagar los segmentos del display de siete segmentos para mostrar los números del 0 al 5.
[![circuito.png](https://i.postimg.cc/sfbPLgcT/circuito.png)](https://postimg.cc/9ztqRVs9)
##  holaa
### chau 
