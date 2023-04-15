import java.util.Scanner;

public class Question1 {
    public static void main(String[] args) {


        //------------------------------------------------------------
//ask user for column and row size
        //------------------------------------------------------------

        Scanner input = new Scanner(System.in);

        System.out.println("create a 2D matrix");

        System.out.println("Rows : ");

        int rows = input.nextInt();

        System.out.println("Columns: ");

        int columns = input.nextInt();

        int matrix[][] = new int[rows][columns];

        int MatrixVal;

        //------------------------------------------------------------
        // letting user create array
        //------------------------------------------------------------


        System.out.println("Enter A value for the matrix: ");

        for (int row = 0; row < matrix.length; row++) {
            for (int column = 0; column < matrix[row].length; column++) {
                MatrixVal = input.nextInt();
                System.out.println("Enter A value for matrix: ");
                matrix[row][column] = MatrixVal;
            }
        }

        //------------------------------------------------------------
        // print out the matrix
        //------------------------------------------------------------


        for (int row = 0; row < matrix.length; row++) {

            for (int column = 0; column < matrix[row].length; column++) {

                System.out.print(matrix[row][column] + " ");

            }
            System.out.println();
        }

        // answer
        System.out.println("the existence of a pattern of 4 is " + isConsecutiveFour(matrix));

    }

    //------------------------------------------------------------
//check if theres a pattern
    //------------------------------------------------------------

    public static boolean isConsecutiveFour(int[][] values)
    {

        // check for pattern
        for (int row = 0; row < values.length; row++) {


            int checker=0; //see if theres a pattern


            int value1 = values[row][0];


            for (int column = 0; column < values[row].length; column++)
            {
                if(values[row][column]  ==value1 ) {
                    checker++;
                    if (checker == 4) {

                        return true;
                    }
                }
                else
                {
                    value1 = values[row][column];

                    checker= 1;
                }
            }

        }


        //------------------------------------------------------------
        // check for pattern vertically
        //------------------------------------------------------------

        for (int column = 0; column<values[0].length;column++)      // read through array vertically
        {
            int checkVert = 0;

            int ValueVert = values[0][column];

            for (int row = 0; row < values.length; row++)

            {

                if (values[row][column] == ValueVert)
                {
                    checkVert++;

                    if (checkVert == 4)
                        return  true;
                }
                else
                {
                    ValueVert = values[row][column];

                    checkVert = 1;

                }


            }


        }


        //------------------------------------------------------------
        //check on the top left of the matrix
        //------------------------------------------------------------

        for (int vari = 0; vari < values.length; vari++) {

            int yes = vari;

            int xvar = 0;

            int checktopleft = 0;

            int currentValuetopleft = values[yes][xvar];


            while (yes >= 0) {

                if (values[yes][xvar] == currentValuetopleft) {

                    checktopleft++;

                    if (checktopleft == 4)

                        return true;

                } else {

                    checktopleft = 1;

                    currentValuetopleft = values[yes][xvar];


                }

                xvar++;

                yes--;

            }
        }

        //------------------------------------------------------------
        // check on the bottom right of the matrix
        //------------------------------------------------------------

        for (int variab = 0; variab < values[0].length; variab++) {

            int yes = values.length - 1;

            int xvar = variab;

            int checkbottomright = 0;

            int currentValuebottomright = values[yes][xvar];


            while (xvar < values[0].length && yes >= 0) {

                if (values[yes][xvar] == currentValuebottomright) {

                    checkbottomright++;

                    if (checkbottomright == 4) return true;

                } else {

                    checkbottomright = 1;

                    currentValuebottomright = values[yes][xvar];
                }
                xvar++;
                yes--;
            }
        }

        //------------------------------------------------------------
        // check  for the pattern in the bottom left side going up left
        //------------------------------------------------------------

        for (int e= values[0].length - 1; e > 0; e--) {

            int xvalue2 = e;

            int yvalue2 = values.length - 1;

            int currentvlaueofmatrix = values[yvalue2][xvalue2];

            int consecutiveCount = 0;

            while (xvalue2 >= 0 && yvalue2 >= 0) {

                if (values[yvalue2][xvalue2] == currentvlaueofmatrix) {

                    consecutiveCount++;

                    if (consecutiveCount == 4) return true;

                } else {

                    consecutiveCount = 1;

                    currentvlaueofmatrix = values[yvalue2][xvalue2];
                }

                xvalue2--;

                yvalue2--;
            }

        }


        for (int row = 1 ; row < values.length; row++) {

            int xvalue3 = values[0].length - 1;

            int yvalue3 = row;

            int consecutive = 0;

            int currentvalue = values[yvalue3][xvalue3];

            while (yvalue3 >= 0) {

                if (values[yvalue3][xvalue3] == currentvalue) {

                    consecutive++;

                    if (consecutive == 4) return true;

                } else {

                    consecutive = 1;

                    currentvalue = values[yvalue3][xvalue3];
                }
                xvalue3--;

                yvalue3--;
            }

        }
        return  false;
    }



}
