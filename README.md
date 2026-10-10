
import 'package:flutter/material.dart';
import 'package:flutter_test/flutter_test.dart';
import 'package:counter_testing_app/main.dart';

void main() {
  group('Counter Application Widget Tests', () {

    testWidgets('Initial counter value is zero',
        (WidgetTester tester) async {
      await tester.pumpWidget(const MyApp());

      expect(find.text('0'), findsOneWidget);
    });

    testWidgets('Increment button increases counter by one',
        (WidgetTester tester) async {
      await tester.pumpWidget(const MyApp());

      await tester.tap(find.byIcon(Icons.add));
      await tester.pump();

      expect(find.text('1'), findsOneWidget);
    });

    testWidgets('Decrement button decreases counter by one',
        (WidgetTester tester) async {
      await tester.pumpWidget(const MyApp());

      await tester.tap(find.byIcon(Icons.add));
      await tester.pump();

      await tester.tap(find.byIcon(Icons.remove));
      await tester.pump();

      expect(find.text('0'), findsOneWidget);
    });

    testWidgets('Counter never goes below zero',
        (WidgetTester tester) async {
      await tester.pumpWidget(const MyApp());

      await tester.tap(find.byIcon(Icons.remove));
      await tester.pump();

      expect(find.text('0'), findsOneWidget);
    });

    testWidgets('Counter text displays the correct value',
        (WidgetTester tester) async {
      await tester.pumpWidget(const MyApp());

      final counterFinder =
          find.byKey(const ValueKey('counterValue'));

      expect(counterFinder, findsOneWidget);
      expect(tester.widget<Text>(counterFinder).data, '0');

      await tester.tap(find.byIcon(Icons.add));
      await tester.pump();

      expect(tester.widget<Text>(counterFinder).data, '1');
    });
  });
}
