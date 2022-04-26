 # Intents, Activities, and SharedPreferences
 ___
 ## Task
 set of activities that user can interact with when using application , for example when using whatsup u will cross alot of activities to send message ,or to go to specific screen to able to send message .
 ___
 ### lifecycle of task
 when the application starts its begin from home , when click at button that move u to another screen in home , new activity will starts and will be above home activity , so it will be like stack , like books . when activity stops , will return to activity that below it in stack order. activities will never rearranged , they just push or poped .
 
 note : the root activities will declare as intent-filter with both ACTION_MAIN and CATEGORY_LAUNCHER , that make them unique , make them unique  those only activities that can application start in them.
 
 note : in android 11 the application finish the activity, so u when want to open it again will start from cold state ,but in android 12 application will move it to background , so that will make it starts quickly compared to 11.
 
 note : if u want to not finish the activity as in android 11 , and move to background , u can use AndroidX Activity API , which is onBackPressed().
 ___
 ### Background and foreground tasks
 when u starts new task or go to home screen , the tasks will go to background , and will stay for example the home avtivity in foreground .
 ___
 ### Multiple activity instances
 because the activities in the back stack are never rearranged, if your app allows users to start a particular activity from more than one activity, a new instance of that activity is created and pushed onto the stack (rather than bringing any previous instance of the activity to the top). As such, one activity in your app might be instantiated multiple timesMultiple activity instances
 
 example : activity A is on , if activity A starts activity B , activity B is on and activity A stop , if user back , then Activity A is back to on ,and activity B popped from the stack and destroyed.
 
 note : Activities can be instantiated multiple times, even from other tasks.
 ___
 ### Manage tasks
 u can manage activities in manifest file , by changing its attrbutes . here the attributes that u can change:
 
1-taskAffinity

2-launchMode

3-allowTaskReparenting

4-clearTaskOnLaunch

5-alwaysRetainTaskState

6-finishOnTaskLaunch
___
### Defining launch mode
u define launch by two ways :

#### 1- in manifest file using the <activity> element's launchMode attribute
  
  launchMode 
  
  -standard : he system creates a new instance of the activity in the task from which it was started and routes the intent to it
  
  -singleTask: f an instance of the activity already exists at the top of the current task, the system routes the intent to that instance through a call to its onNewIntent() method, rather than creating a new instance of the activity
  
  -singleInstance : The system creates the activity at the root of a new task or locates the activity on an existing task with the same affinity. If an instance of the activity already exists and is at the root of the task, the system routes the intent to existing instance through a call to its onNewIntent() method, rather than creating a new instance. Meanwhile all of the other activities on top of it are destroyed
  
  -singleInstance : Same as "singleTask", except that the system doesn't launch any other activities into the task holding the instance
  

#### 2-using intent flags 
The flags you can use to modify the default behavior are:
  
  -FLAG_ACTIVITY_NEW_TASK
  
  -FLAG_ACTIVITY_SINGLE_TOP
  
  -FLAG_ACTIVITY_CLEAR_TOP
  
  ___
 ## shared-preferences
 If you have a relatively small collection of key-values that you'd like to save, you should use the SharedPreferences APIs. A SharedPreferences object points to a file containing key-value pairs and provides simple methods to read and write them. Each SharedPreferences file is managed by the framework and can be private or shared
  
### How to create shared-preferences ?
  u can create it by calling methods :
  
  1-getSharedPreferences() :  Use this if you need multiple shared preference files identified by name, which you specify with the first parameter. You can call this from any Context in your app.
  
 2- getPreferences() :  Use this from an Activity if you need to use only one shared preference file for the activity. Because this retrieves a default shared preference file that belongs to the activity, you don't need to supply a name
  
 For example, the following code accesses the shared preferences file that's identified by the resource string :
  
  ```
  Context context = getActivity();
SharedPreferences sharedPref = context.getSharedPreferences(
        getString(R.string.preference_file_key), Context.MODE_PRIVATE);
  ```
  
Alternatively, if you need just one shared preference file for your activity, you can use the getPreferences() method:
  
  ```
 SharedPreferences sharedPref = getActivity().getPreferences(Context.MODE_PRIVATE);
```
  _____
  ### Write to shared preferences
  
  ```
  SharedPreferences sharedPref = getActivity().getPreferences(Context.MODE_PRIVATE);
SharedPreferences.Editor editor = sharedPref.edit();
editor.putInt(getString(R.string.saved_high_score_key), newHighScore);
editor.apply();
  ```
  ___
  ### Read from shared preferences
  
  ```
  SharedPreferences sharedPref = getActivity().getPreferences(Context.MODE_PRIVATE);
int defaultValue = getResources().getInteger(R.integer.saved_high_score_default_key);
int highScore = sharedPref.getInt(getString(R.string.saved_high_score_key), defaultValue);
  ```
  ___
 
