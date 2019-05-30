# Compiler Project 2
20141440 Seungwon Lee 

## Main Idea of Your Solution
First, I added types in lex file and storing its value to yylval.type which is character type.
I defined symbol table by 2-dimension array, which contains the pair of ID and TYPE.
When array is declared, it stores its length size information in length array and next, it calls insert(..) function for storing its ID and TYPE information in symbol table. Finally, it calls computed_length(..) which computes the multiplication of length size and size of type.
Later, using lookup(..) and lookup_length functions, it could finds its own information such as type, size and computed_size.

## Code Description
```c
void insert(char *id, char type){
   symbol[flag][0] = *id;
   symbol[flag][1] = type;
   flag++;
 }
 int lookup(char *id){
   char type;
   int i;
   for(i=0; i<flag+1; i++){
     if( symbol[i][0] == *id )
         type = symbol[i][1];
   }

   switch(type){
     case 'i':   // int
       return 4;
     case 'f':   // float
       return 4;
     case 'c':   // char
       return 1;
     case 'd':   // double
       return 8;
     default:
       return -1;
       break;
   }
 }
 int lookup_length(char *id){
   int i;
   for(i=0; i<flag; i++){
     if( symbol[i][0] == *id ){
       //printf("for debugging\n");
       return computed[i][++length_flag];
     }
   }
   return -1;
 }

 void compute_length(int length[][20], int length_size){
   int i; int result=1;
   computed[flag][0] = flag;
   for(i=length_size+1; i>0; i--){
     result = result*length[flag][length_size--];
     computed[flag][i] = result;
   }
 }
```

## Detailed Algorithm
When insert function is called, it stored two information according to parameters; ID and it's type.
when computed_length function is called, it computes the actual size of defined array and stores the result in computed[][] array. For example, int a[10][20]; will give computed[ID][0]==80 and computed[ID][1]==4.
When lookup function is called, it starts to search same ID in symbol table array. If it finds same ID, it checks the type of it, and return integer value according to the type.i
When lookup_length function is called, it helps to find computed[][] array according to caller's ID, and returns the specific computed size which caller wants at that time.

## anything else...
My code uses one more unnecessary registr allocation compared to given optimized output, but it works correctly.
