Peticiones a web service

Desde nuestra pc, solicitamos una página, ej: www.google.com
Un servidor dns que contiene mapeadas las urls con sus respectivos ip, nos devuelve la ip de la página.
Con esa ip se hace una petición con un header get ( llamada request ).
El servidor la resuelve y nos devuelve un paquete http ( llamado response ).


Clase HTTP Manager es nuestra
  getStrDataByGet() 
    Obtener texto, obtiene los bytes y se formatean como un objeto string
  
  getBytesDatabyGet 
    conn obj httpurlconnection que tiene la información de la respuesta adentro, se le solicita un objeto input stream par apoder leerla
    Stream, es una conexión a un recurso ()
    buffer es un array de bytes donde se guarda lo que se va leyendo, y luego lo escribo con el stream de escritura
    devolver en el formato de array de bytes.
