# Code Explanation

```C
    char gram[20],part1[20],part2[20],modifiedGram[20],newGram[20],tempGram[20];
    int i,j=0,k=0,l=0,pos;
    printf("Enter Production : A->");
    gets(gram);
``` 
First, we are taking some variables for further use. You’ll get them along the way. Then we are simply taking the production.

```C
    for(i=0;gram[i]!='|';i++,j++)
        part1[j]=gram[i];
    part1[j]='\0';
    for(j=++i,i=0;gram[j]!='\0';j++,i++)
        part2[i]=gram[j];
    part2[i]='\0';
```
Here, we are separating the production and saving them in another variable. And adding null characters at the end of each string. If we don’t add a null character at the ending of the string it will carry some garbage value which will generate fault output.

```C
    for(i=0;i<strlen(part1)||i<strlen(part2);i++){
        if(part1[i]==part2[i]){
            modifiedGram[k]=part1[i];
            k++;
            pos=i+1;
        }
    }
```

Using for loop and if statement, we are taking the common prefix and storing them in modifiedGram variable. And we are also taking the latest position of common prefix and increment by one for the next character.

```C
    for(i=pos,j=0;part1[i]!='\0';i++,j++){
        newGram[j]=part1[i];
    }
    newGram[j++]='|';
    for(i=pos;part2[i]!='\0';i++,j++){
        newGram[j]=part2[i];
    }
    modifiedGram[k]='X';
    modifiedGram[++k]='\0';
    newGram[j]='\0';
    printf("\nGrammar Without Left Factoring : : \n");
    printf(" A->%s",modifiedGram);
    printf("\n X->%s\n",newGram);
}
```

The position we take, using that along with for loop, we are taking the rest of the production. 

And the rest of the things are quite simple.
