---
title: デモのサンプル
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99b557114e8650c2370b81d2ba627b987929414d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="demo-sample"></a>デモのサンプル

この次の手順のサンプルを作成する方法を示します[チュートリアル: 分析するコードと C/C++ コードの欠陥](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md)です。 プロシージャを作成します。

-   A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CppDemo をという名前のソリューションです。

-   スタティック ライブラリ プロジェクトでは、CodeDefects という名前です。

-   スタティック ライブラリ プロジェクトには、注釈がという名前です。

 手順では、静的ライブラリのヘッダーと .cpp ファイルのコードも提供します。

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>CppDemo ソリューションおよび CodeDefects プロジェクトを作成します。

1.  クリックして、**ファイル** メニューのをポイント**新規**、順にクリック**新しいプロジェクト**です。

2.  **プロジェクトの種類**リストをツリーで、Visual C は VS で、既定の言語ではない場合は展開**他の言語**します。

3.  展開**Visual C**、クリックして**全般**です。

4.  **テンプレート**をクリックして**空のプロジェクト**です。

5.  **名前**テキスト ボックスで、「 **CodeDefects**です。

6.  選択、**ソリューションのディレクトリを作成**チェック ボックスをオンします。

7.  **ソリューション名**テキスト ボックスで、「 **CppDemo**です。

## <a name="configure-the-codedefects-project-as-a-static-library"></a>スタティック ライブラリとして CodeDefects プロジェクトを構成します。

1.  ソリューション エクスプ ローラーで右クリック**[CodeDefects** ] をクリックし、**プロパティ**です。

2.  展開**構成プロパティ** をクリックし、**全般**です。

3.  **全般**一覧で、列の横にテキストを選択**ターゲットの拡張子**、し、入力**.lib**です。

4.  **プロジェクトの既定値**、横に列をクリックして**構成の種類**、クリックして**スタティック ライブラリ (.lib)**です。

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>CodeDefects プロジェクトに、ヘッダーとソース ファイルを追加します。

1.  ソリューション エクスプ ローラーで、 **[CodeDefects**を右クリックして**ヘッダー ファイル**、] をクリックして**追加**、順にクリック**新しい項目の**します。

2.  **新しい項目の追加**ダイアログ ボックスで、をクリックして**コード**、クリックして**ヘッダー ファイル (.h)**です。

3.  **名前**ボックスに、入力**Bug.cpp**  をクリックし、**追加**です。

4.  次のコードをコピーして貼り付けます、 **Bug.cpp**ファイルで、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]エディターです。

    ```cpp
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

5.  ソリューション エクスプ ローラーで右クリック**ソース ファイル**、 をポイント**新規**、クリックして**新しい項目の**します。

6.  **新しい項目の追加**ダイアログ ボックスで、をクリックして**C++ ファイル (.cpp)**

7.  **名前**ボックスに、入力**Bug.cpp**  をクリックし、**追加**です。

8.  次のコードをコピーし、Bug.h ファイルに貼り付け、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]エディターです。

    ```cpp
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

9. クリックして、**ファイル** メニューをクリックして**すべて保存**です。

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>注釈プロジェクトを追加し、スタティック ライブラリとして構成します。

1.  ソリューション エクスプ ローラーでクリックして**[CppDemo**、] をポイント**追加**、順にクリック**新しいプロジェクト**です。

2.  **新しいプロジェクトの追加** ダイアログ ボックス、Visual C を展開し、をクリックして**全般**、クリックして**空のプロジェクト**です。

3.  **名前**テキスト ボックスで、「**注釈**、クリックしてして**追加**です。

4.  ソリューション エクスプ ローラーで右クリック**注釈** をクリックし、**プロパティ**です。

5.  展開**構成プロパティ** をクリックし、**全般**です。

6.  **全般**一覧で、列の横にテキストを選択**ターゲットの拡張子**、し、入力**.lib**です。

7.  **プロジェクトの既定値**、横に列をクリックして**構成の種類**、クリックして**スタティック ライブラリ (.lib)**です。

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>ヘッダー ファイルとソース ファイルを注釈プロジェクトに追加します。

1.  ソリューション エクスプ ローラーで、**注釈**を右クリックして**ヘッダー ファイル**、 をクリックして**追加**、順にクリック**新しい項目の**します。

2.  **新しい項目の追加**ダイアログ ボックスで、をクリックして**ヘッダー ファイル (.h)**です。

3.  **名前**ボックスに、入力**annotations.h**  をクリックし、**追加**です。

4.  次のコードをコピーして貼り付けます、 **annotations.h**ファイルで、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]エディターです。

    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>

    struct LinkedList
    {
        struct LinkedList* next;
        int data;
    };

    typedef struct LinkedList LinkedList;

    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();

    ```

5.  ソリューション エクスプ ローラーで右クリック**ソース ファイル**、 をポイント**新規**、クリックして**新しい項目の**します。

6.  **新しい項目の追加**ダイアログ ボックスで、をクリックして**コード** をクリックし、 **C++ ファイル (.cpp)**

7.  **名前**ボックスに、入力**annotations.cpp**  をクリックし、**追加**です。

8.  次のコードをコピーして貼り付けます、 **annotations.cpp**ファイルで、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]エディターです。

    ```cpp
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

9. クリックして、**ファイル** メニューをクリックして**すべて保存**です。