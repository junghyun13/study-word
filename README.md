# study-word
# Enter a letter consisting of uppercase and lowercase letters, and the lowercase and uppercase letters are considered as the same letter and the most frequent letter is printed. 알파벳 대소문자로 이루어진 문자를 입력해서 소문자와 대문자는 같은 문자로 생각하고 가장 많이 나온 문자를 출력한다.(다만, 가장 많이 사용된 알파벳이 여러개일 경우는 ?를 출력해라!)
# c program
#include <stdio.h>
#include <string.h>
int main(void){
	char x[100001];
	int y[26]={0,};
	scanf("%s",x);
	char *p=x; //포인터를 이용해보자! 
	int *q=y;
	int i,max=0,num=0,n=0;
	for(i=0;i<strlen(x);i++){ //대소문자 구분 X않고 a,A를 A로 저장  
		if(p[i]>=97){
			p[i]=p[i]-32;
		}
		q[p[i]-65]++;
	}
	max=y[0];
	for(i=1;i<26;i++){
		if(q[i]>max){
			max=q[i];
			num=i;
		}
	}
	for(i=0;i<26;i++){
		if(max==q[i]){   
			n++;
		}
	}
	if(n>1) //n이 1보다 크다는 것은 yaYA에서 Y랑 A가 2번으로 둘다 많이 나와서 비교X  
	  printf("?");
	else
	  printf("%c",num+65); //0번째부터가 A니까 num+65 
    return 0;
}
#input-->Zza
#result-->Z
