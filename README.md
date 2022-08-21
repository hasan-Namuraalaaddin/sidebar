# sidebar
import 'package:flutter/material.dart';
import 'package:google_nav_bar/google_nav_bar.dart';
import 'package:sidebar/sidebar.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Sidebar Ex',
      home: Home(),
    );
  }
}

class Home extends StatefulWidget {
  const Home({Key? key}) : super(key: key);

  @override
  State<Home> createState() => _HomeState();
}

class _HomeState extends State<Home> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      drawer: SideBar(),
      bottomNavigationBar:
      Container(
        color: Colors.teal,
        child: Padding(
          padding: const EdgeInsets.symmetric(
              horizontal: 15,
          vertical: 20,),
          child: GNav(
            backgroundColor: Colors.teal,
            color: Colors.white,
            activeColor: Colors.white,
            tabBackgroundColor: Colors.pink.shade800,
            gap: 8,
            padding: EdgeInsets.all(16),
            tabs: [
              GButton(icon: Icons.home,
              text:'Home',),
              GButton(icon: Icons.favorite_border,
              text:'Likes' ,),
              GButton(icon: Icons.search,
              text: 'Search',),
              GButton(icon: Icons.settings,
              text: 'Settings',),

            ],
          ),
        ),
      ),
      appBar: AppBar(
        backgroundColor: Colors.teal,
        title: Text(
          'Sidebar',
        ),
      ),
      body: Container(
        color: Colors.green[100],
        padding: EdgeInsets.all(10),
        child: GridView.count(
          crossAxisCount: 4,
          children: [
            MyMenu(title: 'Akademik',icon:Icons.account_balance ,
            color: Colors.brown,),
            MyMenu(title: 'information',icon:Icons.info ,
              color: Colors.blue,),
            MyMenu(title: 'place',icon:Icons.school ,
              color: Colors.orange,),
            MyMenu(title: 'personel',icon:Icons.person_pin ,
              color: Colors.green,),
            MyMenu(title: 'e-learning',icon:Icons.local_library ,
              color: Colors.red,),
            MyMenu(title: 'sec',icon:Icons.library_books ,
              color: Colors.teal,),
          ],
        ),
      ),
    );
  }
}

class MyMenu extends StatelessWidget {
  MyMenu({
    required this.title,
    required this.icon,
    required this.color,
  });
  final String title;
  final IconData icon;
  final MaterialColor color;
  @override
  Widget build(BuildContext context) {
    return Card(
      margin: EdgeInsets.all(8),
      child: InkWell(
        onTap: () {},
        splashColor: Colors.green,
        child: Center(
          child: Column(
            mainAxisSize: MainAxisSize.min,
            children: [
              Icon(
                icon,
                size: 70.0,
                color: color,
              ),
              Text(
                title,
                style: TextStyle(
                  fontSize: 17,
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
import 'package:flutter/material.dart';

class SideBar extends StatelessWidget {
  const SideBar({Key? key}) : super(key: key);
  @override
  Widget build(BuildContext context) {
    return Drawer(
     child: ListView(
       padding: EdgeInsets.zero,
       children: [
         UserAccountsDrawerHeader(
             accountName: Text('Emma canım',
               style: TextStyle(
               color: Colors.black,
               fontWeight: FontWeight.bold,
               fontSize: 20,
             ),),
             accountEmail: Text('hasan@gamil.com',
               style: TextStyle(
                 color: Colors.black,
                 fontWeight: FontWeight.bold,
                 fontSize: 15,
               ),),
             currentAccountPicture:CircleAvatar(
             child: ClipOval(
               child: Image.network('https://m.media-amazon.com/images/M/MV5BMjI4NjM1NDkyN15BMl5BanBnXkFtZTgwODgyNTY1MjE@._V1_.jpg',
             width: 90,
                 height: 90,
                 fit: BoxFit.cover,
              ),
         ),

         ),
           decoration: BoxDecoration(
             color: Colors.teal[100],
           ),
         ),
         ListTile(
           leading: Icon(
             Icons.favorite,
           ),
           title: Text(
             'Favorite',
           ),
           onTap: () {},
         ),
         Divider(),
         ListTile(
           leading: Icon(
             Icons.people,
           ),
           title: Text(
             'Friends',
           ),
           onTap: () {},
         ),
         Divider(),
         ListTile(
           leading: Icon(
             Icons.share,
           ),
           title: Text(
             'Share',
           ),
           onTap: () {},
         ),
         Divider(),
         ListTile(
           leading: Icon(
             Icons.notifications,
           ),
           title: Text(
             'Request',
           ),
           onTap: () {},
           trailing: Container(
             color: Colors.red,
             width: 20,
             height: 20,
             child: Center(
               child: Text('6', style:
               TextStyle(
                 color: Colors.white,
                 fontSize: 12,
               ),),
             ),
           ),
         ),
         Divider(),
         ListTile(
           leading: Icon(
             Icons.settings,
           ),
           title: Text(
             'Settings',
           ),
           onTap: () {},
         ),
         Divider(),
         ListTile(
           leading: Icon(
             Icons.description,
           ),
           title: Text(
             'Policies',
           ),
           onTap: () {},
         ),
         Divider(),
         ListTile(
           leading: Icon(
             Icons.exit_to_app,
           ),
           title: Text(
             'Exit',
           ),
           onTap: () {},
         ),
         Divider(),
       ],
     ),
    );
  }
}
