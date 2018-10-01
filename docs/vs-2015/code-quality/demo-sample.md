---
title: サンプルのデモ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 23
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8aca1c819ee413f1bcc2fe81c90233256a12317a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533865"
---
# <a name="demo-sample"></a>デモのサンプル
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[デモ サンプル](https://docs.microsoft.com/visualstudio/code-quality/demo-sample)します。  
  
この次の手順のサンプルを作成する方法を示して[チュートリアル: C/C++ コード障害の検出に分析](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md)します。 プロシージャを作成します。  
  
-   A [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] CppDemo という名前のソリューションです。  
  
-   スタティック ライブラリ プロジェクトでは、CodeDefects という名前です。  
  
-   スタティック ライブラリ プロジェクトの注釈の名前。  
  
 手順では、静的ライブラリのヘッダーおよび .cpp ファイルのコードも提供します。  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>CppDemo ソリューションと CodeDefects プロジェクトを作成します。  
  
1.  をクリックして、**ファイル**メニューで、**新規**、 をクリックし、**新しいプロジェクト**。  
  
2.  **プロジェクトの種類**リストをツリーで、Visual C は、VS で、既定の言語ではない場合は展開**他の言語**します。  
  
3.  展開**Visual C**、 をクリックし、**全般**します。  
  
4.  **テンプレート**、 をクリックして**空のプロジェクト**します。  
  
5.  **名前**テキスト ボックスに「 **CodeDefects**します。  
  
6.  選択、**ソリューションのディレクトリを作成**チェック ボックスをオンします。  
  
7.  **ソリューション名**テキスト ボックスに「 **CppDemo**します。  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>スタティック ライブラリとして CodeDefects プロジェクトを構成します。  
  
1.  ソリューション エクスプ ローラーで右クリックして**CodeDefects**し**プロパティ**します。  
  
2.  展開**構成プロパティ** をクリックし、**全般**します。  
  
3.  **全般**一覧で、列の横にテキストを選択**Target Extension**、し、入力 **.lib**します。  
  
4.  **プロジェクトの既定値**、横に列をクリックして**構成の種類**、 をクリックし、**スタティック ライブラリ (.lib)** します。  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>ヘッダーとソース ファイルを CodeDefects プロジェクトに追加します。  
  
1.  ソリューション エクスプ ローラーで、 **[CodeDefects**、右クリック**ヘッダー ファイル**、] をクリックして**追加**、順にクリックします**新しい項目の**します。  
  
2.  **新しい項目の追加**ダイアログ ボックスで、をクリックして**コード**、 をクリックし、**ヘッダー ファイル (.h)**。  
  
3.  **名前**ボックスに「 **Bug.cpp**  をクリックし、**追加**します。  
  
4.  次のコードをコピーして貼り付けます、 **Bug.cpp**ファイル、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]エディター。  
  
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
  
5.  ソリューション エクスプ ローラーで右クリック**ソース ファイル**、 をポイント**新規**、 をクリックし、**新しい項目の**。  
  
6.  **新しい項目の追加**ダイアログ ボックスで、をクリックして**C++ ファイル (.cpp)**  
  
7.  **名前**ボックスに「 **Bug.cpp**  をクリックし、**追加**します。  
  
8.  次のコードをコピーしてで Bug.h ファイルに貼り付け、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]エディター。  
  
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
  
9. をクリックして、**ファイル** メニューをクリック**すべて保存**します。  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>注釈のプロジェクトを追加し、スタティック ライブラリとして設定  
  
1.  ソリューション エクスプ ローラーで次のようにクリックします。 **CppDemo**、 をポイント**追加**、 をクリックし、**新しいプロジェクト**します。  
  
2.  **新しいプロジェクトの追加** ダイアログ ボックス、Visual C を展開し、をクリックして**全般**、 をクリックし、**空のプロジェクト**します。  
  
3.  **名前**テキスト ボックスに「**注釈**、 をクリックし、**追加**します。  
  
4.  ソリューション エクスプ ローラーで右クリック**注釈**し**プロパティ**します。  
  
5.  展開**構成プロパティ** をクリックし、**全般**します。  
  
6.  **全般**一覧で、列の横にテキストを選択**Target Extension**、し、入力 **.lib**します。  
  
7.  **プロジェクトの既定値**、横に列をクリックして**構成の種類**、 をクリックし、**スタティック ライブラリ (.lib)** します。  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>ヘッダー ファイルとソース ファイルを注釈プロジェクトに追加します。  
  
1.  ソリューション エクスプ ローラーで、**注釈**、右クリック**ヘッダー ファイル**、 をクリックして**追加**、順にクリックします**新しい項目の**します。  
  
2.  **新しい項目の追加**ダイアログ ボックスで、をクリックして**ヘッダー ファイル (.h)** します。  
  
3.  **名前**ボックスに「 **annotations.h**  をクリックし、**追加**します。  
  
4.  次のコードをコピーして貼り付けます、 **annotations.h**ファイル、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]エディター。  
  
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
  
5.  ソリューション エクスプ ローラーで右クリック**ソース ファイル**、 をポイント**新規**、 をクリックし、**新しい項目の**。  
  
6.  **新しい項目の追加**ダイアログ ボックスで、をクリックして**コード** をクリックし、 **C++ ファイル (.cpp)**  
  
7.  **名前**ボックスに「 **annotations.cpp**  をクリックし、**追加**します。  
  
8.  次のコードをコピーして貼り付けます、 **annotations.cpp**ファイル、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]エディター。  
  
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
  
9. をクリックして、**ファイル** メニューをクリック**すべて保存**します。



