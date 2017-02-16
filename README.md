# httpLibrary

### Demonstration of use

**Gradle Dependency**

 - Add this to your app build.gradle:

```
dependencies {
    compile 'com.scantity.ScHttpLibrary:ScHttpLibrary:1.0.0'
    }
```

 **Java Code**
 
 - Add Simple String parameters
  ```
  HashMap<String, String> stringParameters = new HashMap<>();
        stringParameters.put("name", "abc");
        stringParameters.put("age", "25");
  ```
 
  - Add Header values
  
```
HashMap<String, String> headerParameters = new HashMap<>();
        headerParameters.put("headerKey1", "headerValue1");
        headerParameters.put("headerKey2", "headerValue2");
```
 
   - Add File Parameters (Images,  docs, text ..etc.)
   ```
   String filePath = Environment.getExternalStorageDirectory()+"/DCIM/test_image.jpg";
        HashMap<String, File> fileParameters = new HashMap<>();
        fileParameters.put("fileKey", new File(filePath));
   ```
 
 - Final Calling
 
```
new HttpRequestResponse(MainActivity.this)
                .setOnResultListener(new HttpRequestResponse.ResultListener() {
                    @Override
                    public void onPostExecute(JSONObject json, String requestCode) {
                        Log.d(TAG, "json=="+json.toString());
                    }
                })
                .setUrl("http://requestb.in/11xjkya1")
                .setHeaderParameters(headerParameters)
                .setStringParameters(stringParameters)
                .setFileParameters(fileParameters)
                .setMethod(HttpRequestResponse.Method.POST)
                .isDialogShown(true, "")
                .setSocketTimeOut(30)
                .executeMethod();
```

