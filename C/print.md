# printf() fprintf() perror()

printf() == fprintf(stdout, "***")

perror() == fprintf(stderr, "***")

## stdin stdout stderr

File *fp=fopen()，這個fp就是我們向系統申請的，相當於一通往檔案的通道。  
其實，stdin,stdout,stderr就是這個fp，不過他是隨著計算機系統的開啟預設開啟的，其中0就是stdin，表示輸入流，指從鍵盤輸入，1代表stdout，2代表stderr，1,2預設是顯示器。

# Example

    #include<stdio.h>     

    int main(){  

        printf("Stdout Helo World!!\n");  

        fprintf(stdout,"Stdout Hello World!!\n");  

        perror("Stderr Hello World!!\n");  

        fprintf(stderr,"Stderr Hello World!!\n");    

        return 0;  
    }

編譯過後,./test,螢幕上是四條輸出，如果./test > test.ext ,結果是螢幕上輸出兩條Stderr Hello World!!，Stdout Helo World!!在檔案test.txt中，基於上面說的很容易理解現在的結果，於是我們可以隨便處理我們想要的輸出，例如：

    ./test 1>testout.txt 2>testerr.txt，我們將stdout輸出到檔案testout.txt中,將stderr輸出到testerr.txt檔案中；

    ./test 1>testout.txt ,將stdout輸出到檔案testout.txt 中，stderr輸出到螢幕上；

    ./test 2>testerr.txt,將stderr輸出到檔案testerr.txt中，stdout輸出到螢幕上；

    ./test > test.txt 2>&1,這是將stdout和stderr重定向到同一檔案test.txt檔案中。

## Note

stderr，和stdout還有重要一點區別，stderr是沒有緩衝的，它立即輸出，而stdout預設是行緩衝，也就是它遇到‘\n’，才向外輸出內容，如果你想stdout也實時輸出內容，那就在輸出語句後加上fflush（stdout），這樣就能達到實時輸出的效果。