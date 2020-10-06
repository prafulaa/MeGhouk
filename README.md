import java.util.Scanner;
import java.util.Scanner;

public class VoteRecorder {

   private static String nameCandidatePresident1;
   private static String nameCandidatePresident2;
   private static String nameCandidateVicePresident1;
   private static String nameCandidateVicePresident2;

   private static int votesCandidatePresident1;
   private static int votesCandidatePresident2;
   private static int votesCandidateVicePresident1;
   private static int votesCandidateVicePresident2;

   int myVoteForPresident;
   int myVoteForVicePresident;

   public VoteRecorder() {

   }
   public static void setCandidatesPresident(String name1, String name2) {
       nameCandidatePresident1 = name1;
       nameCandidatePresident2 = name2;
   }

   public static void setCandidatesVicePresident(String name1, String name2) {
       nameCandidateVicePresident1 = name1;
       nameCandidateVicePresident2 = name2;
   }

   public static void resetVotes() {
       votesCandidatePresident1 = 0;
       votesCandidatePresident2 = 0;
       votesCandidateVicePresident1 = 0;
       votesCandidateVicePresident2 = 0;
   }


   public static String getCurrentVotePresident() {
       return  nameCandidatePresident1 + " has "
               + votesCandidatePresident1 + " votes;" 
               + nameCandidatePresident2 + " has " 
               + votesCandidatePresident2 + " votes;";
   }

   public static String getCurrentVoteVicePresident() {
       return  " " +nameCandidateVicePresident1 + " has "
               + votesCandidateVicePresident1 + " votes;" 
               + nameCandidateVicePresident2 + " has " 
               + votesCandidateVicePresident2 + " votes;";
   }


   public void getConfirmVotes() {
       Scanner scanner = new Scanner(System.in);
       getVotes();
       if (confirmVotes() == true) {
           System.out.println("Type yes if you are happy with your vote");
           String i = scanner.next();
           if (i.equalsIgnoreCase("Yes")) {
               getConfirmVotes();
           }
       } else {
           getConfirmVotes();
       }

   }


   private void getVotes() {
       myVoteForPresident = getAVote(nameCandidatePresident1,
               nameCandidatePresident2);
       myVoteForVicePresident = getAVote(nameCandidateVicePresident1,
               nameCandidateVicePresident2);

   }


   private boolean confirmVotes() {
       Scanner scanner = new Scanner(System.in);
       if (myVoteForPresident == 0)
           System.out.println("Your vote for president is no one");
       if (myVoteForPresident == 1)
           System.out.println("Your vote for president is " + nameCandidatePresident1);
       if (myVoteForPresident == 2)
           System.out.println("Your vote for president is " + nameCandidatePresident2);
       if (myVoteForVicePresident == 0)
           System.out.println("Your vote for vice president is no one");
       else if (myVoteForVicePresident == 1)
           System.out.println("Your vote for vice president is " + nameCandidateVicePresident1);
       else if (myVoteForVicePresident == 2)
           System.out.println("Your vote for vice president is " + nameCandidateVicePresident2);

       
  
}

   private int getAVote(String name1, String name2) {
       Scanner scanner = new Scanner(System.in);
       System.out.println("Please choose a candidate:");
       System.out.println("      0 - No one");
       System.out.println("      1 - "+ name1);
       System.out.println("      2 - " + name2);
       int choice = scanner.nextInt();
       return choice;
   }

   private void recordVotes() {
       if (myVoteForPresident == 1)
           votesCandidatePresident1++;
       else
           votesCandidatePresident1 = votesCandidatePresident1;
       if (myVoteForPresident == 2)
           votesCandidatePresident2++;
       else
           votesCandidatePresident2 = votesCandidatePresident2;
       if (myVoteForVicePresident == 1)
           votesCandidateVicePresident1++;
       else
           votesCandidateVicePresident1 = votesCandidateVicePresident1;
       if (myVoteForVicePresident == 2)
           votesCandidateVicePresident2++;
       else
           votesCandidateVicePresident2 = votesCandidateVicePresident2;

}



class VoteRecorderDemo {

   public static void main(String[] args) {

       Scanner scanner = new Scanner(System.in);
       String nore;
       
       VoteRecorder voteRecorder = new VoteRecorder();
       voteRecorder.setCandidatesPresident("Annie", "Bob");
       voteRecorder.setCandidatesVicePresident("John", "Susan");
       voteRecorder.getConfirmVotes();
     

       System.out .println("Type yes if there is another voter");
       nore = scanner.next();
       if (nore.equalsIgnoreCase("Yes")) {
           voteRecorder.resetVotes();
       }
       
       System.out.println(voteRecorder.getCurrentVotePresident());
       System.out.println(voteRecorder.getCurrentVoteVicePresident());
       
    }
   }
}
