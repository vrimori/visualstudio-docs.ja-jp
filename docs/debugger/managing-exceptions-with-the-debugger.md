---
title: Visual Studio デバッガーでの例外の管理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/05/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors
- exception handling, during debugging
- errors [debugger]
- debugger, runtime errors
- On Error-style error handlers
- exceptions, Win32
- run-time errors, debugging
- Win32, exceptions
- run time, exceptions
- error handling
- debugging [Visual Studio], exception handling
- common language runtime, exceptions
- native run-time checks
- exceptions, debugging
ms.assetid: 43a77fa8-37d0-4c98-a334-0134dbca4ece
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 063f4581a741325ce34022b731322cf0a4e37e39
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>デバッガーでは、Visual Studio での例外を管理します。

例外は、プログラムの実行中に発生したエラー状態を示します。 わかりますデバッガーで、中断する例外 (または例外のセット) し、この時点で、デバッガーが中断 (デバッガーが停止したらを示しています、例外がスローされました)。 追加するか例外を削除します。 Visual Studio で開いて、ソリューションを使用して**デバッグ > Windows > 例外設定**を開くには、**例外設定**ウィンドウです。 

最も重要な例外に応答するハンドラーを提供する必要がありますが、常に実行を中断するいくつかの例外にデバッガーを構成する方法を理解することが重要です。
  
例外が発生すると、[出力] ウィンドウに例外メッセージが書き込まれます。 次のような場合、例外によって実行が中断される可能性があります。  
  
-   例外がスローされたが、処理されない場合。  
  
-   デバッガーを構成するとき、ハンドラーが呼び出される前に実行を中断します。  
  
-   設定した場合[マイ コードのみ](../debugger/just-my-code.md)、ユーザー コードで処理されていないすべての例外で中断する、デバッガーが構成されているとします。  
  
