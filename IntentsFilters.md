# Intent Filters 
your app can perform an action that might be useful , your app should be prepared to respond to action requests by specifying the appropriate intent filter in your application.

note : to allow other apps to start your activity in this way , you need to add  <intent-filter> element in your manifest file for the corresponding <activity> element.

note : when your app is installed on a device , the system identifies your intent filters and adds the information to an internal catalog of intents supported by installed apps.
  
  ## add an intent filter 
  In order to properly define which intents your activity can handle , each intent filter you add should be as specific as possible in terms of the type of action and data :
  
  ### Action 
      naming the action to perform . usually one of the platform-defined values as ACTION_SEND or ACTION_VIEW
   
  note : Specify this in your intent filter with the <action> element .
  
  ### data 
   description of the data associated with the intent.
  
 note : specify this in your intent filter with the <data> element .Using one or more attributes in this element.
  
  ### category
  provides an additional way to characterize the activity handling the intent , usually related to the user gesture or location from which it's started.
  
  note : specify this in your intent filter with <category> element.
  
  edample , here an activity with an intent filter that handles the ACTION_SEND intent when the data type is either text or an image :
  
  ``` 
  <activity android:name ="sharedActivity"
            <intent-filter>
                  <action android:name="android.intent.action.SEND"/>
                  <category android:name="android.intent.category.DEFAULT"/>
                  <data android:mimeType="text/plain"/>
                  <data android:mimeType="image/*"/>
            </intent-filter>
  </activity>
  ```
  
  __________
  ## Handle the intent in your activty
  as your activity starts , call getIntent() to retieve the Intent that started the activity . you can do so at any time during the lifecycle of the activity .
  
  ```
  @Override 
  protected void onCreate(Bundle savedInstanceState) {
           super.onCreate(savedInstanceState);
   
            setContentView(R.layout.main);
  
            Intent intent=getIntent();
            Uri data=intent.getData();
  
            if(intent.getType().indexOf("image/") != -1) {
              // handle intents with image data
           else if (intent.getType().equals("text/plain")){
             // handle intents with text 
               }
  } 
  
  ```
____________
  ## return a result 
  ```
  Intent result =new Intent('com.example.RESULT_ACTION",Uri.parse("content://result_uri));
  setResult(Activity.RESULT_OK,result);
  finish();
  
  ```
  _______________
  ## Intents 
  
  . start an activity 
     represesnt a single screen in an app . u can start a new instance of an activity by passing an intent to startActivity().
  
  .starting service 
    A service is a component that performs opertions in the background withour user interface . You can start a service to perform a one time opertion by passing an intent to startService()
  
  .Delivering a broadcast
  is message that any app can receive . the system delivers various broadcasts for system events , such as when the system boots up or the device starts charging . you can delivert a broadcast to other apps by passing an intent to sendBroadcast()
  
 ____________
  ## Intent types 
  
  . Explicit intents : specifiy which application will satisfy the intent , by supplying either the target app's package name or a fully-qualify component class name 
  
  . Impliciy intents : do not name a specific component , but instead declare a general action to perform , which allows a component from another app to handle it .
  
  __________
  ## building an intent
  an Intent object carreis information that the android system uses to determine which component to start , plus information that she recipient component uses in order to properly perform the action 
  
  -component name : the name of component to start , it;s the critical piece of information that makes an intent explicit , meaning that the intent should be delivered only to the app component defined by the component name .
  
  -Action : A string that specifies the generic action to perform 
  
  in the case of a broadcast intent , this is the action that took place and is being reported .
  
  -ACTION_VIEW 
  use this action in an intent with startActivity() , when you have some information that an activity can show to the user
  
  -ACTION_SEND
  as the share intent , you should use this in an intent with startActivity() when you have some data that the user can share through another app.
  
  __________
  
  
