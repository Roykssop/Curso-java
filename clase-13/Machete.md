<uses-permission
android:name="android.permission.RECEIVE_SMS"/>

___________________________________________________________________________________________

<receiver android:name=".MyBroadCastReceiver">
	<intent-filter>
  		<action android:name="android.provider.Telephony.SMS_RECEIVED"/>
	</intent-filter>
</receiver>

___________________________________________________________________________________________


Bundle info = intent.getExtras();
if(info!=null){
	Object[] pduArray = (Object[]) info.get("pdus");
	SmsMessage[] messages = new SmsMessage[pduArray.length];
	for(int i=0;i<pduArray.length;i++)
	{
		messages[i]=SmsMessage.createFromPdu((byte[])pduArray[i]);
		Log.d("br","Msg de:"+messages[i].getOriginatingAddress());
		Log.d("br","Texto:"+messages[i].getMessageBody());
	}	
}


___________________________________________________________________________________________









NotificationManager mNotificationManager = (NotificationManager) 
                                            context.getSystemService(Context.NOTIFICATION_SERVICE);

_________________________________________________________________________________________________________

int icon = R.mipmap.ic_launcher;
String tickerText = "Evento de sms";
long when = System.currentTimeMillis();

CharSequence contentTitle = "SMS";
CharSequence contentText = "Evento de sms";

Intent notificationIntent = new Intent(context,PantallaNotificacionActivity.class);

PendingIntent contentIntent = PendingIntent.getActivity(context, 0, notificationIntent, PendingIntent.FLAG_UPDATE_CURRENT);


_________________________________________________________________________________________________________

NotificationCompat.Builder  builder = new NotificationCompat.Builder(context);

Notification notification = builder.setContentIntent(contentIntent)
                      	.setSmallIcon(icon)
				.setTicker(tickerText)
				.setWhen(when)
		   		.setAutoCancel(true)
				.setContentTitle(contentTitle)
			      .setContentText(contentText)
				.build();

_________________________________________________________________________________________________________

mNotificationManager.notify(id, notification);



_________________________________________________________________________________________________________
_________________________________________________________________________________________________________










Intent takePictureIntent = new Intent(MediaStore.ACTION_IMAGE_CAPTURE);
startActivityForResult(takePictureIntent, 0);

_________________________________________________________________________________________________________


        Bundle extras = data.getExtras();
        // obtenemos un bitmap con una preview de la imagen tomada
        ImageView imageViewPreView=(ImageView)findViewById(R.id.imageViewPreView);
        Bitmap imageBitmap = (Bitmap) extras.get("data");
        // mostramos el bitmap
        imageViewPreView.setImageBitmap(imageBitmap);

_________________________________________________________________________________________________________
_________________________________________________________________________________________________________











private File getAlbumDir()
{
	String strPath = Environment.getExternalStorageDirectory()+"/Android/data/"+getPackageName()+"/Pictures";
	File path = new File (strPath);
	// creamos el directorio si no existe
	path.mkdirs();
	return path;
}

_________________________________________________________________________________________________________

private File createImageFile() throws IOException
{
	// creamos el nombre del archivo
	String timeStamp = new SimpleDateFormat("yyyyMMdd_HHmmss").format(new Date());
	String imageFileName = "foto_"+ timeStamp + ".jpg";
	// creamos el archivo
	File image = new File(getAlbumDir(), imageFileName);
	image.createNewFile();
	return image;
}


_________________________________________________________________________________________________________

File f = null;
f = createImageFile();
Intent takePictureIntent = new Intent(MediaStore.ACTION_IMAGE_CAPTURE);
takePictureIntent.putExtra(MediaStore.EXTRA_OUTPUT,Uri.fromFile(f));
startActivityForResult(takePictureIntent, 0);


_________________________________________________________________________________________________________


if (resultCode == RESULT_OK)
{
	Bitmap captureBmp = Media.getBitmap(getContentResolver(), Uri.fromFile(f));
	ImageView img=(ImageView) findViewById(R.id.imageViewPreView);
	img.setImageBitmap(captureBmp);
}

_________________________________________________________________________________________________________


<uses-permission
android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
