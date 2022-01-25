# jobtask

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://flutter.dev/docs/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://flutter.dev/docs/cookbook)

For help getting started with Flutter, view our
[online documentation](https://flutter.dev/docs), which offers tutorials,
samples, guidance on mobile development, and a full API reference.
Column(
          children: [
            if (userData != null) ...[
              SizedBox(height: 25),
              CircleAvatar(
                radius: 70,
                // backgroundColor: Colors.black,
                backgroundImage:
                    Image.network(userData["photoUrl"].toString()).image,
              ),
              SizedBox(height: 25),
              Text(
                "Product Name: ${userData["productname"]}",
                style: TextStyle(fontSize: 20),
              ),
              SizedBox(height: 10),
              Text(
                "Description: ${userData["description"]}",
                style: TextStyle(fontSize: 20),
              ),
              SizedBox(height: 10),
              Text(
                "Price: ${userData["price"]}",
                style: TextStyle(fontSize: 20),
              ),
              IconButton(
                  onPressed: () {
                    Share.share(
                        "${userData["photoUrl"]}\n ${userData["productname"]}");
                  },
                  icon: Icon(Icons.share)),
              ElevatedButton(
                  onPressed: () {
                    launchRazorPay();
                  },
                  child: Text("Pay Now"))
            ]
          ],
        ),

        await FirebaseAuth.instance.verifyPhoneNumber(
                    phoneNumber: '+91 ${number.text}',
                    verificationCompleted: (phoneAuthCredential) {
                      // PhoneAuthCredential phoneAuthCredential = phoneAuthCredential.
                    },
                    verificationFailed: (error) {
                      print(error);
                    },
                    codeSent: (verificationId, [forceResendingToken]) {
                      this.verificationId = verificationId;
                      ScaffoldMessenger.maybeOf(context)!
                          .showSnackBar(SnackBar(content: Text("sms sent")));
                    },
                    codeAutoRetrievalTimeout: (verificationId) {
                      print('time out maroof');
                    },
                  );