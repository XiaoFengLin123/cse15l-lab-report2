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

![image](https://github.com/XiaoFengLin123/cse15l-lab-report2/assets/146484956/666f8c3b-914f-4cef-8479-1acd9f66a760)

