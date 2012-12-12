JuegoFinal
==========

import pilas
import sys
sys.path.insert(0, "..")
from pilas.actores import Bomba
pilas.iniciar(gravedad=(0, 0))

#----------------Menu------------------------

class EscenaDeMenu(pilas.escena.Base):

    def __init__(self):
        pilas.escena.Base.__init__(self)

    def iniciar(self):
        pilas.fondos.Pasto()

        opciones = [
  	    ('Comenzar a jugar', self.comenzar),		    
            ('Salir', self.salir)]

        self.menu = pilas.actores.Menu(opciones)

    def comenzar(self):
        pilas.cambiar_escena(EscenaDeJuego())

    def salir(self):
        import sys
        sys.exit(0)

#-------------------------Juego----------------------------
class EscenaDeJuego(pilas.escena.Base):

    def __init__(self):
        pilas.escena.Base.__init__(self)

    def iniciar(self):
        def crear_mapa():
            mapa = pilas.actores.Mapa(filas=15, columnas=20)
            #...........Grilla...........
            grilla = pilas.imagenes.cargar_grilla("grillas/plataformas_10_10.png", 10, 10)
            grilla.x = 200
            grilla.y = 200
            mapa = pilas.actores.Mapa(grilla)

            # Pinta todo el suelo
            for columna in range(0, 20):
                mapa.pintar_bloque(16, columna, 1)

            mapa.pintar_bloque(13, 3, 0)
            mapa.pintar_bloque(13, 4, 1)
            mapa.pintar_bloque(13, 5, 1)
            mapa.pintar_bloque(13, 6, 1)
            mapa.pintar_bloque(13, 7, 1)
            mapa.pintar_bloque(13, 8, 1)
            mapa.pintar_bloque(13, 9, 1)
            mapa.pintar_bloque(13, 10, 1)
            mapa.pintar_bloque(13, 11, 1)
            mapa.pintar_bloque(13, 12, 1)
            mapa.pintar_bloque(13, 13, 1)
            mapa.pintar_bloque(13, 14, 1)
            mapa.pintar_bloque(13, 15, 1)
            mapa.pintar_bloque(13, 16, 2)

            mapa.pintar_bloque(10, 0, 0)
            mapa.pintar_bloque(10, 1, 1)
            mapa.pintar_bloque(10, 2, 1)
            mapa.pintar_bloque(10, 3, 1)
            mapa.pintar_bloque(10, 4, 1)
            mapa.pintar_bloque(10, 5, 2)
            mapa.pintar_bloque(10, 8, 0)
            mapa.pintar_bloque(10, 9, 1)
            mapa.pintar_bloque(10, 10, 1)
            mapa.pintar_bloque(10, 11, 1)
            mapa.pintar_bloque(10, 12, 2)
            mapa.pintar_bloque(10, 15, 0)
            mapa.pintar_bloque(10, 16, 1)
            mapa.pintar_bloque(10, 17, 1)
            mapa.pintar_bloque(10, 18, 1)
            mapa.pintar_bloque(10, 19, 2)

            mapa.pintar_bloque(7, 0, 0)
            mapa.pintar_bloque(7, 1, 1)
            mapa.pintar_bloque(7, 2, 1)
            mapa.pintar_bloque(7, 3, 1)
            mapa.pintar_bloque(7, 4, 1,)
            mapa.pintar_bloque(7, 5, 1)
            mapa.pintar_bloque(7, 6, 1)
            mapa.pintar_bloque(7, 7, 2)
            mapa.pintar_bloque(7, 12, 0)
            mapa.pintar_bloque(7, 13, 1)
            mapa.pintar_bloque(7, 14, 1)
            mapa.pintar_bloque(7, 15, 1)
            mapa.pintar_bloque(7, 16, 1)
            mapa.pintar_bloque(7, 17, 1)
            mapa.pintar_bloque(7, 18, 1)
            mapa.pintar_bloque(7, 19, 2)  
            
            return mapa      

        #..........Actor.........        
        mapa = crear_mapa()
        actor = pilas.actores.Martian(mapa)
        actor.y = -180
        actor.x = -260
        actor.radio_de_colision = 30
        actor.escala = 1
        pilas.fondos.Tarde()

        #..........Temporzador..........
        t = pilas.actores.Temporizador()
        t.x = -300
        t.y = 220
        def funcion_callback():
            pilas.avisar("Temporizador: el tiempo se acabo!")
        t.ajustar(60, funcion_callback)
        t.iniciar()

        #..........puntaje........
        puntaje = pilas.actores.Puntaje()
        texto = pilas.actores.Texto('Puntaje:')
        texto.x = 200
        texto.y = 220
        puntaje.x = 270
        puntaje.y = 220

        #..........Monedas..........
        moneda01 = pilas.actores.Moneda()
        moneda01.x = -200
        moneda01.y = -80
        moneda02 = pilas.actores.Moneda()
        moneda02.x = -150
        moneda02.y = -80
        moneda03 = pilas.actores.Moneda()
        moneda03.x = -100
        moneda03.y = -80
        moneda04 = pilas.actores.Moneda()
        moneda04.x = -50
        moneda04.y = -80
        moneda05 = pilas.actores.Moneda()
        moneda05.x = 0
        moneda05.y = -80	
        moneda06 = pilas.actores.Moneda()
        moneda06.x = 50
        moneda06.y = -80
        moneda07 = pilas.actores.Moneda()
        moneda07.x = 100
        moneda07.y = -80
        moneda08 = pilas.actores.Moneda()
        moneda08.x = 150
        moneda08.y = -80
        moneda09 = pilas.actores.Moneda()
        moneda09.x = 200
        moneda09.y = -80


        moneda10 = pilas.actores.Moneda()
        moneda10.x = -310
        moneda10.y = 20
        moneda11 = pilas.actores.Moneda()
        moneda11.x = -260
        moneda11.y = 20
        moneda12 = pilas.actores.Moneda()
        moneda12.x = -210
        moneda12.y = 20
        moneda13 = pilas.actores.Moneda()
        moneda13.x = -160
        moneda13.y = 20
        moneda14 = pilas.actores.Moneda()
        moneda14.x = -60
        moneda14.y = 20
        moneda15 = pilas.actores.Moneda()
        moneda15.x = -10
        moneda15.y = 20
        moneda16 = pilas.actores.Moneda()
        moneda16.x = 40
        moneda16.y = 20
        moneda17 = pilas.actores.Moneda()
        moneda17.x = 90
        moneda17.y = 20
        moneda18 = pilas.actores.Moneda()
        moneda18.x = 190
        moneda18.y = 20
        moneda19 = pilas.actores.Moneda()
        moneda19.x = 240
        moneda19.y = 20
        moneda20 = pilas.actores.Moneda()
        moneda20.x = 290
        moneda20.y = 20
        moneda21 = pilas.actores.Moneda()
        moneda21.x = 340
        moneda21.y = 20


        moneda22 = pilas.actores.Moneda() 
        moneda22.x = -300        
        moneda22.y = -180
        moneda23 = pilas.actores.Moneda()
        moneda23.x = -250
        moneda23.y = -180
        moneda24 = pilas.actores.Moneda()
        moneda24.x = -200
        moneda24.y = -180
        moneda25 = pilas.actores.Moneda()
        moneda25.x = -150
        moneda25.y = -180
        moneda26 = pilas.actores.Moneda()
        moneda26.x = -100
        moneda26.y = -180
        moneda27 = pilas.actores.Moneda()
        moneda27.x = -50
        moneda27.y = -180
        moneda28 = pilas.actores.Moneda()
        moneda28.x = 0
        moneda28.y = -180
        moneda29 = pilas.actores.Moneda()
        moneda29.x = 50
        moneda29.y = -180
        moneda30 = pilas.actores.Moneda()
        moneda30.x = 100
        moneda30.y = -180
        moneda31 = pilas.actores.Moneda()
        moneda31.x = 150
        moneda31.y = -180
        moneda32 = pilas.actores.Moneda()
        moneda32.x = 200
        moneda32.y = -180
        moneda33 = pilas.actores.Moneda()
        moneda33.x = 250
        moneda33.y = -180
        moneda34 = pilas.actores.Moneda()
        moneda34.x = 300
        moneda34.y = -180
          

        moneda35 = pilas.actores.Moneda()
        moneda35.x = -300
        moneda35.y = 130
        moneda36 = pilas.actores.Moneda()
        moneda36.x = -250
        moneda36.y = 130
        moneda37 = pilas.actores.Moneda()
        moneda37.x = -200
        moneda37.y = 130
        moneda38 = pilas.actores.Moneda()
        moneda38.x = -150
        moneda38.y = 130
        moneda39 = pilas.actores.Moneda()
        moneda39.x = -100
        moneda39.y = 130
        moneda40 = pilas.actores.Moneda()
        moneda40.x = 100
        moneda40.y = 130
        moneda41 = pilas.actores.Moneda()
        moneda41.x = 150
        moneda41.y = 130
        moneda42 = pilas.actores.Moneda()
        moneda42.x = 200
        moneda42.y = 130
        moneda43 = pilas.actores.Moneda()
        moneda43.x = 250
        moneda43.y = 130
        moneda44 = pilas.actores.Moneda()
        moneda44.x = 300
        moneda44.y = 130
        
        lista_de_monedas = [ moneda01, moneda02, moneda03, moneda04, moneda05, moneda06, moneda07, moneda08, moneda09, moneda10, moneda11, moneda12, moneda13, moneda14, moneda15, moneda16, moneda17, moneda18, moneda19, moneda20, moneda21, moneda22, moneda23, moneda24, moneda25, moneda26, moneda27, moneda28, moneda29, moneda30, moneda31, moneda32, moneda33, moneda34, moneda35, moneda36, moneda37, moneda38, moneda39, moneda40, moneda41, moneda42, moneda43, moneda44]

        def cuando_colisionan(lista_de_monedas, actor):
            lista_de_monedas.eliminar()      
            puntaje.aumentar(5)        
        pilas.escena_actual().colisiones.agregar(lista_de_monedas, actor, cuando_colisionan)


        class MonedaConMovimiento(Bomba):

            def __init__(self, x=0, y=0):
                Bomba.__init__(self, x, y)

                self.circulo = pilas.fisica.Circulo(x, y, 20, restitucion=1, friccion=0, amortiguacion=0)
                self.imitar(self.circulo)

                self._empujar()

            def _empujar(self):
                dx = 1
                dy = 1
                self.circulo.impulsar(dx * 10, dy * 10)

        bomba_1 = MonedaConMovimiento()
        bomba_2 = MonedaConMovimiento(x=150, y=0)
        bomba_3 = MonedaConMovimiento(x=0, y=100)
        bomba_4 = MonedaConMovimiento(x=100, y=50)

        lista_de_bombas = [bomba_1, bomba_2, bomba_3, bomba_4]

        def cuando_colisionan(pingu, bomba):
            bomba.explotar()
            pingu.eliminar()
            pilas.avisar("PERDISTE: presiona la tecla q")
        pilas.mundo.colisiones.agregar(actor, lista_de_bombas, cuando_colisionan)

          
        pilas.eventos.pulsa_tecla.conectar(self.cuando_pulsa_tecla)
    def cuando_pulsa_tecla(self, evento):
        if evento.texto == u'q':
            pilas.cambiar_escena(EscenaDeMenu())


	
# Carga la nueva escena
pilas.cambiar_escena(EscenaDeMenu())
pilas.ejecutar()
