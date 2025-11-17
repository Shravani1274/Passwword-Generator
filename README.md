import java.util.Random; import 
java.util.Scanner;  
public class PasswordGenerator {  
// Option 1: Use part of name + random characters     
public 
static String generateWithName(String name, int length) {  
String characters = "0123456789!@#$%^&*()";  
Random random = new Random();  
StringBuilder password = new StringBuilder();  
// Add first 3 letters of name  
password.append(name.substring(0, Math.min(3, name.length())));  
// Fill remaining length with random characters         
for (int i = password.length(); i < length; i++) {             
index 
= 
int 
random.nextInt(characters.length());             
password.append(characters.charAt(index));  
}  
return password.toString();  
}  
// Option 2: Completely random password     
public static String generateRandom(int length) {  
String characters =  
"ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789!@#$%^&*()";         
Random random = new Random();  
StringBuilder password = new StringBuilder();  
for (int i = 0; i < length; i++) {    
random.nextInt(characters.length());             
         int index = 
password.append(characters.charAt(index));  
}  
return password.toString();  
}  
// Option 3: Strong password with all character types     
public static String generateStrong(int length) {  
String upper = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
String lower = "abcdefghijklmnopqrstuvwxyz";  
String digits = "0123456789";  
String special = "!@#$%^&*()";  
String all = upper + lower + digits + special;  
Random random = new Random();  
StringBuilder password = new StringBuilder();  
// Ensure at least one of each type  
password.append(upper.charAt(random.nextInt(upper.length())));         
password.append(lower.charAt(random.nextInt(lower.length())));         
password.append(digits.charAt(random.nextInt(digits.length())));         
password.append(special.charAt(random.nextInt(special.length())));  
// Fill remaining length  
for (int i = password.length(); i < length; i++) {             
password.append(all.charAt(random.nextInt(all.length())));  
}  
return password.toString();  
}  
public static void main(String[] args) {  
Scanner sc = new Scanner(System.in);  
System.out.println("==================================");  
System.out.println("
        P
 ASSWORD GENERATOR        ");  
System.out.println("==================================\n");  
System.out.print("Enter your name: ");  
String name = sc.nextLine();  
System.out.print("Enter desired password length: ");         
int length = sc.nextInt();  
if (length < 4) {  
System.out.println("Password length should be at least 4.");  
} else {  
System.out.println("\nChoose an option for password generation:");  
System.out.println("1. Name + Random Characters");  
System.out.println("2. Completely Random Password");  
System.out.println("3. Strong Password (Uppercase, Lowercase, Numbers, Symbols)");  
System.out.print("Enter your choice (1/2/3): ");  
            int choice = sc.nextInt();  
  
            String password = "";  
  
            switch (choice) {  
                case 1:  
                    password = generateWithName(name, length);  
                    break;                 
case 2:  
                    password = generateRandom(length);  
                    break;                 
case 3:  
                    password = generateStrong(length);  
                    break;                 
default:  
                    System.out.println("Invalid choice!");  
                    return;  
            }  
  
            System.out.println("\nGenerated Password: " + password); 
             }  
  
        sc.close();  
    }  
} 
