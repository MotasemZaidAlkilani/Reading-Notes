# Amazon s3
Amazon Simple storage service is an object stotage servies that offers industry-leading scalability ,security , and performance. Customers of all sizes and industries can use amaszon s3 to store and protect any amont of data for a range of use cases , such as data lakes ,webistes , mobile application , backup and restore archive .
_____

## features of amazon s3

### 1- Storage classes 
Amazon S3 offers a range of storage classes designed for different use cases.

### 2- storage managment 
feature that u can use to manage costs , meet reulatory requirments , reduce latency , and save multiple distinct copies of your data compliance requirements.

### 3- Access management 
provides for audition and manging access to your buckets and objects . by default , s3 buckets and the objects in them are private . you have access only to the s3 resources that u create . to grant granular resource permissions that support your specific use case or to audit the permissions of your amazon s3 resources.

### 4 - Data processing 
to transform data and trigger workflows to automate a variety of other processing activities.

### 5- storage logging and monitoring 
amazon provies logging and monitoring tools that you can use to monitor and control how your amazon s3 resources are being used.

### 6- Analytics and insights 
amazon s3 offers features to help you gain visbility into your storage usage , which empowers you to better unserstand , analyze and optimize yout storage at scalre.

### 7- strong consisteny
provides strong read-after-write consistency for put and delete requests of objects in your amazon s3 bucket in all aws regions . this behavior applies to both writes of new objects as well as put request that overwrite existing objects and delete requests.
____
## How Amazon S3 Works
is an object storage servies that stores data as objects within buckets . an object is a file and any metadata that desvrives the files . a bucket is a container for objects .

to store your data in s3 , you first create a bucket and specify a bucket name and aws region . then , you upload your data to that bucket as objects in S3 . each object has has a key , which is the unique identifier for the object with th bucket.

### buckets 
is a container for objects stored in s3 . uou can store any number of obbjects in a bucket and can have up to 100 buckets in your account.

### objects 
are the fundamental entites stored in s3 . objects consist of object data and metadata . the metadata is set of name-value pairs that descrive the object .

### keys 
object key is the unique identifier for an object within a bucket .every object in a bucket has exactly one key 

_________
## Storage 
the amplfy storage category provides an interface for managing user content for your app in public , protected , provate storage buckets . the storage category comes with defaul built-in support for amazon simple storage service .

### Prerequisites 
android application with android api 16 or above 

### provision backend storage 
to start provisioning storage resources in the backend , go to the directory project :

```
amplify add storage

```

enter the following when prompted :

```
'Content (Image , audio ,Video, etc.)'

'Yes'

'Defaul configuration'

'Username'

'No,I am done'

'S3firendName'

'storagebucketname'

'Auth and quest users'

'create/update,read ,delete'

'create/update, read, delete'

'No'

```

then push :
```
amplfiy push

```

### install amplify libraries 
build gradle (module:app)

```
dependencies {

implementation 'com.amplifyframework:aws-storage-s3:1.35.4'

implementation 'com.amplifyframwork:aws-auth-cognito:1.35.4'

}

```
### Initialize Amplify Storage 

```
Amplify.addPlugin(new AWSCognitoAuthPlugin());
Amplify.addPlugin(new AWSS3StoragePlugin());

```

_______________
## Uploading data to your bucket 

``` 
priavte void uploadFile(){
  file exampleFile=new File(getApplicationContext().getFilesDir(),"ExampleKey");
  
  try {
     BufferedWriter writer =new BufferedWriter(new FileWriter(exampleFile));
     writer.append("example file contents");
     writer.close();
  catch (Excepton e) {
     Log.e("MyAmplifyApp","Upload failed ",exception);
     }
     
     Amplify.Storage.uploadFile(
             "ExampleKey",
              exampleFile,
              result -> Log.i("MyAmplifyApp","Successfully uploaded :" + result.getKey()),
              storageFailure -> Log.e("MyAmplifyApp","Upload failed", storageFailure)));
              
 ```
 
 __________
