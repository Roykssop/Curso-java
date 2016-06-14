BroadCast receiver, recibe eventos de sistema
  Por ejemplo cuando hay wifi, con esto evito tener una aplicación que este haciendo un while
  
  Si hago un BR que escucha la llamada por ejemplo y mi aplicacion atiende el evento de llamada entrante lo que debe hacer 
  no hay que hacer nada que tome mucho tiempo porque retraza la llamada.
  En el manifest hay que declarar el broadcast receiver
  Poner el intent filter dentro del tag receiver


   (intent datos del evento)
   
   
           Bundle info = intent.getExtras(); // Obtengo los datos de extras
        if(info!=null){
            Object[] pduArray = (Object[]) info.get("pdus"); 
            
            // Creo array de SMS messages y tiene la misma cantidad de items
            // Se convierte el array de bytes en objetos sms messages
            SmsMessage[] messages = new SmsMessage[pduArray.length];
            for(int i=0;i<pduArray.length;i++)
            {
                messages[i]=SmsMessage.createFromPdu((byte[])pduArray[i]);
                Log.d("br", "Msg de:" + messages[i].getOriginatingAddress());
                Log.d("br","Texto:"+messages[i].getMessageBody());
            }
        }
