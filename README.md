# language-evaluation
A language proficiency evaluation system for University admission
import java.util.Scanner;

public class Language_evaluation {

	public static void main(String[] args) {

		int option; //option chosen by user, 1 or 2, integer
		double listening, speaking, reading, writing, overall, difference, integer_part; // use "double" to store variables regarding scores
		Scanner keyboard = new Scanner(System.in);
		
		System.out.println("-------****-------****-------****-------****-----****-----");
		System.out.println("      Welcome to XXX Language Proficiency Evaluator!");
		System.out.println("                based on IELTS exam");
		System.out.println("-------****-------****-------****-------****-----****-----");

		System.out.println("\nHere are the available options:");
		System.out.println("      1 – Language Proficiency Requirements for the Applicant");
		System.out.println("      2 – Evaluation of your language proficiency\n");

		System.out.print("Please enter the digit corresponding to your case: ");
		
		option=keyboard.nextInt(); //capture user input for option
		
		if (option==1)
		{
		
			System.out.println("\n- The overall score of IELTS exam of applicants needs to be equal or above 6.5 and the scores for writing and reading skills should not be below 6.0. If your overall score is 6, and your reading and writing scores are at least 6, you will be eligible for conditional admission. So you need to take an English course in the first semester. Otherwise you have to retake the IELTS exam.");
			System.out.println("Thanks for choosing XXX.");
		}
		
		if (option==2)
		{
		
			System.out.print("\nPlease enter your listening score: ");
			listening=keyboard.nextDouble();

			
			System.out.print("\nPlease enter your speaking score: ");
			speaking=keyboard.nextDouble();

			
			System.out.print("\nPlease enter your reading score: ");
			reading=keyboard.nextDouble();

			
			System.out.print("\nPlease enter your writing score: ");
			writing=keyboard.nextDouble();

			
			overall=(listening+speaking+reading+writing)/4; //calculate overall score before rounding
			difference = overall%1; //capture the part that's less than 1 of overall score, the part after "."
			integer_part=overall-difference; //capture the other part of the overall score, the integer part
			
			//the following "if" does the rounding work for overall score
			if (difference>=0&&difference <0.25)
				overall=integer_part;
  		        else if (difference>=0.25&&difference<0.75)
				overall=integer_part+0.5;
			else if (difference>=0.75&&difference<1)
				overall=integer_part+1;
							
			System.out.println("\n      Your overall score is: "+overall);
			System.out.println("      Your reading score is: "+reading);
			System.out.println("      Your writing score is: "+writing+"\n");

			
			//this "if" decides whether the IELTS score meets the admission requirement
			if (overall>=6.5&&reading>=6&&writing>=6)
				System.out.println("      Congratulations: You are eligible for Admission.");
			else if (overall>=6.5&&(reading<6||writing<6))
				System.out.println("You are eligible for Conditional Admission.");
			else if (overall==6&&(reading>=6&&writing>=6))
				System.out.println("You are eligible for Conditional Admission.");
			else if (overall==6&&(reading<6||writing<6))
				System.out.println("Sorry, you have to retake the exam.");
			else if (overall<6)
				System.out.println("Sorry, you have to retake the exam.");
			
			keyboard.close();
				
		}
				
	}

}
