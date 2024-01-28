# Lab Report 2
This lab report is about servers and SSH keys.
## Part 1 - ChatServer

### Code
```java
import java.io.IOException;
import java.net.URI;
import java.util.Arrays;

class Handler1 implements URLHandler {
    String savedText = "Message Board:\n";

    public String handleRequest(URI url) {
        if(url.getPath().equals("/")){
            return savedText;
        }
        else if(url.getPath().equals("/add-message")){
            String query = url.getQuery();
            if(query.startsWith("s=")){
                String[] remain = query.split("[=&]");
                if(remain.length != 4) {
                    System.out.println(Arrays.toString(remain));
                    return "404 Not Found!";
                }
                String message = remain[1];
                if(remain[2].equals("user")){
                    String user = remain[3];
                    savedText += String.format("%s: %s\n", user, message);
                    return savedText;
                }
                else {
                    return "Cannot find \"user\".";
                }
            }
            return "404 Not Found!";
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

        Server.start(port, new Handler1());
    }
}
```

### Screenshot 1
### Screenshot 2

## Part 2 - SSH

## Part 3 - Something I Learned
