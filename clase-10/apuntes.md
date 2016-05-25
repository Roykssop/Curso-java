Temas:

1) Toolbar
    -- Back
    -- Share
    -- Search
    
2) Navigation drawer


1) Para el share
    Agregar en res/menu_main.xml
          <item
        android:id="@+id/menu_item_share"
        app:showAsAction="ifRoom"
        android:title="Share"
        app:actionProviderClass="android.support.v7.widget.ShareActionProvider" />
    
    Esto agrega un componente en el layout (boton de share) ,
    
        //Ponemos código para obtener el ShareActionProvider         
        MenuItem item = menu.findItem(R.id.menu_item_share); // obtengo el share action provider
        ShareActionProvider mShareActionProvider = (ShareActionProvider) MenuItemCompat.getActionProvider(item);

        Intent intent = new Intent(Intent.ACTION_SEND);
        intent.setType("text/plain");
        intent.putExtra(Intent.EXTRA_TEXT,"http://www.lslutnfra.com");
        mShareActionProvider.setShareIntent(intent);

2) Para search

  Implementar interface SearchView.OnQueryTextListener (en el activity main puede ser)
  Tiene 2 métodos 
    onquerytextchange (cuando se va tecleando algo), 
    onquerytextsubmit (cuando se da enter )
  
3) Back 

    Es sencillo
    
    
3) NavBar Drawer

  activity main, tiene el navbar y el content
    Drawer layout tiene 2 hijos
    Al navigation view le digo que layout tomar 
    
  Header tiene el imageview y 2 textview
  
  // Coment codigo
  
  Drawer layout es el que tiene el contenido y lo que sale de costado
  Nos traemos el objeto 
    DrawerLayout drawer = (DrawerLayout) findViewById(R.id.drawer_layout);
    
  Navigation view es toda la barra (el header solo la parte de arriba)
  
