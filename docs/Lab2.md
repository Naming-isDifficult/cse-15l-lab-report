# Week 2 Lab Report

## **Part 1**
### Code for my <font face='Courier New'>StringServer</font>
```
import java.io.IOException;
import java.net.URI;

public class StringServer{
    
	private static boolean test = false;
	
    /**
     * Inner class for URI handler
     */
    static class Handler implements URLHandler{

        StringBuilder strToDisplay;

        public Handler(){
            strToDisplay = new StringBuilder();
        }

        public String handleRequest(URI url){
            String path = url.getPath();

            if(path.indexOf("add-message")==1){
                //should be an add command
                String strToBeAdded = url.getQuery();

                if(strToBeAdded.startsWith("s=")){
                    strToDisplay.append(strToBeAdded.substring(2));
                    strToDisplay.append("\n");
                    return strToDisplay.toString();
                }
            }
            return "404 Not Found";  
        }
    }

    public static void main(String... args) throws IOException{
    	
    	int port = -1;
    	
    	if(test) {
    		port = 4000;
    	}
    	else {
	        if(args.length == 0){
	            System.out.println("Missing port number!"+
                                   "Try any number between 1024 to 49151");
	            return;
	        }
	        
	        port = Integer.parseInt(args[0]);
    	}

        Server.start(port, new Handler());
    }
}
```
### **Screenshot 1**
![image](../Lab2/Screenshot1.png)

### **Screenshot 2**
![image](../Lab2/Screenshot2.png)

