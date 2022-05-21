# Graph connection 

## One To Many relationship

to make relation between two table , u must use @hasMany , as for example below :

```
type Post @model {
  id: ID!
  title: String!
  comments: [Comment] @hasMany
}

type Comment @model {
  id: ID!
  content: String!
}
```
_______________

 to retrieve the related Comment records from the source Post record :
 
 ```
 mutation CreatePost {
  createPost(input: {title: "Hello World!!"}) {
    title
    id
    comments {
      items {
        id
        content
      }
    }
  }
}
```

___________

You can customize the specific secondary index used for the "has many" relationship. First, configure a secondary index using @index. Then, pass in the secondary index name indexName parameter and the respective fields which match the connected index.

```
type Post @model {
  id: ID!
  title: String!
  comments: [Comment] @hasMany(indexName: "byPost", fields: ["id"])
}

type Comment @model {
  id: ID!
  postID: ID! @index(name: "byPost", sortKeyFields: ["content"])
  content: String!
}
```

__________
In this case, the Comment type has a postID field added to store the reference of Post record. The id field referenced by @hasMany is the id on the Post type. @hasMany can then get the connected Comment object by querying the Comment table's secondary index "byPost" with this postID:

```
mutation CreatePost {
  createPost(input: {title: "Hello world!"}) {
    comments {
      items {
        postID
        content
        id
      }
    }
    title
    id
  }
}
```
____________

## Completable future 
 is used for asynchronous programming. Asynchronous programming means writing non-blocking code. It runs a task on a separate thread than the main application thread and notifies the main thread about its progress, completion or failure.
 
 In this way, the main thread does not block or wait for the completion of the task. Other tasks execute in parallel. Parallelism improves the performance of the program.
 
 A CompletableFuture is a class in Java. It belongs to java.util.cocurrent package. It implements CompletionStage and Future interface.
 
 For example, we can create an instance of this class with a no-arg constructor to represent some future result, hand it out to the consumers, and complete it at some time in the future using the complete method. The consumers may use the get method to block the current thread until this result is provided.
 ____________
 
 In the example below, we have a method that creates a CompletableFuture instance, then spins off some computation in another thread and returns the Future immediately.
 
 ```
 public Future<String> calculateAsync() throws InterruptedException {
    CompletableFuture<String> completableFuture = new CompletableFuture<>();

    Executors.newCachedThreadPool().submit(() -> {
        Thread.sleep(500);
        completableFuture.complete("Hello");
        return null;
    });

    return completableFuture;
}
```
Notice that the calculateAsync method returns a Future instance.

Also observe that the get method throws some checked exceptions, namely ExecutionException (encapsulating an exception that occurred during a computation) and InterruptedException (an exception signifying that a thread executing a method was interrupted):

```
Future<String> completableFuture = calculateAsync();

// ... 

String result = completableFuture.get();
assertEquals("Hello", result);
```
_________
 
 

