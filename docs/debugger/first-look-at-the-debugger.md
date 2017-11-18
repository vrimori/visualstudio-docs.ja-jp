---
title: "デバッガーでは、Visual Studio で作業を開始 |Microsoft ドキュメント"
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 0b3138c4-b840-446a-a15c-10ed8e2dd050
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68eb471f1db42b60114c2a14745ba4771b640c0d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="get-started-with-the-visual-studio-debugger"></a>Visual Studio デバッガーを概要します。
Visual Studio デバッガーは、どの言語でも簡単に使用できます。 ここでは、単純な c# プログラムをデバッグする方法を説明しますが、C++、JavaScript などの他の言語のコードを同じ手順を適用することができます。

同様の機能を示すビデオを見るには、次を参照してください。[デバッガーの使用を開始する](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6)です。
  
##  <a name="BKMK_Start_debugging_a_VS_project"></a>基本的な c# プロジェクトをデバッグします。  
 簡単な c# コンソール アプリケーションから始めましょう (**ファイル > 新規 > プロジェクト**選択してから、 **Visual c#**し**コンソール アプリケーション**)。 初めて作業する前に Visual Studio で、表示[チュートリアル: 簡単なアプリケーションを作成する](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)です。 **Main**だけメソッドは整数変数を 10 回に 1 が加算し、コンソールに結果を出力します。  
  
```CSharp  
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
  
 このコードをビルド、**デバッグ**構成します。 この構成は、既定で設定されています。 構成の詳細については、次を参照してください。[ビルド構成について](../ide/understanding-build-configurations.md)です。  
  
 クリックして、デバッガーでこのコードを実行**デバッグ > [デバッグ開始]** (または**開始**ツールバーで、または**f5 キーを押して**)。 アプリケーションは、コンソール ウィンドウで、印刷されたものかどうかを指示することはできません実際には、ほぼ即座に終了する必要があります。  
  
 ブレークポイントを設定してから先に進むことで、コンソール ウィンドウを確認する間実行を停止することができます。 ブレークポイントを設定するカーソルを置きます、`Console.WriteLine`行をクリックして**デバッグ > 新しいブレークポイント > 関数のブレークポイント**、または、同じ行の左余白内をクリックします。 ブレークポイントは次のように表示されます。  
  
 ![ブレークポイントを設定する](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 ブレークポイントの詳細については、次を参照してください。[を使用してブレークポイント](../debugger/using-breakpoints.md)です。  
  
##  <a name="BKMK_Inspect_Variables"></a>変数を検査します。  
 多くの場合、デバッグするには、特定の時点で必要な値が含まれていない変数を検索するが含まれます。 いくつかの変数を検査することができます、方法を示します。  
  
 デバッグを再度開始します。 `Console.WriteLine` のコードが実行される前に実行が停止します。 事前ステップで実行するようになります (をクリックして**デバッグ > ステップ オーバー**または**F10**)。 ここで選択した可能性があります**ステップ イン**(**F11**) 同じ結果を取得し、違いを後で説明しています。 メソッドの最後の中かっこの行が黄色に変わっているはずです。 コンソール ウィンドウを見てください。 表示されるはず**10**です。  
  
 合わせることができます、 **testInt**変数がデータ ヒントで、現在の値を表示します。  
  
 ![DBG &#95;です。基本 #95; データ &#95;です。ヒント](../debugger/media/dbg_basics_data_tips.png "DBG_Basics_Data_Tips")  
  
 コード ウィンドウのすぐ下に表示されるはずの**[自動変数]**、 **[ローカル]**、および**ウォッチ**windows です。 これらのウィンドウは、実行時における変数の現行値を表示します。 両方、 **[自動変数]**と**ローカル**windows 表示**testInt**の値を持つ**10**です。  
  
 ![[自動変数] ウィンドウのデバッグ時に](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 これらのウィンドウの詳細については、次を参照してください。 [[自動変数] と [ローカル] ウィンドウ](../debugger/autos-and-locals-windows.md)します。  
  
 プログラムを進めながらように、変数の値がどのように変化するかを確認してみましょう。 ブレークポイントを設定、`testInt += 1;`し、デバッグを再開します。 表示する必要があります**testInt**で、 **[ローカル]**と**[自動変数]** windows が**0**、および**すれば**は**1**です。 デバッグを続行すると (**デバッグ > 続行**、または**続行**ツールバーで、または**f5 キーを押して**) がの値**testInt**変更**1**、し**2**のようにします。 これらの変更を見るが面倒なときは、ブレークポイントを削除 (**デバッグ > ブレークポイントの切り替え**余白にそれをクリックしてまたは)、デバッグを続行します。 すべてのブレークポイントを削除する場合をクリックして**デバッグ > すべてのブレークポイントの削除**、または**CTRL + SHIFT + F9**、 をクリック**はい**確認するダイアログ ボックスで**しないでくださいすべてのブレークポイントを削除しますか?**.  
  
## <a name="stepping-into-and-over-function-calls"></a>関数の呼び出しのステップ インとステップ オーバー  
 ステートメントによって--ステートメントにあるデバッガーでコードを実行することができます (**ステップ イン**) したり、デバッガーは関数をスキップ中にコードを実行したりできます (**ステップ オーバー**) 興味のある複数 (コードをすばやく表示するには関数コードが実行されます)。 どちらの方法で、同じデバッグ セッションを切り替えることができます。  
  
 間の違いを表示する**ステップ イン**と**ステップ オーバー**、別の方法で呼び出されるメソッドを追加する必要があります。 C# アプリケーションにメソッドを追加し、Main メソッドから呼び出します。 コードは次のようになります。  
  
```CSharp  
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
  
 Main メソッド内の `Method1();` の呼び出しにブレークポイントを設定し、デバッグを開始します。 実行が停止したらをクリックして**デバッグ > ステップ イン**(または**ステップ イン**ツールバーで、または**F11**)。 Method1() 内の最初の中かっこでもう一度実行が中断します。  
  
 ![コードにステップ イン](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 デバッグを停止し、再び起動し、実行がブレークポイントで中断をクリックして**デバッグ > ステップ オーバー** (または**ステップ オーバー**ツールバーで、または**F10**)。 実行が `Console.WriteLine("end");` で再度中断します。  
  
 デバッガーでは、コード内の移動の詳細については、「たい場合[デバッガーでのコードを移動する](../debugger/navigating-through-code-with-the-debugger.md)です。