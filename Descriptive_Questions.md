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
  ##### 4. What is BuildContext? What is its importance?
    The BuildContext is the handle/pointer to the location of the particular widget in the widget tree. Note that every widget you create has its own BuildContext, and as a matter of fact, every widget should have its own BuildContext for them to locate themselves in the widget tree or reach out to the nearest ancestor widget.
    The BuildContext is the set of inputs that Flutter uses to create an instance of a widget. It includes properties on the Android and iOS platforms, as well as properties related to the current device and environment.
    Why Is BuildContext Important?
    There are many reasons why BuildContext is important. From locating widgets in the tree to interacting with RenderObjects, the context makes all of these interactions possible. It serves as the “bridge” between the widgets and rendering layer and is especially powerful for combining functionality or using information from one tree in another.
   