> [!NOTE]
>  ASP.NET は、エラー ページをブラウザーに表示する最上位の例外ハンドラーを持っています。 **マイ コードのみ** が有効ではない場合、実行は中断されません。 例については、以下の「 [Setting the debugger to continue on user-unhandled exceptions](../debugger/managing-exceptions-with-the-debugger.md#BKMK_UserUnhandled) 」をご覧ください。  
  
> [!NOTE]
>  Visual Basic アプリケーションで、デバッガーでは on Error 形式のエラー ハンドラーを使用する場合でも、すべてのエラーを例外として管理します。    
  
## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>例外がスローされたときに中断するようにデバッガー  
例外がスローされた時点でデバッガーは実行を中断することができます。これにより、例外ハンドラーが呼び出される前に例外を調査する機会が与えられます。  
  
**例外設定**ウィンドウ (**デバッグ > Windows > 例外設定**)、例外のカテゴリのノードを展開 (たとえば、 **Common Language Runtime Exceptions**、つまり、.NET に関する例外)、そのカテゴリ内の特定の例外のチェック ボックスをオンにし (たとえば**System.AccessViolationException**)。 例外のカテゴリ全体を選択することもできます。  
  
![AccessViolationException をチェック](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")  

> [!TIP]
> 特定の例外を見つけるには、 **[例外設定]** ツールバーの **[検索]** ウィンドウを使用するか、検索機能を使用して特定の名前空間 (たとえば **System.IO**) をフィルター処理します。
  
例外を選択した場合、**例外設定**ウィンドウで、処理やハンドルされていないときに関係なく、例外がスローされるたびに、デバッガーの実行が中断されます。 この時点で、例外は初回例外と呼ばれます。 例として、いくつかのシナリオを以下に示します。  
  
*  次の C# コンソール アプリケーションで、Main メソッドは **try/catch** ブロック内で `try/catch` をスローします。  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        try  
        {  
            throw new AccessViolationException();  
            Console.WriteLine("here");  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("caught exception");  
        }  
        Console.WriteLine("goodbye");  
    }  
    ```  
  
     **try/catch** で **[例外設定]**のチェック ボックスをオンにした場合、このコードをデバッガーで実行すると、 `throw` 行で実行が中断されます。 実行は続行することができます。 コンソールには、次の行が両方とも表示される必要があります。  
  
    ```  
    caught exception  
    goodbye  
    ```  
  
     しかし、 `here` 行は表示されていません。  
  
*  C# コンソール アプリケーションは、2 つのメソッド、例外をスローして処理するメソッドと同じ例外をスローし、それを処理しない 2 つ目のメソッドを持つクラスを含むクラス ライブラリを参照します。  
  
    ```csharp 
    public class Class1  
    {  
        public void ThrowHandledException()  
        {  
            try  
            {  
                throw new AccessViolationException();  
            }  
            catch (AccessViolationException ave)  
            {  
                Console.WriteLine("caught exception" + ave.Message);  
            }  
        }  
  
        public void ThrowUnhandledException()  
        {  
            throw new AccessViolationException();  
        }  
    }  
    ```  
  
     コンソール アプリケーションの Main() メソッドを次に示します。  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        Class1 class1 = new Class1();  
        class1.ThrowHandledException();  
        class1.ThrowUnhandledException();  
    }  
    ```  
  
     あれば**AccessViolationException**チェックイン**例外設定**で中断は、デバッガーの実行でこのコードを実行すると、`throw`両方で行**ThrowHandledException()**と**ThrowUnhandledException()**です。  
  
 例外設定を既定値に戻す場合は、ツールバーの **[復元]** ボタンをクリックします。  
  
 ![例外設定に戻す](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")  
  
##  <a name="BKMK_UserUnhandled"></a> ユーザーよって処理されない例外のまま続行するようにデバッガー  
 [ [Just My Code](../debugger/just-my-code.md)] を使用して .NET コードまたは JavaScript コードをデバッグする場合、ユーザー コードで処理されないが他の場所で処理される例外について、中断しないようにデバッガーを設定することができます。  
  
1.  **[例外設定]** ウィンドウでコンテキスト メニューを開くには、ウィンドウで右クリックし、 **[列の表示]**を選択します ( **[マイ コードのみ]**を選択していない場合、このコマンドは表示されません)。  
  
2.  **[追加のアクション]**という名前の 2 つ目の列が表示されます。 この列には、特定の例外に対して **[ユーザー コードで処理されない場合は続行]** が表示されます。すなわち、例外がユーザー コードで処理されないが外部コードで処理される場合、デバッガーは中断されません。  
  
3.  この設定は、特定の例外に対して変更することも (例外を選択し、右クリックし、 **[ユーザー コードで処理されない場合は続行]**を選択または選択解除する)、例外のカテゴリ全体 (たとえば、すべての共通言語ランタイム例外) に対して変更することもできます。  
  
 たとえば、ASP.NET Web アプリケーションは、例外を HTTP 500 状態コードに変換して処理します ([ASP.NET API での例外の処理](http://www.asp.net/web-api/overview/error-handling/exception-handling))。この場合、例外の原因を特定できないことがあります。 次の例では、ユーザー コードは、 `String.Format()` をスローする <xref:System.FormatException>を呼び出します。 実行は次のように中断されます。  
  
 ![ユーザーに設定された改&#45;中断例外](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")  
  
## <a name="add-and-delete-exceptions"></a>追加および削除例外  
 例外は追加および削除することができます。 任意のカテゴリから任意の種類の例外を削除するには、例外を選択し、 **[例外設定]** ツールバーの **[削除]** ボタン (マイナス記号) をクリックするか、または例外を右クリックし、コンテキスト メニューから **[削除]** をクリックします。 例外を削除することは、例外をオフにするのと同じ結果になります。すなわち、該当する例外がスローされたとき、デバッガーは中断されません。  
  
 例外を追加するには、 **[例外設定]** ウィンドウで、例外カテゴリの 1 つ (たとえば、 **[共通言語ランタイム]**) を選択し、 **[追加]** ボタンをクリックします。 例外の名前を入力します (たとえば、 **System.UriTemplateMatchException**)。 例外は一覧 (アルファベット順の) に追加され、自動的にオンになります。  
  
 GPU メモリ アクセス例外、JavaScript ランタイム例外、または Win32 例外というカテゴリに例外を追加する場合は、エラー コードと説明を含める必要があります。  
  
> [!TIP]
>  スペルを確認してください。 **例外設定**ウィンドウで、追加された例外の存在を確認しません。 入力した場合は**Sytem.UriTemplateMatchException**、その例外のエントリが表示されます (ではなく**System.UriTemplateMatchException**)。  
  
 例外の設定は、ソリューションの .suo ファイルに永続化され、特定のソリューションに適用されます。 ソリューション全体で特定の例外の設定を再利用することはできません。 この時点では、追加された例外だけが保存されます。削除された例外は保持されません。 すなわち、例外を追加してから、ソリューションをいったん閉じて、再度開いた場合、その例外は表示されたままです。 しかし、例外を削除してから、ソリューションをいったん閉じて、再度開いた場合、例外は再表示されます。  
  
 **[例外設定]** ウィンドウでは、C# の汎用的な例外タイプをサポートしていますが、Visual Basic の汎用的な例外タイプはサポートしていません。 `MyNamespace.GenericException<T>`のような例外が発生したときに実行が中断されるようにするには、例外を **[MyNamespace.GenericException`1]**として追加する必要があります。 すなわち、例外を次のように作成した場合:  
  
```csharp  
public class GenericException<T> : Exception  
{  
    public GenericException() : base("This is a generic exception.")  
    {  
    }  
}  
```  
  
 **[例外設定]** に例外を次のように追加できます。  
  
 ![一般的な例外を追加する](../debugger/media/addgenericexception.png "AddGenericException")  

## <a name="add-conditions-to-an-exception"></a>例外に条件を追加します。

例外に条件を設定することができます、**例外設定** ダイアログ ボックス。 現在サポートされている条件には、例外のるまたは除外するには、モジュール名が含まれます。 条件として、モジュール名を設定することにより、特定のコード モジュールでのみ例外を中断することもできます。 または特定のモジュールの互換性に影響を回避できます。

> [!NOTE]
> 新機能は、例外への条件の追加 [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

条件付きの例外を追加するには、選択、**条件の編集**アイコン [例外設定] ダイアログ ボックスまたは例外を右クリックして選択**条件の編集**です。

![例外条件](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")
  
## <a name="see-also"></a>関連項目  
 [例外の後の実行の継続](../debugger/continuing-execution-after-an-exception.md)   
 [方法: 例外の後にシステム コードを調べる](../debugger/how-to-examine-system-code-after-an-exception.md)   
 [方法: ネイティブ ランタイム チェックの使用](../debugger/how-to-use-native-run-time-checks.md)   
 [C ランタイム ライブラリなしのチェックの実行時刻を使用します。](../debugger/using-run-time-checks-without-the-c-run-time-library.md)   
 [デバッガーの基本事項](../debugger/debugger-basics.md)