### B. Coding Questions:
  ##### 1.  Refactor the code below so that the children will wrap to the next line when the display width is small for them to fit.?
    ```
    import 'package:flutter/material.dart';
    class LongStringWidget extends StatelessWidget {
      const LongStringWidget({Key? key}) : super(key: key);

      @override
      Widget build(BuildContext context) {
        return SafeArea(
          child: Scaffold(
            body: Padding(
              padding: const EdgeInsets.all(8.0),
              child: Wrap(
                spacing: 6.0,
                runSpacing: 6.0,
                children: const [
                  Chip(label: Text('I')),
                  Chip(label: Text('am')),
                  Chip(label: Text('looking')),
                  Chip(label: Text('for')),
                  Chip(label: Text('a')),
                  Chip(label: Text('job')),
                  Chip(label: Text('and')),
                  Chip(label: Text('I')),
                  Chip(label: Text('need')),
                  Chip(label: Text('a')),
                  Chip(label: Text('job')),
                ],
              ),
            ),
          ),
        );
      }
    }
    ```
Output    
![](images/three.jpg)
