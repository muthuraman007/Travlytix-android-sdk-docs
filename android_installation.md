<link href="https://storage.googleapis.com/travlytix-web-sdk-doc/styles.css" rel="stylesheet"></link>

# Travlytix Android SDK vX.X.X - Installation Document

## **Install SDK**

To install the SDK, you need to follow these steps,

 Add the jcenter repository to your project level `build.gradle` file.

```
allprojects {
    repositories {
        ...
        jcenter()
    }
}
```

 Add the Travlytix SDK to your app level `build.gradle` file.

 ```
  implementation 'com.app.travlytix:travlytix:X.X.X'
 ```

## **Configure SDK**

To configure the SDK to work properly, you should follow these steps,
Add this line to intialise the SDK.
```
Travlytix.init(context, url, id);
```

| Parameters | Type | Required | Description 
:---| :---| :--- | :---
context | Context | yes | Application context. Used for SDK data handling, identify device information and locale.
url |String| yes| Travlytix Api endpoint url. Used to post data to api.
id | String | no| One-signal Id generated in app. Used for sending personalised push notifications.


To disable the travlytix events during your development time, you can set `true` to the below method. 

**Note:** For production release app, you should set `false` to the below method.

```
Travlytix.setDisableEvents(status);
```

| Parameters | Type | Required | Description |
|:---| :---| :--- | :---|
|status | boolean | yes | Set `true` to disable travlytix events. Set `false` to enable travlytix events.|


That's it. You have successfully completed the installation steps. Please refer the integration document next.

---