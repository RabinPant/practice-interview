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
