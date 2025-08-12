import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'ثقافة وتاريخ',
      theme: ThemeData(primarySwatch: Colors.teal),
      home: HomePage(),
    );
  }
}

class HomePage extends StatelessWidget {
  final List<String> culturalFacts = [
    'هل تعلم أن اللغة العربية تحتوي على أكثر من 12 مليون كلمة؟',
    'الفن الإسلامي يتميز بالزخرفة الهندسية المعقدة.',
  ];

  final List<String> historicalFacts = [
    'معركة بدر وقعت في السنة الثانية للهجرة.',
    'الحضارة الفرعونية بدأت قبل أكثر من 5000 سنة.',
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('ثقافة وتاريخ')),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            ElevatedButton(
              child: Text('معلومات ثقافية'),
              onPressed: () => Navigator.push(
                context,
                MaterialPageRoute(
                  builder: (context) => InfoPage(
                    title: 'معلومات ثقافية',
                    facts: culturalFacts,
                  ),
                ),
              ),
            ),
            SizedBox(height: 20),
            ElevatedButton(
              child: Text('معلومات تاريخية'),
              onPressed: () => Navigator.push(
                context,
                MaterialPageRoute(
                  builder: (context) => InfoPage(
                    title: 'معلومات تاريخية',
                    facts: historicalFacts,
                  ),
                ),
              ),
            ),
          ],
        ),
      ),
    );
  }
}

class InfoPage extends StatelessWidget {
  final String title;
  final List<String> facts;

  InfoPage({required this.title, required this.facts});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text(title)),
      body: ListView.builder(
        itemCount: facts.length,
        itemBuilder: (context, index) {
          return Card(
            margin: EdgeInsets.all(10),
            child: Padding(
              padding: EdgeInsets.all(15),
              child: Text(
                facts[index],
                style: TextStyle(fontSize: 18),
              ),
            ),
          );
        },
      ),
    );
  }
}
