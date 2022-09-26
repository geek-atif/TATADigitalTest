# TATADigitalTest

### A. Descriptive Questions:
  ##### 1. Can we nest the Scaffold widget? Why or Why not?
    It is recommended not to use nested scaffold and the scaffold was designed to be the single top-level container for a MaterialApp and it's typically not necessary to nest scaffolds. we should be using one Scaffold per page / screen.
  ##### 2. What are the different ways we can create a custom widget ?
    By Right Clicking on Widget:
    By Right-Clicking on the Particular widget -> Refactor -> Extract Flutter Widget (we can also use shortcut Ctrl+Alt+W)
![](images/one.jpg)
    Give it a name and then click on refactor.
![](images/two.jpg)
  ##### 3. How can I access platform(iOS or Android) specific code from Flutter?
     Future<void> responseFromNativeCode() async {
     String response = "";
     try {
      final String result = await platform.invokeMethod('helloFromNativeCode');
      response = result;
     } on PlatformException catch (e) {
      response = "Failed to Invoke: '${e.message}'.";
     }
     setState(() {
      _responseFromNativeCode = response;
     });
    }
  
   ````
    Full Code
    class MyApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return new MaterialApp(
        home: new HomePage(),
      );
    }
  }
  class HomePage extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return new Scaffold(
        appBar: new AppBar(
          title: const Text('Native Code from Dart'),
        ),
        body: new MyHomePage(),
      );
      }
     }
      class MyHomePage extends StatefulWidget {
        MyHomePage({Key key, this.title}) : super(key: key);
        final String title;
        @override
        _MyHomePageState createState() => new _MyHomePageState();
      }
      class _MyHomePageState extends State<MyHomePage> {
        static const platform = const MethodChannel('flutter.native/helper');
        String _responseFromNativeCode = 'Waiting for Response...';
        Future<void> responseFromNativeCode() async {
          String response = "";
          try {
            final String result = await platform.invokeMethod('helloFromNativeCode');
            response = result;
          } on PlatformException catch (e) {
            response = "Failed to Invoke: '${e.message}'.";
          }
          setState(() {
            _responseFromNativeCode = response;
          });
        }
        @override
        Widget build(BuildContext context) {
          return Material(
            child: Center(
              child: Column(
                mainAxisAlignment: MainAxisAlignment.spaceEvenly,
                children: [
                  RaisedButton(
                    child: Text('Call Native Method'),
                    onPressed: responseFromNativeCode,
                  ),
                  Text(_responseFromNativeCode),
                ],
              ),
            ),
          );
        }
    } 
   ```
    
   
