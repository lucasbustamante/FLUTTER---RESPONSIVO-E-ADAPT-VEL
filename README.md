# FLUTTER - APLICATIVOS RESPONSIVOS E ADAPTÁVEIS

Sempre que estamos desenvolvendo um aplicativo, normalmente o desenvolvemos para um único dispositivo,
mas não se destina a ser usado apenas em um único dispositivo, mas em diferentes dispositivos de 
diferentes tamanhos e em caso de flutter também nos fornece a facilidade de desenvolver para a web 
em o mesmo tempo. Portanto, temos que lidar com uma variedade de tamanhos diferentes. 
Aqui estaremos discutindo como lidar com esse problema.

Para lidar com este problema, estaremos usando a classe MediaQuery do Flutter. 
Esta aula nos fornece informações relacionadas ao tamanho da tela em que o aplicativo está sendo executado.
o atributo size fornece o tamanho, largura e altura do dispositivo.


Estaremos desenvolvendo um aplicativo simples que nos dirá em qual plataforma estamos e a largura do 
dispositivo. É apenas um aplicativo simples que nos ajudará a começar a usar aplicativos responsivos. 
Estaremos testando o aplicativo no flutter para a web para verificar sua capacidade de resposta.

Primeiro, inicializaremos o aplicativo em main.dart com um widget Home simples que iremos 
desenvolver em um arquivo DART separado chamado home.dart .

```dart
import 'package:flutter/material.dart';
import 'home.dart';

void main() {
runApp(MyApp());
}

class MyApp extends StatelessWidget {

// This widget is the root of your application.
@override
Widget build(BuildContext context) {
return MaterialApp(
debugShowCheckedModeBanner: false,
title: 'GeeksforGeeks',
home: Home(),
theme: ThemeData(primarySwatch: Colors.green),
);
}
}
```

No home.dart estaremos escrevendo algumas funções para definir os tamanhos dos diferentes dispositivos. 
Definimos as funções para verificar o tamanho do dispositivo. O MediaQuery.of (context) .size.width 
requer um contexto que é um contexto de construção, portanto, usaremos essas funções dentro da 
função de construção.

```dart
import 'package:flutter/material.dart';

double deviceSize(BuildContext context) => MediaQuery.of(context).size.width;

class Home extends StatelessWidget {
static bool isMobile(BuildContext context) =>
MediaQuery.of(context).size.width < 800;

static bool isTablet(BuildContext context) =>
MediaQuery.of(context).size.width >= 800 &&
MediaQuery.of(context).size.width < 1200;

static bool isDesktop(BuildContext context) =>
MediaQuery.of(context).size.width >= 1200;

@override
Widget build(BuildContext context) {
return Scaffold(
body: SafeArea(
child: Column(
children: [
Container(
width: double.infinity,
height: 50,
color: Colors.green,
child: Center(
child: Text(
'GeeksforGeeks',
style: TextStyle(color: Colors.white, fontSize: 18),
),
),
),
Expanded(
flex: 1,
child: isDesktop(context)
? Desktop()
: isTablet(context)
? Tablet()
: Mobile(),
)
],
),
),
);
}
}
```

Depois disso, definimos mais três widgets para lidar com tamanhos diferentes. 
Definimos os widgets no mesmo arquivo dart, mas para o desenvolvimento de widgets complexos, 
podemos fazer arquivos separados para esses widgets.

```dart
class Desktop extends StatelessWidget {
@override
Widget build(BuildContext context) {
return Center(child: Text('Desktop ${deviceSize(context).toInt()}'));
}
}
```
<p float="left">
  <img src="/images/image1.jpg" width="250" />
Modo desktop

```dart
class Tablet extends StatelessWidget {
@override
Widget build(BuildContext context) {
return Center(child: Text('Tablet ${deviceSize(context).toInt()}'));
}
}
```
<p float="left">
  <img src="/images/image2.jpg" width="250" />
Modo tablet

```dart
class Mobile extends StatelessWidget {
@override
Widget build(BuildContext context) {
return Center(child: Text('Mobile ${deviceSize(context).toInt()}'));
}
}
```
<p float="left">
  <img src="/images/image3.jpg" width="250" />
Modo mobile

Execute o aplicativo e ajuste a janela para ver as diferentes saídas.

Saída para tamanho da tela do celular:


Fonte: https://acervolima.com/flutter-aplicativos-responsivos-e-adaptaveis/
