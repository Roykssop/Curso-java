Nuevo proyecto con blank activity

En carpeta res , tenemos creada una carpeta menu conteniendo un xml.
  En esa carpeta podemos agregar items que según el parámetro showsactions "never || always" se va a mostrar en los 3 puntos o como boton en la toolbar

En método onCreateOptionsMenu
    El inflate relaciona el archivo xml , con el objeto menu de esa activity en particular
    
En el Activity_main.xml se puede usar <include layout="@layout/content_main" /> , para reutilizar partes de otros layouts
  Luego desde la clase activity main haciendo setContentView al layout padre , nos permitirá acceder también a los elementos
   del layout incluído
   
  Toolbar toolbar = (Toolbar) findViewById(R.id.toolbar);
  setSupportActionBar(toolbar);
  
  Hace que funcione como un action bar ( los 3 puntos )
