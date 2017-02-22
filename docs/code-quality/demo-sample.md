---
title: "デモのサンプル | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コード分析, サンプル"
  - "デモ サンプル [Visual Studio ALM]"
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# デモのサンプル
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

次の手順では、「[チュートリアル : C\/C\+\+ コード分析による障害の検出](../Topic/Walkthrough:%20Analyzing%20C-C++%20Code%20for%20Defects.md)」のサンプルを作成する方法について説明します。  この手順では次のものが作成されます。  
  
-   CppDemo という名前の [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ソリューション。  
  
-   CodeDefects という名前のスタティック ライブラリ プロジェクト。  
  
-   Annotations という名前のスタティック ライブラリ プロジェクト。  
  
 この手順では、スタティック ライブラリ用のヘッダー ファイルと .cpp ファイルのコードも提供されます。  
  
### CppDemo ソリューションと CodeDefects プロジェクトを作成する  
  
1.  **\[ファイル\]** メニューをクリックし、**\[新規作成\]** をポイントし、**\[新しいプロジェクト\]** をクリックします。  
  
2.  **\[プロジェクトの種類\]** ツリー リストで、Visual C\+\+ が VS の既定の言語ではない場合は、**\[他の言語\]** を展開します。  
  
3.  **\[Visual C\#\]** を展開し、**\[全般\]** をクリックします。  
  
4.  **\[テンプレート\]** で **\[空のプロジェクト\]** をクリックします。  
  
5.  **\[名前\]** ボックスに「**CodeDefects**」と入力します。  
  
6.  **\[ソリューションのディレクトリを作成\]** チェック ボックスをオンにします。  
  
7.  **\[ソリューション名\]** ボックスに「**CppDemo**」と入力します。  
  
### CodeDefects プロジェクトをスタティック ライブラリとして構成する  
  
1.  ソリューション エクスプローラーで **\[CodeDefects\]** を右クリックし、**\[プロパティ\]** をクリックします。  
  
2.  **\[構成プロパティ\]** を展開し、**\[全般\]** をクリックします。  
  
3.  **\[全般\]** の一覧で、**\[ターゲットの拡張子\]** の横の列のテキストを選択し、「**.lib**」と入力します。  
  
4.  **\[プロジェクトの既定値\]** で、**\[構成の種類\]** の横の列をクリックし、**\[スタティック ライブラリ \(.lib\)\]** をクリックします。  
  
### CodeDefects プロジェクトにヘッダー ファイルとソース ファイルを追加する  
  
1.  ソリューション エクスプローラーで **\[CodeDefects\]** を展開し、**\[ヘッダー ファイル\]** を右クリックして **\[追加\]** をクリックし、**\[新しい項目\]** をクリックします。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスの **\[コード\]** をクリックし、**\[ヘッダー ファイル\]** をクリックします。  
  
3.  **\[ファイル名\]** ボックスに「**Bug.cpp**」と入力し、**\[追加\]** をクリックします。  
  
4.  次のコードをコピーし、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] エディターで **Bug.cpp** ファイルに貼り付けます。  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5.  ソリューション エクスプローラーで **\[ソース ファイル\]** を右クリックし、**\[新規作成\]** をポイントして、**\[新しい項目\]** をクリックします。  
  
6.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[C\+\+ ファイル \(.cpp\)\]** をクリックします。  
  
7.  **\[ファイル名\]** ボックスに「**Bug.cpp**」と入力し、**\[追加\]** をクリックします。  
  
8.  次のコードをコピーし、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] エディターで Bug.h ファイルに貼り付けます。  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. **\[ファイル\]** メニューをクリックし、**\[すべてを保存\]** をクリックします。  
  
### Annotations プロジェクトを追加し、スタティック ライブラリとして構成する  
  
1.  ソリューション エクスプローラーで **\[CppDemo\]** をクリックし、**\[追加\]** をポイントして **\[新しいプロジェクト\]** をクリックします。  
  
2.  **\[新しいプロジェクトの追加\]** ダイアログ ボックスで Visual C\+\+ を展開し、**\[全般\]** をクリックして **\[空のプロジェクト\]** をクリックします。  
  
3.  **\[名前\]** ボックスに「**Annotations**」と入力し、**\[追加\]** をクリックします。  
  
4.  ソリューション エクスプローラーで **\[Annotations\]** を右クリックし、**\[プロパティ\]** をクリックします。  
  
5.  **\[構成プロパティ\]** を展開し、**\[全般\]** をクリックします。  
  
6.  **\[全般\]** の一覧で、**\[ターゲットの拡張子\]** の横の列のテキストを選択し、「**.lib**」と入力します。  
  
7.  **\[プロジェクトの既定値\]** で、**\[構成の種類\]** の横の列をクリックし、**\[スタティック ライブラリ \(.lib\)\]** をクリックします。  
  
### Annotations プロジェクトにヘッダー ファイルとソース ファイルを追加する  
  
1.  ソリューション エクスプローラーで **\[Annotations\]** を展開し、**\[ヘッダー ファイル\]** を右クリックして **\[追加\]** をクリックし、**\[新しい項目\]** をクリックします。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[ヘッダー ファイル \(.h\)\]** をクリックします。  
  
3.  **\[ファイル名\]** ボックスに「**annotations.h**」と入力し、**\[追加\]** をクリックします。  
  
4.  次のコードをコピーし、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] エディターで **\[annotations.h\]** ファイルに貼り付けます。  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  ソリューション エクスプローラーで **\[ソース ファイル\]** を右クリックし、**\[新規作成\]** をポイントして、**\[新しい項目\]** をクリックします。  
  
6.  **\[新しい項目の追加\]** ダイアログ ボックスの **\[コード\]** をクリックし、**\[C\+\+  ファイル \(.cpp\)\]** をクリックします。  
  
7.  **\[ファイル名\]** ボックスに「**annotations.cpp**」と入力し、**\[追加\]** をクリックします。  
  
8.  次のコードをコピーし、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] エディターで **\[annotations.cpp\]** ファイルに貼り付けます。  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. **\[ファイル\]** メニューをクリックし、**\[すべてを保存\]** をクリックします。