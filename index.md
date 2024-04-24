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
![image](https://github.com/XiaoFengLin123/cse15l-lab-report2/assets/146484956/4af51412-d66a-4df2-90c7-c41d0420b946)

Which methods in your code are called?

My code uses the method `public String handleRequest(URI url)` within the Handler class. It is responsible for handling URLs and checking the path for queries. I use the `split` function and `getQuery()`function from the `URI` library to separate users and their corresponding messages. Any other paths will result will return `"404 Not Found!"`.  

What are the relevant arguments to those methods, and the values of any relevant fields of the class?

The `public String handleRequest(URI url)` method uses `URI url` as it's argument. It is responsible for handling URLs within the `URI` library. Within the same class, I also have a Type String Variable named `Chatlog` for concatenating and displaying the method's outputs. Chatlog is a field within the `Handler` class, used to concatenate all requests and update them every time someone tries to use the path `/add-message.s=<string>&user=<string>`.


How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

The values of the fields of this class change from this specific request. The original request was: `http://localhost:5678/add-message?s=Hello World!&user=xil245`. Upon this request, the `public String handleRequest(URI url)` method was called and concatenated the user's name followed by a semicolon with a space `": "` and the messages, followed by a newline character. All of this is assigned to the field `String Chatlog` which holds the String value `xil245: Hello World!`

**Image Two of using `/add-message`**
![image](https://github.com/XiaoFengLin123/cse15l-lab-report2/assets/146484956/b7648692-a7a0-45f4-b59f-c14b595cc117)


