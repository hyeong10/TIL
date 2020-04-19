```kotlin
class RetrofitCreator {

    companion object {
        private fun defaultRetrofit(): Retrofit {
            return Retrofit.Builder()
                .baseUrl("<url>")
                .addConverterFactory(GsonConverterFactory.create())
                .addCallAdapterFactory(RxJava2CallAdapterFactory.create())
                .client(createOkHttpClient())
                .build()
        }

        fun <T> create(service: Class<T>): T {
            return defaultRetrofit()
                .create(service)
        }

        private fun createOkHttpClient(): OkHttpClient {
            val interceptor = HttpLoggingInterceptor()
            if (BuildConfig.DEBUG) {
                interceptor.level = HttpLoggingInterceptor.Level.BODY
            } else {
                interceptor.level = HttpLoggingInterceptor.Level.NONE
            }

            return OkHttpClient.Builder()
                .addNetworkInterceptor(interceptor)
                .build()
        }
    }
}
```

```kotlin
//gson
/*
data class <dataName> (
  @SerializedName("<arrayName>")
  var <arrayName>: ArrayList<<arrayType>> = ArrayList(),
  @SerializedName("<nullableName>")
  var <nullableName>: <nullableName>? = null,
  @SerializedName("varName")
  var <varName>: <varType> = 0
)
*/

data class pProduct(
    @SerializedName("userId")
    var userId: Int = 0,
    @SerializedName("products")
    var products: ArrayList<Int> = ArrayList()
)

data class Product (
    @SerializedName("id")
    var id: Int = 0,
    @SerializedName("name")
    var name: String? = null,
    @SerializedName("price")
    var price: Int = 0,
    @SerializedName("thumbnail")
    var thumbnail: String? = null
)

data class PageImpl_User (
    @SerializedName("content")
    var content: ArrayList<gUser> = ArrayList(),
    @SerializedName("firstPage")
    var firstPage: Boolean = false,
    @SerializedName("lastPage")
    var lastPage: Boolean = false,
    @SerializedName("number")
    var number: Int = 0,
    @SerializedName("numberOfElements")
    var numberOfElement: Int = 0,
    @SerializedName("size")
    var size: Int = 0,
    /*@SerializedName("sort")
    var sort: Int = 0,*/
    @SerializedName("totalElements")
    var totalElements: Int = 0,
    @SerializedName("totalPages")
    var totalPages: Int = 0
)

```

```kotlin
interface RestService {
  /*
  @<Method>("<url>")
  fun <funcName>(
    @Path("<pathName>") <pathName> : <pathType>,
    @Query("<queryName>") <queryName> : <queryType>,
    @Body <bodyName>: <bodyType>
  ): Call<<ResponseType>>
  */
  
  @GET("/v1/users/{userId}/friends/list")
  fun getPageImpl_User(
    @Path("userId") userId: Int,
    @Query("page") page: Int,
    @Query("size") size: Int
  ): Call<PageImpl_User>
  
  @POST("/{id}/name")
  fun postName(
    @Path("id") id: Int,
    @Query("page") page: Int,
    @Body name: String
  ): Call<ResponseBody>
}
```

```kotlin
val service = RetrofitCreator.create(RestService::class.java)

service.<restServiceFuncName>(userId).enqueue(object : Callback<<responseType>> {
  override fun onResponse(call: Call<<responseType>>?, response: Response<<responseType>>) {
    //var content = response.body()
  }

  override fun onFailure(call: Call<<responseType>>?, t: Throwable) {
    //
  }
})
```
