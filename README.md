# interview


### Array questions: 
  Count the total number of distinct element:

```
public class practise {

     public static void main(String[] args) {

         int arr[] = {10,20,10,20,30,30,30,50};
         distinctElement(arr);
     }

    private static void distinctElement(int[] arr) {
         int distinct=0;

         boolean isDis = true;

         for(int i=0;i<arr.length;i++){

            for(int j=i-1;j>=0;j--){
                if(arr[i]==arr[j]){
                    isDis = false;
                    break;
                }

            }
             if(isDis){
                 distinct++;
             }
             isDis = true;
        }
        System.out.println(distinct);
     }
```

### check if array is sorted:
```
public static void sortedArray(int arr[]){
         boolean isSort = true;
         //to check sorted array
        for(int i=0;i<arr.length-1;i++){
            if((arr[i+1]<arr[i]))
                isSort = false;
        }
        System.out.println(isSort?"is sorted":"not sorted");
    }
```

### Jagged array where row is static but column is variable:
```
public static void main(String[] args) {
         int m=3;
         int arr[][] = new int[3][];
         for(int i=0;i<arr.length;i++){
             arr[i] = new int[i+1];
             for(int j=0;j<arr[i].length;j++){
                 arr[i][j] = i;
                 System.out.print(arr[i][j]+"");
             }
             System.out.println();
         }
```
### String and immutability:

We can create string in three different ways :<br>
1) String class : String a1 / String name = new String("rabin"); This is immutable+ thread safe
2) StringBuffer : This is used for mutability and only when you need thread safety. StringBuffer s = new StringBuffer("rabin");
3) StringBuilder : This is also mutable but not thread safe. StringBuilder s = new StringBuilder("rain");

#### String pool constant:
```
String s1 = "rabin";
String s2 ="rabin";
if(s1==s2){
  sout("equal")
}else{
sout("not equal");
}
```
Here the output will be yes because although two strings are class and refrences are compare, when we compare two string literals then at that time a string pool constant is created and both of these variable s1 and s2 will refer same value.

<br>

but if we create using 
String s3 = new String("rabin");<br>
Then compairing this with s1 and s2 will give not equal

### Different String function:
1) "rabin".length();
2) "rabin".charAt(3);
3) "rabin".substring(2,4); => here 2 is b and last value will be not included. i.e i
4) contains() => return true or false
5) equals() => check whether two string are equal or not
6) compareTo() => return 0 if same if alphabetically greater then returns positive value otherwise negative value
7) indexOf() => s1.indexOf(s2,1) if s2 is contain in s1 then return the first value of contain string. here second parameter is to order function to start searching from that index.

   #### String builder function:
```
   StringBuilder s = new StringBuilder("rabin");
   s.reverse();
   s.append("paant");
   s.setCharAt(0,s);
   s.deleteCharAt(0);
   s.insert(1,rabaabba);
```
### Pattern Search problem in String:
```
String txt = "abcd bqcda";
         String pat = "cd";
         patSearch(txt,pat);

static void patSearch(String txt, String pat){
         int pos = txt.indexOf(pat);
         while(pos>=0){
             System.out.println(pos + " ");
             pos = txt.indexOf(pat,pos+1);
         }
     }
```
### taking out digits after decimal point:
```
public static void main(String[] args) {
         String s1 = "12.5318";
         String s2 = "19.385";

         patterSolve(s1,s2);
     }
     static void patterSolve(String s1, String s2){
         int point_pos = s1.indexOf(".");
         System.out.println(s1.substring(point_pos+1));
     }
```
### Reverse the String:
```
public static void main(String[] args) {
        String name = "geeks";

        reverseString(name);
    }
    static void reverseString(String name){

        String newStr = "";

        int point = name.length()-1;
        System.out.println("point"+point);
        while(point>=0){
            newStr = newStr + name.charAt(point);
            point--;
        }
        System.out.println(newStr);
    }
```
With the use of an array: 
```
static void reverse(String name){
        int i = name.length()-1;
        String str="";

        while(i>=0){
            str = str + name.charAt(i);
            i--;
        }
        if(str == name)
            System.out.println("palindrome");
        else
            System.out.println("not palindrome");
    }
```
### Decimal To Binary
```
public void binary(int dec_number){
        int i =0;
        String res = "";
        while(dec_number>0){
            int r = dec_number % 2;
            res = r + res;
            dec_number = dec_number/2;
        }
        System.out.println(res);

    }
```

### Basic concept of Wrapper Classes:
we have primitive type in Java like int, float,char etc in similar way we have wrapper classes of these like Integer, Character.<br>
why we need these? beacuse when we're working in OOPS then we can't make use of the primitive type and we need these <br> 
when we have the arraylist then at that time also we need to make use of these Wrapper classes

### Autoboxing and Unboxing:
```
int x = 10;
Integer y = x;  //autoboxing
int z = y    // unboxing
```

The concept of changing the primitive to wrapper is the autoBoxing <br>
The concept of changing the wrapper to primitve is the unBoxing <br>

### Merge String Alternately:
Input: word1 = "abc", word2 = "pqr" <br>
Output: "apbqcr" <br>
Explanation: The merged string will be merged as so: <br>
word1:  a   b   c <br>
word2:    p   q   r <br>
merged: a p b q c r <br>
Example 2: <br>

Input: word1 = "ab", word2 = "pqrs" <br>
Output: "apbqrs" <br>
Explanation: Notice that as word2 is longer, "rs" is appended to the end. <br>
word1:  a   b  <br>
word2:    p   q   r   s <br>
merged: a p b q   r   s <br>

```
public String mergeAlternately(String word1, String word2) {
       int i=0;
       int j=0;
        boolean flag = true;

        StringBuilder str = new StringBuilder();
       while(i<word1.length() && j<word2.length()){
           if(flag){
               str.append(word1.charAt(i));
               i++;
           }else{
               str.append(word2.charAt(j));
               j++;
           }
           flag = !flag;
       } 

       while(i<word1.length()){
           str.append(word1.charAt(i));
           i++;
       }
       while(j<word2.length()){
           str.append(word2.charAt(j));
           j++;
       }
       return str.toString();
    }
}
```
