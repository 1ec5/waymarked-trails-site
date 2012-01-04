.. subpage:: about About the Map

Este mapa muestra las rutas para pat�n en l�nea se�alizadas alrededor del mundo. Se basa en los datos del proyecto `OpenStreetMap`_ (OSM). OSM es un mapa mundial que se puede modificar libremente donde cualquiera puede participar. Eso significa que este mapa para bicicletas no est� completo, y tambi�n significa que usted puede contribuir mediante la adici�n de nuevas rutas y la correcci�n de errores en las existentes. Para obtener m�s informaci�n acerca de OpenStreetMap, consulte la `Gu�a del principiante`_.

Este mapa s�lo proporciona una capa superpuesta con las rutas en bicicleta. Fue dise�ado para el mapa de OSM Mapnik como mapa base, pero deber�a trabajar junto con otros mapas en l�nea. Por favor, lea la `Pol�tica de uso`_ antes de usarlo en su propio website.

.. _OpenStreetMap: http://www.openstreetmap.org
.. _`Gu�a del principiante`: http://wiki.openstreetmap.org/wiki/ES:Beginners%27_Guide
.. _`Pol�tica de uso`: copyright

.. subpage:: rendering Representaci�n de datos del OSM

Las rutas para pat�n en l�nea en el OSM deben ingresarse como relaciones. C�mo funciona esto se describe en detalle en la p�gina de etiquetas (tags) de la wiki del OSM sobre `Rutas Suizas de Pat�n en l�nea`_ (en ingl�s). Este mapa muestra todas las relaciones que tienen por lo menos las siguientes etiquetas: 

::

    type = route|superroute
    route = inline_skates

La clasificaci�n (y por lo tanto el color de la ruta en el mapa) se determina a partir de la etiqueta de ``red``. 

La etiqueta o sigla en este mapa es estimada a partir de las etiquetas del OSM en el siguiente orden:

  1. Si una etiqueta ``ref`` existe, hace una etiqueta de texto en este mapa con los datos de la etiqueta ref.
  2. Si una etiqueta ``name`` existe, obtiene una referencia de all�, primero utilizando s�lo las letras may�sculas y en su defecto mediante el uso de las primeras letras del nombre.
     *Tenga en cuenta al mapear: adivinar una referencia por el nombre de la ruta es b�sicamente un truco para mostrar algo en las rutas mal etiquetadas. Utilizar una referencia de ruta expl�cita siempre que sea posible.*
  3. Darse por vencido.

El mapa tambi�n es compatible con `relaciones jer�rquicas`_.

.. _`Rutas Suizas de Pat�n en l�nea`: http://wiki.openstreetmap.org/wiki/EN:Switzerland/InlineNetwork
.. _`relaciones jer�rquicas`: rendering/hierarchies


.. subpage:: rendering/hierarchies Relaciones Jer�rquicas

El mapa tambi�n soporta relaciones anidadas, p.ej. relaciones que a su vez contienen relaciones. En este momento hay dos usos principales para las relaciones jer�rquicas: son utilizadas para dividir las rutas muy largas (p.ej. E1_) o se utilizan para evitar la duplicaci�n del trabajo en el que dos rutas van por el mismo camino (v�ase, por ejemplo, la suiza `Via Francigena`_ que forma parte de la Europea `Via Romea Francigena`_). En el primer caso las sub-relaciones no son rutas completas en s� mismas y no deben por lo tanto, aparecer en el mapa.

C�mo es tratada exactamente una subrelaci�n para el procesado, depende de la etiqueta de la red:

  * Si la relaci�n madre e hija comparten la misma etiqueta de red, la relaci�n hija se considera que es s�lo una etapa de la relaci�n madre. Por lo tanto, su ruta se a�ade a la relaci�n madre y la relaci�n hija no se muestra en el mapa.
  * Si la etiqueta de red de una relaci�n madre e hija son diferentes, las relaciones se supone que son independientes. La ruta de la relaci�n hija se a�ade a la relaci�n madre y las dos relaciones se muestran en el mapa.

*Nota:* siempre se puede inspeccionar subrelaciones a trav�s del navegador. S�lo tiene que seleccionar la relaci�n madre y una lista seleccionable de subrelaciones es mostrada.

.. _E1: /route/European%20walking%20route%20E1
.. _`Via Francigena`: /route/Via%20Francigena,%20Swiss%20part
.. _`Via Romea Francigena`: /route/Via%20Romea%20Francigena
