# Easy Routes

Route traffic the easy way.

---

## How to Use 

### Step 1

Include the below dependency in your `build.gradle` project.

```gradle
buildscript {
    repositories {
        jcenter()
        maven { url "http://code.newtronlabs.com:8081/artifactory/libs-release-local" }
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.5.2'
        classpath 'com.newtronlabs.android:plugin:4.0.0'
    }
}

allprojects {
    repositories {
        jcenter()
        maven { url "http://code.newtronlabs.com:8081/artifactory/libs-release-local" }
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

## License
https://gist.github.com/NewtronLabs/216f45db2339e0bc638e7c14a6af9cc8

## Contact

solutions@newtronlabs.com
