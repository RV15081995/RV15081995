import java.util.OptionalInt;
import java.util.Scanner;
import java.util.Arrays;
import java.util.Collections;

class Stockers{
    public static void main(String args[]){
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Enter the no. of companies: ");
        int n_companies= sc.nextInt();

        float[] st_prices=new float[n_companies];
        boolean[] st_price_rise=new boolean[n_companies];
        for(int i=1; i<=n_companies; i++){
            System.out.print("Enter current Stock Price for Company "+ i +": ");
            st_prices[i-1]=sc.nextFloat();
            System.out.println("Whether company's stock price rose today compare to yesterday?: ");
            st_price_rise[i-1]=sc.nextBoolean();
        }

        while(true){
            System.out.println();
            System.out.println("-----------------------------------------------");
            System.out.println("1. Display the companies stock prices in ascending order.");
            System.out.println("2. Display the companies stock prices in descending order.");
            System.out.println("3. Display the total no. of companies for which stock prices rose today.");
            System.out.println("4. Display the total no. of companies for which stock prices declined today.");
            System.out.println("5. Search a specific stock price.");
            System.out.println("6. Exit.");
            System.out.print("Your Choice: ");
            int option=sc.nextInt();
            switch(option){
                case 1:
                    Arrays.sort(st_prices);
                    System.out.println("Stock Prices in ascending order are: "+ Arrays.toString(st_prices));
                    break;
                case 2:
                    Arrays.sort(st_prices);
                    System.out.println("Stock Prices in descending order are: ");
                    for(int x=n_companies-1; x>=0; x--){
                        System.out.print(st_prices[x] + " ");
                    }
                    break;
                case 3:
                    int rose_count=0;
                    for(int j=0; j<n_companies; j++){
                        if(st_price_rise[j]==true){
                            rose_count++;
                        }
                    }
                    System.out.println("Total no. of companies whose stock price rose today: "+ rose_count);
                    break;
                case 4:
                    int dec_count=0;
                    for(int j=0; j<n_companies; j++){
                        if(st_price_rise[j]==false){
                            dec_count++;
                        }
                    }
                    System.out.println("Total no. of companies whose stock price decline today: "+ dec_count);
                    break;
                case 5:
                    System.out.print("Enter the key value: ");
                    float st_value=sc.nextFloat();
                    int flag=0;
                    for(int k=0; k<n_companies; k++){
                        if(st_prices[k]==st_value){
                            flag=1;
                            break;
                        }  
                    }
                    if(flag==1){
                        System.out.println("Stock of value "+ st_value+" is present");
                    }else{
                        System.out.println("Stock of value "+ st_value+" is not present");
                    }
                    break;
                case 6:
                    System.exit(0);
            }
        }
        

    }
}