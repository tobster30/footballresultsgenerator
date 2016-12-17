import java.io.File;
import java.util.Scanner;

public class FRG {
	
	public static void main (String[] args) { 
		
		// Variables to count each loop
		int lc = 0;
		int invalidlc = 0;
		int tm = 0;
		
		// Variable to call user input
		String Result;
		
		// Variable used to make program recognise where to split the Result string
		String Deliminator = ":";
		
		// Arrays to store user entered data
	
		String[] home_team = new String[100];
   		String[] away_team = new String[100];
   		int[] home_score = new int[100];
   		int[] away_score = new int[100];
   		
   		String[] ud = new String[4];
   		
   		// Variable to add up the integers in home_score and away_score
   		int htotal = 0;   		
   		int atotal = 0;
   		
   		// Variables for picking out the largest home and away score
   		int hmax = home_score[3];  		
   		int amax = away_score[4];   		
   		
   		// Scanner for user input
   		Scanner userinput = new Scanner (System.in);
   		
   		// User instructions
   		System.out.println("Please enter your football results");
	   	System.out.println("Do it in this format: Team 1:Team 2:Team 1 Score:Team 2 Score");
	   	System.out.println("To stop entering football results type stop");
	   	System.out.println("To see input statistics type Totals"); 		
	   	
   		// Loop to repeat the data input 100 times and count how many times it has done it
   		for (lc = 0; lc <= 100 ; lc++)	{
   		
	   		// User enters data here
	   		
	   		System.out.println("Input Results: ");
	   		Result = userinput.next();
	   		
	   		Result = Result.replace(" : ", ":");
	   		
	   		// If user enters stop the loop ends
	   		if (Result.equals("stop")){
	   			break;
	   		}
	   		
	   		// if user enters Totals the following statistics are shown and returns back to user input
	   		else if (Result.equals("Totals")){
	   			System.out.println("Total number of matches played: " + tm );
	   			System.out.println("Total home scores of all matches: " + htotal );
	   			System.out.println("Total away scores of all matches: " + atotal );
	   			System.out.println("Highest home score: " + hmax );
	   			System.out.println("Highest away score: " + amax );
	   			System.out.println("Total number of invalid entries: " + invalidlc );
	   			continue;
	   		}
	   		
	   		
	   		try {
	   		// String split into 4 different variables
	   		ud = Result.split(Deliminator);
			
	   		// String is split into 4 seperate variables and stored in array
	   		home_team [lc] = ud[0];
			away_team [lc] = ud[1];
			home_score [lc] = Integer.parseInt(ud[2]);
			away_score [lc] = Integer.parseInt(ud[3]);
			tm++;
			
			
			// loops used for finding the total sum for home and away scores
				for (int i = 0 ;i<home_score.length; i++){
					htotal += home_score[i];
				}
					
				for (int x = 0 ;x<away_score.length; x++){
					atotal += away_score[x];
				}
				
				
				
			// loops used for finding the highest score in each team	
				for (int y = 0; y < home_score.length; y++ ) {
	   				if (home_score[y] > hmax) {
	   					hmax = home_score[y];
	   				}
	   			}
				
				for (int e = 0; e < home_score.length; e++ ) {
	   				if (away_score[e] > amax) {
	   					amax = away_score[e];
	   				}
	   			}
	   		}
	   		
	   		// if either error occurs it automatically goes back to the start of the loop and counts it
	   		
	   		catch(java.lang.NumberFormatException e){
	   			System.out.println("Invalid entry, please try again");
	   			invalidlc++;
	   		}
	   		
	   		catch(java.lang.ArrayIndexOutOfBoundsException e){
	   			System.out.println("Invalid entry, please try again");
	   			invalidlc++;
	   		}
   		}
   		
   		// For loop to print out all of the scores user has entered
   		for (; lc > 0; lc--)
   		{
   			System.out.println(home_team[lc-1] + " [" + home_score[lc-1] + "]" + " | " + away_team[lc-1] + " [" + away_score[lc-1] + "] ");
   		}
	}
}
