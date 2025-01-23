# Stone-Paper-and-Scissor-
import java.util.Scanner;
import java.util.Random;

public class StonePaperScissor {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int rounds = 5; // Number of rounds
        int userWins = 0, computerWins = 0, ties = 0;

        System.out.println("Welcome to Stone-Paper-Scissors!");
        System.out.println("You will play " + rounds + " rounds against the computer.");

        for (int i = 1; i <= rounds; i++) {
            System.out.println("\nRound " + i + ":");
            System.out.println("Enter your choice:");
            System.out.println("For Stone: 0");
            System.out.println("For Paper: 1");
            System.out.println("For Scissors: 2");


            // User input
            int userChoice = scanner.nextInt();

            // Validate user input
            if (userChoice < 0 || userChoice > 2) {
                System.out.println("Invalid choice! Please enter 0, 1, or 2.");
                i--; // Replay the current round
                continue;
            }

            // Computer's random choice
            int computerChoice = random.nextInt(3);

            // Display choices
            String[] choices = {"Stone", "Paper", "Scissors"};
            System.out.println("You chose: " + choices[userChoice]);
            System.out.println("Computer chose: " + choices[computerChoice]);

            // Determine the winner of the round
            if (userChoice == computerChoice) {
                System.out.println("It's a tie!");
                ties++;
            } else if ((userChoice == 0 && computerChoice == 2) ||
                       (userChoice == 1 && computerChoice == 0) ||
                       (userChoice == 2 && computerChoice == 1)) {
                System.out.println("You win this round!");
                userWins++;
            } else {
                System.out.println("Computer wins this round!");
                computerWins++;
            }
        }

        // Display final results
        System.out.println("\nGame Over! Final Results:");
        System.out.println("You won " + userWins + " round(s).");
        System.out.println("Computer won " + computerWins + " round(s).");
        System.out.println("Ties: " + ties);

        // Declare the overall winner
        if (userWins > computerWins) {
            System.out.println("Congratulations! You are the overall winner!");
        } else if (computerWins > userWins) {
            System.out.println("Computer is the overall winner! Better luck next time.");
        } else {
            System.out.println("It's an overall tie!");
        }

        scanner.close();
    }
}
