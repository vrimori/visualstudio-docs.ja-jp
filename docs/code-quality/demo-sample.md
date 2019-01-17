---
title: コード分析のためのサンプル C++ プロジェクト
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: ad5a7d3b2c13b603fd3a9f523563c844dda8b67d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852506"
---
# <a name="sample-c-project-for-code-analysis"></a>コード分析のためのサンプル C++ プロジェクト

「[チュートリアル:C/C++ コード分析による障害の検出](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md)」のためのサンプルの作成方法を以下の手順で示します。 この手順で次が作成されます。

- CppDemo という名前の Visual Studio。

- CodeDefects という名前のスタティック ライブラリ プロジェクト。

- Annotations という名前のスタティック ライブラリ プロジェクト。

この手順では、スタティック ライブラリのヘッダー ファイルと *.cpp* ファイルのコードも作成されます。

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>CppDemo ソリューションと CodeDefects プロジェクトを作成する

1. **[ファイル]** メニューをクリックし、**[新規作成]** をポイントし、**[新しいプロジェクト]** をクリックします。

2. **[プロジェクトの種類]** ツリー リストで、Visual C++ が VS の既定の言語になっていない場合、**[その他の言語]** を展開します。

3. **[Visual C++]** を展開し、**[全般]** をクリックします。

4. **[テンプレート]** で **[空のプロジェクト]** をクリックします。

5. **[名前]** テキスト ボックスに「**CodeDefects**」と入力します。

6. **[ソリューションのディレクトリを作成]** チェック ボックスをオンにします。

7. **[ソリューション名]** テキスト ボックスに「**CppDemo**」と入力します。

## <a name="configure-the-codedefects-project-as-a-static-library"></a>CodeDefects プロジェクトをスタティック ライブラリとして構成する

1. ソリューション エクスプローラーで **[CodeDefects]** を右クリックし、**[プロパティ]** をクリックします。

2. **[構成プロパティ]** を展開し、**[全般]** をクリックします。

3. **[全般]** リストで **[ターゲットの拡張子]** の隣にある列のテキストを選択し、「**.lib**」と入力します。

4. **[プロジェクトの既定値]** で **[構成のタイプ]** の隣にある列をクリックし、**[スタティック ライブラリ (.lib)]** をクリックします。

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>CodeDefects プロジェクトにヘッダーとソース ファイルを追加する

1. ソリューション エクスプローラーで **[CodeDefects]** を展開し、**[ヘッダー ファイル]** を右クリックし、**[追加]** をクリックし、**[新しい項目]** をクリックします。

2. **[新しい項目の追加]** ダイアログ ボックスで、**[コード]** をクリックし、**[ヘッダー ファイル (.h)]** をクリックします。

3. **[名前]** ボックスに「**Bug.h**」と入力し、**[追加]** をクリックします。

4. 次のコードをコピーし、Visual Studio エディターで *Bug.h* ファイルに貼り付けます。

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

5. ソリューション エクスプローラーで、**[ソース ファイル]** を右クリックし、**[新規作成]** をポイントし、**[新しい項目]** をクリックします。

6. **[新しい項目の追加]** ダイアログ ボックスで、**[C++ ファイル (.cpp)]** をクリックします。

7. **[名前]** ボックスに「**Bug.cpp**」と入力し、**[追加]** をクリックします。

8. 次のコードをコピーし、Visual Studio エディターで *Bug.cpp* ファイルに貼り付けます。

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

9. **[ファイル]** メニューをクリックし、**[すべて保存]** をクリックします。

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Annotations プロジェクトを追加し、それをスタティック ライブラリとして構成する

1. ソリューション エクスプローラーで **[CppDemo]** をクリックし、**[追加]** をポイントして **[新しいプロジェクト]** をクリックします。

2. **[新しいプロジェクトの追加]** ダイアログ ボックスで [Visual C++] を展開し、**[全般]** をクリックし、**[空のプロジェクト]** をクリックします。

3. **[名前]** テキスト ボックスに「**Annotations**」と入力し、**[追加]** をクリックします。

4. ソリューション エクスプローラーで **Annotations** を右クリックし、**[プロパティ]** をクリックします。

5. **[構成プロパティ]** を展開し、**[全般]** をクリックします。

6. **[全般]** リストで **[ターゲットの拡張子]** の隣にある列のテキストを選択し、「**.lib**」と入力します。

7. **[プロジェクトの既定値]** で **[構成のタイプ]** の隣にある列をクリックし、**[スタティック ライブラリ (.lib)]** をクリックします。

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>ヘッダー ファイルとソース ファイルを注釈プロジェクトに追加する

1. ソリューション エクスプローラーで **[Annotations]** を展開し、**[ヘッダー ファイル]** を右クリックし、**[追加]** をクリックし、**[新しい項目]** をクリックします。

2. **[新しい項目の追加]** ダイアログ ボックスで、**[ヘッダー ファイル (.h)]** をクリックします。

3. **[名前]** テキスト ボックスに「**annotations.h**」と入力し、**[追加]** をクリックします。

4. 次のコードをコピーし、Visual Studio エディターで *annotations.h* ファイルに貼り付けます。

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

5. ソリューション エクスプローラーで、**[ソース ファイル]** を右クリックし、**[新規作成]** をポイントし、**[新しい項目]** をクリックします。

6. **[新しい項目の追加]** ダイアログ ボックスで、**[コード]** をクリックし、**[C++ ファイル (.cpp)]** をクリックします。

7. **[名前]** テキスト ボックスに「**annotations.cpp**」と入力し、**[追加]** をクリックします。

8. 次のコードをコピーし、Visual Studio エディターで *annotations.cpp* ファイルに貼り付けます。

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

9. **[ファイル]** メニューをクリックし、**[すべて保存]** をクリックします。
