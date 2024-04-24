**Lab Report 2**

**Part 1** 

```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    String Chatlog = "";
    public String handleRequest(URI url) {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("&");
                if (parameters[0].substring(0,2).equals("s=") && parameters[1].substring(0,5).equals("user=")) {
                    String Message = parameters[0].substring(2);
                    String User = parameters[1].substring(5);
                    Chatlog += User + ": " + Message + "\n";
                    return Chatlog;
                }
            }
            return "404 Not Found!";
        }
    }

class ChatServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}

```
**Image One of using `/add-message`** 
![image](https://github.com/XiaoFengLin123/cse15l-lab-report2/assets/146484956/93ea347c-b8b7-412f-8898-7c072846340f)

Which methods in your code are called?

My code uses the method `public String handleRequest(URI url)` within the Handler class. It is responsible for handling URLs and checking the path for queries. I use the `split` function and `getQuery()`function from the `URI` library to separate users and their corresponding messages. Any other paths will result will return `"404 Not Found!"`.  

What are the relevant arguments to those methods, and the values of any relevant fields of the class?

The `public String handleRequest(URI url)` method uses `URI url` as it's argument. It is responsible for handling URLs within the `URI` library. Within the same class, I also have a Type String Variable named `Chatlog` for concatenating and displaying the method's outputs. Chatlog is a field within the `Handler` class, used to concatenate all requests and update them every time someone tries to use the path `/add-message.s=<string>&user=<string>`.


How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

The values of the fields of this class change from this specific request. The original request was: `http://localhost:5678/add-message?s=Hello World!&user=xil245`. Upon this request, the `public String handleRequest(URI url)` method was called and concatenated the user's name followed by a semicolon with a space `": "` and the messages, followed by a newline character. All of this is assigned to the field `String Chatlog` which holds the String value `xil245: Hello World!`

**Image Two of using `/add-message`**
![image](https://github.com/XiaoFengLin123/cse15l-lab-report2/assets/146484956/266cfd4a-c4c9-493c-b2d4-099aa87cb6a7)
![image](https://github.com/XiaoFengLin123/cse15l-lab-report2/assets/146484956/c84530f6-0476-4eb4-8f0c-27386b2e4fe7)




Which methods in your code are called?
The `/add-message` uses the same method, `public String handleRequest(URI URL)`, within the Handler class. The resulting figure is concatenated to `Chatlog`, which stores all of the messages and pathways of the type `/add-message.s=<string>&user=<string>`.

What are the relevant arguments to those methods, and the values of any relevant fields of the class?
The `public String handleRequest(URI url)` method uses `URI url` as it's argument. It is responsible for handling URLs within the `URI` library. Within the same class, I also have a Type String Variable named `Chatlog` for concatenating and displaying the method's outputs. Chatlog is a field within the `Handler` class, used to concatenate all requests and update them whenever someone tries to use the path `/add-message.s=<string>&user=<string>`.The string followed by `"s="` takes in the username Jake From Statefarm, followed by a semicolon with a space `": "`, and the messages are followed by a newline character Resulting in `Jake From StateFarm: Hi my name is Jake`. 

How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.
Following this specific request, we concatenate `Jake From StateFarm: Hi, my name is Jake` to `Chatlog`, which results in a display of the previous commands and changes on top of the new commands. If I were to apply the same commands, it would continue to add the same message, thus increasing the `Chatlog`, and I would be able to see the changes live on my local computer.  

**Part 2**

On the command line of your computer, run ls with the absolute path to the private key for your SSH key for logging into ieng6.
![image](https://github.com/XiaoFengLin123/cse15l-lab-report2/assets/146484956/ddc24d7a-c7f7-4680-83b9-a905251bf67a)

On the command line of the ieng6 machine, run ls with the absolute path to the public key for your SSH key for logging into ieng6 (this is the one you copied to your account on ieng6 using ssh-copy-id, so it should be a path on ieng6's file system).
![image](https://github.com/XiaoFengLin123/cse15l-lab-report2/assets/146484956/990d27c9-2bed-4865-8865-a9c043f7ec29)


A terminal interaction where you log into your ieng6 account without being asked for a password.
![image](https://github.com/XiaoFengLin123/cse15l-lab-report2/assets/146484956/8a7b2d5e-8efa-4aba-8e3f-fd7b7142cea3)

**Part 3** 

I learned about the importance of SSH keys and how they can be used to allow secure and passwordless logins to remote systems. I also learned about the SCP (Secure Copy Protocol) command, which allows me to transfer files securely between my local computer and a remote server. This is especially useful for moving my code to and from the ieng6 server, allowing me  to work locally and test my code in a remote environment. 

