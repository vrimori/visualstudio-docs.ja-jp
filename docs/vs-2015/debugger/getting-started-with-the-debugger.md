---
title: Getting Started with the Debugger |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: get-started-article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2269ceae72f620677f51af960f7fe164f7982412
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544473"
---
# <a name="getting-started-with-the-debugger"></a>デバッガーの使用開始
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[デバッガー機能ツアー](https://docs.microsoft.com/visualstudio/debugger/debugger-feature-tour)します。  
  
Visual Studio デバッガーは、どの言語でも簡単に使用できます。 ここでは、簡単な C# プログラムのデバッグ方法について説明しますが、C++、JavaScript などの他の言語のコードに同じ手順を適用することができます。  
  
##  <a name="BKMK_Start_debugging_a_VS_project"></a> 基本的な c# プロジェクトをデバッグします。  
 単純な c# コンソール アプリケーションから始めましょう (**ファイル/新しいプロジェクト/** を選択し、 **Visual c#** 選び**コンソール アプリケーション**)。 Visual Studio で初めて作業する場合を参照してください。[チュートリアル: 単純なアプリケーション作成](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)です。 **Main**だけメソッドは整数変数を 10 回に 1 が加算し、コンソールに結果を出力します。  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i <= 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 このコードをビルド、**デバッグ**構成します。 この構成は、既定で設定されています。 構成の詳細については、次を参照してください。[ビルド構成について](../ide/understanding-build-configurations.md)します。  
  
 クリックして、デバッガーでこのコードを実行**デバッグ]/[デバッグの開始**(または**開始**ツールバーで、または**F5**)。 アプリケーションはほぼ即座に終了するため、実際に何かがコンソール ウィンドウに出力されたかどうかは分かりません。  
  
 ブレークポイントを設定してから先に進むことで、コンソール ウィンドウを確認する間実行を停止することができます。 ブレークポイントを設定するにカーソルを置く、`Console.WriteLine`行し、をクリックして**デバッグ/新しいブレークポイント/関数のブレークポイント**、または同じ行の左余白内をクリックします。 ブレークポイントは次のように表示されます。  
  
 ![ブレークポイントを設定する](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 ブレークポイントの詳細については、次を参照してください。[を使用してブレークポイント](../debugger/using-breakpoints.md)します。  
  
##  <a name="BKMK_Inspect_Variables"></a> 変数を検査します。  
 多くの場合、デバッグするには、特定の時点で予期される値が含まれていない変数を検索する必要があります。 いくつかの変数を検査することができます、方法を示します。  
  
 デバッグを再度開始します。 `Console.WriteLine` のコードが実行される前に実行が停止します。 先に進むで実行するように発生することができます (をクリックして**デバッグ]/[ステップ オーバー**または**F10**)。 ここで選択した可能性があります**ステップ イン**(**F11**) と同じ結果を取得後で違いを説明します。 メソッドの最後の中かっこの行が黄色に変わっているはずです。 コンソール ウィンドウを見てください。 表示する必要があります**10**します。  
  
 ポイントすると、 **testInt**変数がデータ ヒントで現在の値を表示します。  
  
 ![DBG&#95;基本&#95;データ&#95;ヒント](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 コード ウィンドウのすぐ下に表示されます、 **[自動変数]**、**ローカル**、および**ウォッチ**windows。 これらのウィンドウは、実行時における変数の現行値を表示します。 両方、 **[自動変数]** と**ローカル**windows show **testInt**の値を持つ**10**します。  
  
 ![[自動変数] ウィンドウのデバッグ時に](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 これらのウィンドウの詳細については、次を参照してください。 [[自動変数] と [ローカル Windows](../debugger/autos-and-locals-windows.md)します。  
  
 プログラムを進めながら、変数の値がどのように変化するかを見てみましょう。 ブレークポイントを設定、`testInt += 1;`し、デバッグを再開します。 表示する必要があります**testInt**で、**ローカル**と **[自動変数]** windows が**0**、および**は**は**1**します。 デバッグを続行すると (**デバッグ]/[続行**、または**続行**ツールバーで、または**F5**)、ことを確認の値**testInt**変更**1**、し**2**など。 これらの変更を見るが面倒なときは、ブレークポイントを削除 (**]/[デバッグのブレークポイント**余白内でクリックしてまたは)、デバッグを続行します。 すべてのブレークポイントを削除する場合をクリックして**デバッグ/すべてのブレークポイントを削除**、または**CTRL + SHIFT + F9**、 をクリック**はい**確認するダイアログ ボックスで**Do youすべてのブレークポイントを削除しますか。**.  
  
## <a name="stepping-into-and-over-function-calls"></a>関数の呼び出しのステップ インとステップ オーバー  
 デバッガーをステートメント-by-ステートメント内でコードを実行することができます (**ステップ イン**) か、デバッガーは関数をスキップ中にコードを実行することができます (**ステップ オーバー**) (に強い関心いるコードを迅速に取得するには関数コードが実行されます)。 どちらの方法で、同じデバッグ セッションを切り替えることができます。  
  
 間の差を表示する**ステップ イン**と**ステップ オーバー**、別のメソッドによって呼び出されるメソッドを追加する必要があります。 C# アプリケーションにメソッドを追加し、Main メソッドから呼び出します。 コードは次のようになります。  
  
```csharp  
static void Main(string[] args)  
{  
    Method1();  
    Console.WriteLine("end");  
}  
  
private static void Method1()  
{  
    Console.WriteLine("in Method1");  
}  
```  
  
 Main メソッド内の `Method1();` の呼び出しにブレークポイントを設定し、デバッグを開始します。 実行が中断したときにクリックして**デバッグ]/[ステップ イン**(または**ステップ イン**ツールバーで、または**F11**)。 Method1() 内の最初の中かっこでもう一度実行が中断します。  
  
 ![コードにステップ イン](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 デバッグを停止し、再び起動し、実行がブレークポイントで中断、 をクリックして**デバッグ/ステップ オーバー** (または**ステップ オーバー**ツールバーで、または**F10**)。 実行が `Console.WriteLine("end");` で再度中断します。  
  
 場合は、デバッガーでコード間の移動の詳細を参照してください[デバッガーでコード間の移動](../debugger/navigating-through-code-with-the-debugger.md)します。





