# Easy Routes

Route traffic the easy way.

---

## How to Use 

### Step 1

Include the below dependency in your `build.gradle` project.

```gradle
buildscript {
    repositories {
        google()
        jcenter()
        maven { url "https://newtronlabs.jfrog.io/artifactory/libs-release-local" }
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.5.2'
        classpath 'com.newtronlabs.android:plugin:4.0.5'
    }
}

allprojects {
    repositories {
        google()
        jcenter()
        maven { url "https://newtronlabs.jfrog.io/artifactory/libs-release-local" }
    }
}

subprojects {
    apply plugin: 'com.newtronlabs.android'
}
```

In the `build.gradle` for your app include:

```gradle
dependencies {
    compileOnly 'com.newtronlabs.easyroutes:easyroutes:4.0.0'
}
```


### Step 2

```java
public class MainActivity extends AppCompatActivity implements IRouteListener
{
    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        
        // Configure a route. More options are available.
        RouteManager.getInstance()
             .configureRoute(this, "127.0.0.1", IRouteManager.TRANSPORT_BLUETOOTH, this);
    }

    @Override
    public void onRouteLost(String address, @IRouteManager.RouteCapability int cap)
    {
        Log.e("EasyRoutes", "Route Lost.");
    }

    @Override
    public void onRouteTeardown(String address, @IRouteManager.RouteCapability int cap)
    {
        Log.e("EasyRoutes", "Route Toredown.");
    }

    @Override
    public void onRouteAvailable(String address, @IRouteManager.RouteCapability int cap)
    {
        Log.e("EasyRoutes", "Route Setup Success.");
    }

    @Override
    public void onRouteSetupFailed(String address, @IRouteManager.RouteCapability int cap)
    {
        Log.e("EasyRoutes", "Route Setup Failed.");
    }
}
```

---

## Support Us
Please support the continued development of these libraries. We host and develop these libraries for free. Any support is deeply appriciated. Thank you!

<p align="center">
  <img src="https://drive.google.com/uc?id=1rbY8qjxvWU8GQgaqDrOY4-fYOWobQKk3" width="200" height="200" title="Support us" alt="Support us">
</p>

<p align="center">
  <strong>BTC Address:</strong> 39JmAfnNhaEPKz5wjQjQQj4jcv9BM11NQb
</p>

---

## License
https://gist.github.com/NewtronLabs/216f45db2339e0bc638e7c14a6af9cc8

## Contact

solutions@newtronlabs.com
