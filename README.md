Please take a few minutes and let us know how we are doing by filling out this survey: https://goo.gl/forms/97TYeG6Wx5CA4lBV2

---

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
        classpath 'com.android.tools.build:gradle:2.3.3'
        classpath "com.newtronlabs.android:plugin:1.1.0"
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
    provided 'com.newtronlabs.easyroutes:easyroutes:2.0.0'
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

Easy Routes binaries and source code can only be used in accordance with Freeware license. That is, freeware may be used without payment, but may not be modified. The developer of Easy Routes retains all rights to change, alter, adapt, and/or distribute the software. Easy Routes is not liable for any damages and/or losses incurred during the use of Easy Routes.

You may not decompile, reverse engineer, pull apart, or otherwise attempt to dissect the source code, algorithm, technique or other information from the binary code of Easy Routes unless it is authorized by existing applicable law and only to the extent authorized by such law. In the event that such a law applies, user may only attempt the foregoing if: (1) user has contacted Newtron Labs to request such information and Newtron Labs has failed to respond in a reasonable time, or (2) reverse engineering is strictly necessary to obtain such information and Newtron Labs has failed to reply. Any information obtained by user from Newtron Labs may be used only in accordance to the terms agreed upon by Newtron Labs and in adherence to Newtron Labs confidentiality policy. Such information supplied by Newtron Labs and received by user shall not be disclosed to a third party or used to create a software substantially similar to the technique or expression of the Newtron Labs Easy Routes software.

You are solely responsible for determining the appropriateness of using Easy Routes and assume any risks associated with Your use of Easy Routes. In no event and under no legal theory, whether in tort (including negligence), contract, or otherwise, unless required by applicable law (such as deliberate and grossly negligent acts) or agreed to in writing, shall Newtron Labs be liable to You for damages, including any direct, indirect, special, incidental, or consequential damages of any character arising as a result of this License or out of the use or inability to use the Easy Routes (including but not limited to damages for loss of goodwill, work stoppage, computer failure or malfunction, or any and all other commercial damages or losses), even if Newtron Labs has been advised of the possibility of such damages. 

## Contact

contact@newtronlabs.com
