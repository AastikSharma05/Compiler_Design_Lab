# Code Explanation

We are taking a global variable for the entire program.

```C
char pro[SIZE], alpha[SIZE], beta[SIZE];
    int nont_terminal,i,j, index=3;
    printf("Enter the Production as E->E|A: ");
    scanf("%s", pro);
    nont_terminal=pro[0];
``` 

Here, we are taking index = 3 the 3rd character of the production and non_terminal = pro[0] the first character of the production.

String  Indexing in Elimination of Left Recursion
String Indexing
if(nont_terminal==pro[index])
If the first character and the 3rd character of the string are the same then the production is left recursive. That’s what we are checking. Otherwise, it will print “Grammar is NOT LEFT RECURSIVE”.

If it is left recursive then it will do the following:

```C
for(i=++index,j=0;pro[i]!='|';i++,j++){
            alpha[j]=pro[i];
            //Checking if there is NO Vertical Bar (|)
            if(pro[i+1]==0){
                printf("This Grammar CAN'T BE REDUCED.\n");
                exit(0); //Exit the Program
            }
        }
        alpha[j]='\0'; //String Ending NULL Character
``` 

First, we have to take alpha. Alpha will be the collection of characters from the 4th character to the vertical bar (|).
If there is no vertical bar then it will print the error and exit the program.

And lastly, after the loop, we will add a null character to our alpha string. If we don’t give null characters at the end of String it will show garbage values. alpha[j]='\0' its means the last character of alpha or we can say it is storing a null character at the last position.

```C
if(pro[++i]!=0) //Checking if there is Character after Vertical Bar (|)
        {
            //Getting Beta
            for(j=i,i=0;pro[j]!='\0';i++,j++){
                beta[i]=pro[j];
            }
            beta[i]='\0'; //String Ending NULL character
            //Showing Output without LEFT RECURSION
            printf("\nGrammar Without Left Recursion: \n\n");
            printf(" %c->%s%c'\n", nont_terminal,beta,nont_terminal);
            printf(" %c'->%s%c'|#\n", nont_terminal,alpha,nont_terminal);
        }
        else
            printf("This Grammar CAN'T be REDUCED.\n");
    }
``` 
After getting the Alpha we need to get the beta. For getting beta, first, we need to verify if there is any character after the vertical bar(|). If there is no character after the vertical bar(|), it will show an error.

And if there is any character, it will store those characters in the beta string variable. After storing all the characters we need to put the end character and that’s it. 

After we get the beta, we just have to print those.
