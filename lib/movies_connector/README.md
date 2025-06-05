# movies_connector SDK

## Installation
```sh
flutter pub get firebase_data_connect
flutterfire configure
```
For more information, see [Flutter for Firebase installation documentation](https://firebase.google.com/docs/data-connect/flutter-sdk#use-core).

## Data Connect instance
Each connector creates a static class, with an instance of the `DataConnect` class that can be used to connect to your Data Connect backend and call operations.

### Connecting to the emulator

```dart
String host = 'localhost'; // or your host name
int port = 9399; // or your port number
MoviesConnector.instance.dataConnect.useDataConnectEmulator(host, port);
```

You can also call queries and mutations by using the connector class.
## Queries

### ListMovies
#### Required Arguments
```dart
// No required arguments
MoviesConnector.instance.listMovies().execute();
```

#### Optional Arguments
We return a builder for each query. For ListMovies, we created `ListMoviesBuilder`. For queries and mutations with optional parameters, we return a builder class.
The builder pattern allows Data Connect to distinguish between fields that haven't been set and fields that have been set to null. A field can be set by calling its respective setter method like below:
```dart
class ListMoviesVariablesBuilder {
  ...
 
  ListMoviesVariablesBuilder orderByRating(OrderDirection? t) {
   _orderByRating.value = t;
   return this;
  }
  ListMoviesVariablesBuilder orderByReleaseYear(OrderDirection? t) {
   _orderByReleaseYear.value = t;
   return this;
  }
  ListMoviesVariablesBuilder limit(int? t) {
   _limit.value = t;
   return this;
  }

  ...
}
MoviesConnector.instance.listMovies()
.orderByRating(orderByRating)
.orderByReleaseYear(orderByReleaseYear)
.limit(limit)
.execute();
```

#### Return Type
`execute()` returns a `QueryResult<ListMoviesData, ListMoviesVariables>`
```dart
/// Result of an Operation Request (query/mutation).
class OperationResult<Data, Variables> {
  OperationResult(this.dataConnect, this.data, this.ref);
  Data data;
  OperationRef<Data, Variables> ref;
  FirebaseDataConnect dataConnect;
}

/// Result of a query request. Created to hold extra variables in the future.
class QueryResult<Data, Variables> extends OperationResult<Data, Variables> {
  QueryResult(super.dataConnect, super.data, super.ref);
}

final result = await MoviesConnector.instance.listMovies();
ListMoviesData data = result.data;
final ref = result.ref;
```

#### Getting the Ref
Each builder returns an `execute` function, which is a helper function that creates a `Ref` object, and executes the underlying operation.
An example of how to use the `Ref` object is shown below:
```dart
final ref = MoviesConnector.instance.listMovies().ref();
ref.execute();

ref.subscribe(...);
```


### ListMoviesByGenre
#### Required Arguments
```dart
String genre = ...;
MoviesConnector.instance.listMoviesByGenre(
  genre: genre,
).execute();
```

#### Optional Arguments
We return a builder for each query. For ListMoviesByGenre, we created `ListMoviesByGenreBuilder`. For queries and mutations with optional parameters, we return a builder class.
The builder pattern allows Data Connect to distinguish between fields that haven't been set and fields that have been set to null. A field can be set by calling its respective setter method like below:
```dart
class ListMoviesByGenreVariablesBuilder {
  ...
   ListMoviesByGenreVariablesBuilder orderByRating(OrderDirection? t) {
   _orderByRating.value = t;
   return this;
  }
  ListMoviesByGenreVariablesBuilder orderByReleaseYear(OrderDirection? t) {
   _orderByReleaseYear.value = t;
   return this;
  }
  ListMoviesByGenreVariablesBuilder limit(int? t) {
   _limit.value = t;
   return this;
  }

  ...
}
MoviesConnector.instance.listMoviesByGenre(
  genre: genre,
)
.orderByRating(orderByRating)
.orderByReleaseYear(orderByReleaseYear)
.limit(limit)
.execute();
```

#### Return Type
`execute()` returns a `QueryResult<ListMoviesByGenreData, ListMoviesByGenreVariables>`
```dart
/// Result of an Operation Request (query/mutation).
class OperationResult<Data, Variables> {
  OperationResult(this.dataConnect, this.data, this.ref);
  Data data;
  OperationRef<Data, Variables> ref;
  FirebaseDataConnect dataConnect;
}

/// Result of a query request. Created to hold extra variables in the future.
class QueryResult<Data, Variables> extends OperationResult<Data, Variables> {
  QueryResult(super.dataConnect, super.data, super.ref);
}

final result = await MoviesConnector.instance.listMoviesByGenre(
  genre: genre,
);
ListMoviesByGenreData data = result.data;
final ref = result.ref;
```

#### Getting the Ref
Each builder returns an `execute` function, which is a helper function that creates a `Ref` object, and executes the underlying operation.
An example of how to use the `Ref` object is shown below:
```dart
String genre = ...;

final ref = MoviesConnector.instance.listMoviesByGenre(
  genre: genre,
).ref();
ref.execute();

ref.subscribe(...);
```


### ListGenres
#### Required Arguments
```dart
// No required arguments
MoviesConnector.instance.listGenres().execute();
```



#### Return Type
`execute()` returns a `QueryResult<ListGenresData, void>`
```dart
/// Result of an Operation Request (query/mutation).
class OperationResult<Data, Variables> {
  OperationResult(this.dataConnect, this.data, this.ref);
  Data data;
  OperationRef<Data, Variables> ref;
  FirebaseDataConnect dataConnect;
}

/// Result of a query request. Created to hold extra variables in the future.
class QueryResult<Data, Variables> extends OperationResult<Data, Variables> {
  QueryResult(super.dataConnect, super.data, super.ref);
}

final result = await MoviesConnector.instance.listGenres();
ListGenresData data = result.data;
final ref = result.ref;
```

#### Getting the Ref
Each builder returns an `execute` function, which is a helper function that creates a `Ref` object, and executes the underlying operation.
An example of how to use the `Ref` object is shown below:
```dart
final ref = MoviesConnector.instance.listGenres().ref();
ref.execute();

ref.subscribe(...);
```


### GetMovieById
#### Required Arguments
```dart
String id = ...;
MoviesConnector.instance.getMovieById(
  id: id,
).execute();
```



#### Return Type
`execute()` returns a `QueryResult<GetMovieByIdData, GetMovieByIdVariables>`
```dart
/// Result of an Operation Request (query/mutation).
class OperationResult<Data, Variables> {
  OperationResult(this.dataConnect, this.data, this.ref);
  Data data;
  OperationRef<Data, Variables> ref;
  FirebaseDataConnect dataConnect;
}

/// Result of a query request. Created to hold extra variables in the future.
class QueryResult<Data, Variables> extends OperationResult<Data, Variables> {
  QueryResult(super.dataConnect, super.data, super.ref);
}

final result = await MoviesConnector.instance.getMovieById(
  id: id,
);
GetMovieByIdData data = result.data;
final ref = result.ref;
```

#### Getting the Ref
Each builder returns an `execute` function, which is a helper function that creates a `Ref` object, and executes the underlying operation.
An example of how to use the `Ref` object is shown below:
```dart
String id = ...;

final ref = MoviesConnector.instance.getMovieById(
  id: id,
).ref();
ref.execute();

ref.subscribe(...);
```


### GetActorById
#### Required Arguments
```dart
String id = ...;
MoviesConnector.instance.getActorById(
  id: id,
).execute();
```



#### Return Type
`execute()` returns a `QueryResult<GetActorByIdData, GetActorByIdVariables>`
```dart
/// Result of an Operation Request (query/mutation).
class OperationResult<Data, Variables> {
  OperationResult(this.dataConnect, this.data, this.ref);
  Data data;
  OperationRef<Data, Variables> ref;
  FirebaseDataConnect dataConnect;
}

/// Result of a query request. Created to hold extra variables in the future.
class QueryResult<Data, Variables> extends OperationResult<Data, Variables> {
  QueryResult(super.dataConnect, super.data, super.ref);
}

final result = await MoviesConnector.instance.getActorById(
  id: id,
);
GetActorByIdData data = result.data;
final ref = result.ref;
```

#### Getting the Ref
Each builder returns an `execute` function, which is a helper function that creates a `Ref` object, and executes the underlying operation.
An example of how to use the `Ref` object is shown below:
```dart
String id = ...;

final ref = MoviesConnector.instance.getActorById(
  id: id,
).ref();
ref.execute();

ref.subscribe(...);
```


### GetCurrentUser
#### Required Arguments
```dart
// No required arguments
MoviesConnector.instance.getCurrentUser().execute();
```



#### Return Type
`execute()` returns a `QueryResult<GetCurrentUserData, void>`
```dart
/// Result of an Operation Request (query/mutation).
class OperationResult<Data, Variables> {
  OperationResult(this.dataConnect, this.data, this.ref);
  Data data;
  OperationRef<Data, Variables> ref;
  FirebaseDataConnect dataConnect;
}

/// Result of a query request. Created to hold extra variables in the future.
class QueryResult<Data, Variables> extends OperationResult<Data, Variables> {
  QueryResult(super.dataConnect, super.data, super.ref);
}

final result = await MoviesConnector.instance.getCurrentUser();
GetCurrentUserData data = result.data;
final ref = result.ref;
```

#### Getting the Ref
Each builder returns an `execute` function, which is a helper function that creates a `Ref` object, and executes the underlying operation.
An example of how to use the `Ref` object is shown below:
```dart
final ref = MoviesConnector.instance.getCurrentUser().ref();
ref.execute();

ref.subscribe(...);
```


### GetMovieInfoForUser
#### Required Arguments
```dart
String movieId = ...;
MoviesConnector.instance.getMovieInfoForUser(
  movieId: movieId,
).execute();
```



#### Return Type
`execute()` returns a `QueryResult<GetMovieInfoForUserData, GetMovieInfoForUserVariables>`
```dart
/// Result of an Operation Request (query/mutation).
class OperationResult<Data, Variables> {
  OperationResult(this.dataConnect, this.data, this.ref);
  Data data;
  OperationRef<Data, Variables> ref;
  FirebaseDataConnect dataConnect;
}

/// Result of a query request. Created to hold extra variables in the future.
class QueryResult<Data, Variables> extends OperationResult<Data, Variables> {
  QueryResult(super.dataConnect, super.data, super.ref);
}

final result = await MoviesConnector.instance.getMovieInfoForUser(
  movieId: movieId,
);
GetMovieInfoForUserData data = result.data;
final ref = result.ref;
```

#### Getting the Ref
Each builder returns an `execute` function, which is a helper function that creates a `Ref` object, and executes the underlying operation.
An example of how to use the `Ref` object is shown below:
```dart
String movieId = ...;

final ref = MoviesConnector.instance.getMovieInfoForUser(
  movieId: movieId,
).ref();
ref.execute();

ref.subscribe(...);
```


### SearchAll
#### Required Arguments
```dart
int minYear = ...;
int maxYear = ...;
double minRating = ...;
double maxRating = ...;
String genre = ...;
MoviesConnector.instance.searchAll(
  minYear: minYear,
  maxYear: maxYear,
  minRating: minRating,
  maxRating: maxRating,
  genre: genre,
).execute();
```

#### Optional Arguments
We return a builder for each query. For SearchAll, we created `SearchAllBuilder`. For queries and mutations with optional parameters, we return a builder class.
The builder pattern allows Data Connect to distinguish between fields that haven't been set and fields that have been set to null. A field can be set by calling its respective setter method like below:
```dart
class SearchAllVariablesBuilder {
  ...
 
  SearchAllVariablesBuilder input(String? t) {
   _input.value = t;
   return this;
  }

  ...
}
MoviesConnector.instance.searchAll(
  minYear: minYear,
  maxYear: maxYear,
  minRating: minRating,
  maxRating: maxRating,
  genre: genre,
)
.input(input)
.execute();
```

#### Return Type
`execute()` returns a `QueryResult<SearchAllData, SearchAllVariables>`
```dart
/// Result of an Operation Request (query/mutation).
class OperationResult<Data, Variables> {
  OperationResult(this.dataConnect, this.data, this.ref);
  Data data;
  OperationRef<Data, Variables> ref;
  FirebaseDataConnect dataConnect;
}

/// Result of a query request. Created to hold extra variables in the future.
class QueryResult<Data, Variables> extends OperationResult<Data, Variables> {
  QueryResult(super.dataConnect, super.data, super.ref);
}

final result = await MoviesConnector.instance.searchAll(
  minYear: minYear,
  maxYear: maxYear,
  minRating: minRating,
  maxRating: maxRating,
  genre: genre,
);
SearchAllData data = result.data;
final ref = result.ref;
```

#### Getting the Ref
Each builder returns an `execute` function, which is a helper function that creates a `Ref` object, and executes the underlying operation.
An example of how to use the `Ref` object is shown below:
```dart
int minYear = ...;
int maxYear = ...;
double minRating = ...;
double maxRating = ...;
String genre = ...;

final ref = MoviesConnector.instance.searchAll(
  minYear: minYear,
  maxYear: maxYear,
  minRating: minRating,
  maxRating: maxRating,
  genre: genre,
).ref();
ref.execute();

ref.subscribe(...);
```


### ListMoviesByPartialTitle
#### Required Arguments
```dart
String input = ...;
MoviesConnector.instance.listMoviesByPartialTitle(
  input: input,
).execute();
```



#### Return Type
`execute()` returns a `QueryResult<ListMoviesByPartialTitleData, ListMoviesByPartialTitleVariables>`
```dart
/// Result of an Operation Request (query/mutation).
class OperationResult<Data, Variables> {
  OperationResult(this.dataConnect, this.data, this.ref);
  Data data;
  OperationRef<Data, Variables> ref;
  FirebaseDataConnect dataConnect;
}

/// Result of a query request. Created to hold extra variables in the future.
class QueryResult<Data, Variables> extends OperationResult<Data, Variables> {
  QueryResult(super.dataConnect, super.data, super.ref);
}

final result = await MoviesConnector.instance.listMoviesByPartialTitle(
  input: input,
);
ListMoviesByPartialTitleData data = result.data;
final ref = result.ref;
```

#### Getting the Ref
Each builder returns an `execute` function, which is a helper function that creates a `Ref` object, and executes the underlying operation.
An example of how to use the `Ref` object is shown below:
```dart
String input = ...;

final ref = MoviesConnector.instance.listMoviesByPartialTitle(
  input: input,
).ref();
ref.execute();

ref.subscribe(...);
```

## Mutations

### UpsertUser
#### Required Arguments
```dart
String username = ...;
MoviesConnector.instance.upsertUser(
  username: username,
).execute();
```



#### Return Type
`execute()` returns a `OperationResult<UpsertUserData, UpsertUserVariables>`
```dart
/// Result of an Operation Request (query/mutation).
class OperationResult<Data, Variables> {
  OperationResult(this.dataConnect, this.data, this.ref);
  Data data;
  OperationRef<Data, Variables> ref;
  FirebaseDataConnect dataConnect;
}

final result = await MoviesConnector.instance.upsertUser(
  username: username,
);
UpsertUserData data = result.data;
final ref = result.ref;
```

#### Getting the Ref
Each builder returns an `execute` function, which is a helper function that creates a `Ref` object, and executes the underlying operation.
An example of how to use the `Ref` object is shown below:
```dart
String username = ...;

final ref = MoviesConnector.instance.upsertUser(
  username: username,
).ref();
ref.execute();
```


### AddFavoritedMovie
#### Required Arguments
```dart
String movieId = ...;
MoviesConnector.instance.addFavoritedMovie(
  movieId: movieId,
).execute();
```



#### Return Type
`execute()` returns a `OperationResult<AddFavoritedMovieData, AddFavoritedMovieVariables>`
```dart
/// Result of an Operation Request (query/mutation).
class OperationResult<Data, Variables> {
  OperationResult(this.dataConnect, this.data, this.ref);
  Data data;
  OperationRef<Data, Variables> ref;
  FirebaseDataConnect dataConnect;
}

final result = await MoviesConnector.instance.addFavoritedMovie(
  movieId: movieId,
);
AddFavoritedMovieData data = result.data;
final ref = result.ref;
```

#### Getting the Ref
Each builder returns an `execute` function, which is a helper function that creates a `Ref` object, and executes the underlying operation.
An example of how to use the `Ref` object is shown below:
```dart
String movieId = ...;

final ref = MoviesConnector.instance.addFavoritedMovie(
  movieId: movieId,
).ref();
ref.execute();
```


### DeleteFavoritedMovie
#### Required Arguments
```dart
String movieId = ...;
MoviesConnector.instance.deleteFavoritedMovie(
  movieId: movieId,
).execute();
```



#### Return Type
`execute()` returns a `OperationResult<DeleteFavoritedMovieData, DeleteFavoritedMovieVariables>`
```dart
/// Result of an Operation Request (query/mutation).
class OperationResult<Data, Variables> {
  OperationResult(this.dataConnect, this.data, this.ref);
  Data data;
  OperationRef<Data, Variables> ref;
  FirebaseDataConnect dataConnect;
}

final result = await MoviesConnector.instance.deleteFavoritedMovie(
  movieId: movieId,
);
DeleteFavoritedMovieData data = result.data;
final ref = result.ref;
```

#### Getting the Ref
Each builder returns an `execute` function, which is a helper function that creates a `Ref` object, and executes the underlying operation.
An example of how to use the `Ref` object is shown below:
```dart
String movieId = ...;

final ref = MoviesConnector.instance.deleteFavoritedMovie(
  movieId: movieId,
).ref();
ref.execute();
```


### AddReview
#### Required Arguments
```dart
String movieId = ...;
int rating = ...;
String reviewText = ...;
MoviesConnector.instance.addReview(
  movieId: movieId,
  rating: rating,
  reviewText: reviewText,
).execute();
```



#### Return Type
`execute()` returns a `OperationResult<AddReviewData, AddReviewVariables>`
```dart
/// Result of an Operation Request (query/mutation).
class OperationResult<Data, Variables> {
  OperationResult(this.dataConnect, this.data, this.ref);
  Data data;
  OperationRef<Data, Variables> ref;
  FirebaseDataConnect dataConnect;
}

final result = await MoviesConnector.instance.addReview(
  movieId: movieId,
  rating: rating,
  reviewText: reviewText,
);
AddReviewData data = result.data;
final ref = result.ref;
```

#### Getting the Ref
Each builder returns an `execute` function, which is a helper function that creates a `Ref` object, and executes the underlying operation.
An example of how to use the `Ref` object is shown below:
```dart
String movieId = ...;
int rating = ...;
String reviewText = ...;

final ref = MoviesConnector.instance.addReview(
  movieId: movieId,
  rating: rating,
  reviewText: reviewText,
).ref();
ref.execute();
```


### UpdateReview
#### Required Arguments
```dart
String movieId = ...;
int rating = ...;
String reviewText = ...;
MoviesConnector.instance.updateReview(
  movieId: movieId,
  rating: rating,
  reviewText: reviewText,
).execute();
```



#### Return Type
`execute()` returns a `OperationResult<UpdateReviewData, UpdateReviewVariables>`
```dart
/// Result of an Operation Request (query/mutation).
class OperationResult<Data, Variables> {
  OperationResult(this.dataConnect, this.data, this.ref);
  Data data;
  OperationRef<Data, Variables> ref;
  FirebaseDataConnect dataConnect;
}

final result = await MoviesConnector.instance.updateReview(
  movieId: movieId,
  rating: rating,
  reviewText: reviewText,
);
UpdateReviewData data = result.data;
final ref = result.ref;
```

#### Getting the Ref
Each builder returns an `execute` function, which is a helper function that creates a `Ref` object, and executes the underlying operation.
An example of how to use the `Ref` object is shown below:
```dart
String movieId = ...;
int rating = ...;
String reviewText = ...;

final ref = MoviesConnector.instance.updateReview(
  movieId: movieId,
  rating: rating,
  reviewText: reviewText,
).ref();
ref.execute();
```


### DeleteReview
#### Required Arguments
```dart
String movieId = ...;
MoviesConnector.instance.deleteReview(
  movieId: movieId,
).execute();
```



#### Return Type
`execute()` returns a `OperationResult<DeleteReviewData, DeleteReviewVariables>`
```dart
/// Result of an Operation Request (query/mutation).
class OperationResult<Data, Variables> {
  OperationResult(this.dataConnect, this.data, this.ref);
  Data data;
  OperationRef<Data, Variables> ref;
  FirebaseDataConnect dataConnect;
}

final result = await MoviesConnector.instance.deleteReview(
  movieId: movieId,
);
DeleteReviewData data = result.data;
final ref = result.ref;
```

#### Getting the Ref
Each builder returns an `execute` function, which is a helper function that creates a `Ref` object, and executes the underlying operation.
An example of how to use the `Ref` object is shown below:
```dart
String movieId = ...;

final ref = MoviesConnector.instance.deleteReview(
  movieId: movieId,
).ref();
ref.execute();
```

