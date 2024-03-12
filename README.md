#include<stdio.h>
#include<string.h>
#include<stdlib.h>
//List perfect number
int  Perfect(int a[],int N){
	int m = 0;
	for (int i = 0; i < N; i++){
		int count = 0;
		if (i != 0) {
			for ( int j = 1; j <= i / 2; j++)
				if ( i % j == 0 ) count = count + j;
			if ( count == i){
				a[m] = i;
				m = m + 1;	
			}
		}
	}
	return m;
}
//----------------------
//Check increasing of string
int Check(char s[]){
	for (int i=0; i<strlen(s)-1; i++)
		if (s[i] > s[i+1]) return 0;
	return 1;	
}
//----------------------
//Greatest Common Divisor
int UCLN(int s1, int s2){
    while ( s1 != s2 ){ 
       if (s1>s2)  s1 = s1 - s2;
       else s2 = s2 - s1;
    }
    return s1;
}
//----------------------
//Sum of odd integer
int Sum(int *a, int sizeA){
	int sum=0;
	for (int i=0; i<sizeA; i++)
		if(*(a+i) % 2 != 0 ) sum=sum+*(a+i);
	return sum;	
} 
//----------------------
// nhap
void Nhap (int *b, int sizeB){
	for (int i=0; i<sizeB; i++)
		scanf("%d", b+i);
}
//---------------------------
// Xuat
void Xuat(int *a, int sizeA){
	for (int i=0; i<sizeA; i++)
		printf("%d  ", *(a+i));
}
//-----------------------
int Menu(){
	int choose;
	printf("\n----------------Menu--------------\n");
	printf("1. Printf out list perfect number\n");
	printf("2. Check increasing of string\n");
	printf("3. Greatest Common Divisor\n");
	printf("4. Sum of odd integer\n");
	printf("------------------------------------\n");
	printf("Enter choose: ");
	scanf("%d",&choose);
	return choose;
}
int main(){
	int choose;
	int *a;
	char s[100];
	int s1,s2;
	int sizeB;
	int *b;
	do{
		choose = Menu(choose);
		
		switch(choose){

			case 1:{
				int N=500;
				a = (int*)malloc(100*sizeof(int));
				int sizeA = Perfect(a,N);
				a = (int*)realloc(a,sizeA);
				Xuat(a,sizeA);
				break;
			}
			case 2:{
				fflush(stdin);
				gets(s);
				if( Check(s) == 1 ) printf("incresing");
					else printf(" not increasing");
				break;
			}
			case 3:{
				scanf("%d%d",&s1,&s2);
				printf("%d", UCLN(s1,s2));
				break;
			}
			case 4:{
				scanf("%d", &sizeB);
				b = (int*)malloc(sizeB*sizeof(int));
				Nhap(b,sizeB);
				printf("%d",Sum(b,sizeB));
				break;
			}
			case 0:{
				printf("Press Enter to exit. Good Bye! :v");
				break;
			}
			default:
				printf("Enter choose again!");
				break;
		}
	} while( choose != 0 );
}
