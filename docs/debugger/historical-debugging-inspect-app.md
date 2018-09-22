---
title: デバッグ履歴を使用してアプリを検査 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2309a3213344607fa0f5b2f626fc67af2eff8f79
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542339"
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio"></a>Visual Studio でデバッグ履歴の IntelliTrace を使用してアプリを調べる
使用することができます[デバッグ履歴](../debugger/historical-debugging.md)を後方に移動し、アプリケーションの実行を転送してその状態を検査します。  
  
Visual Studio Enterprise edition がない、Professional または Community edition では、IntelliTrace を使用できます。  
  
## <a name="navigate-your-code-with-historical-debugging"></a>デバッグ履歴でコードを移動します。  
 バグのある単純なプログラムから始めましょう。 C# コンソール アプリケーションで次のコードを追加します。  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    int resultInt = AddAll(testInt);  
    Console.WriteLine(resultInt);  
}  
private static int AddAll(int j)  
{  
    for (int i = 0; i < 20; i++)  
    {  
        j = AddInt(j);  
    }  
    return j;  
}  
  
private static int AddInt(int add)  
{  
    if (add == 10)  
    {  
        return add += 25;  
    }  
    return ++add;  
}  
```  
  
 いると仮定の予期される値`resultInt`呼び出した後`AddAll()`20 (インクリメントした結果`testInt`20 回)。 (でバグが表示されないものとしますも`AddInt()`)。実際には 44 になります。 `AddAll()` を 10 回ステップ実行しないでバグを見つけるにはどうすればよいでしょう。 デバッグ履歴をより速くより簡単にバグを見つけるに使用できます。 次の手順に従います。  
  
1.  **ツール > オプション > IntelliTrace > 全般**、IntelliTrace が有効になっていることを確認および選択**IntelliTrace イベントと呼び出し情報**します。 このオプションを選択しないと、ナビゲーション余白が表示されません (後で説明します)。  
  
2.  `Console.WriteLine(resultInt);` の行にブレークポイントを設定します。  
  
3.  デバッグを開始します。 コードがブレークポイントまで実行されます。 **ローカル**ウィンドウで、ことを確認の値`resultInt`は 44 です。  
  
4.  開く、**診断ツール**ウィンドウ (**デバッグ > 診断ツールの表示**)。 コード ウィンドウは、次のようになります。  
  
     ![コード ウィンドウのブレークポイントで](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5.  ブレークポイントのすぐ上の左余白の横に双方向矢印が表示されます。 この領域は、ナビゲーション余白は呼び出され、履歴デバッグに使用されます。 矢印をクリックします。  
  
     コード ウィンドウでは、上記のコード行 (`int resultInt = AddIterative(testInt);`) がピンク色で表示されます。 ウィンドウの上、デバッグ履歴にメッセージが表示されます。  
  
     コード ウィンドウは、次のようになります。  
  
     ![デバッグ履歴モードでのコード ウィンドウ](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6.  ステップ インできますので、`AddAll()`メソッド (**F11**、または**ステップ イン**ナビゲーション余白のボタン。 ステップ前進 (**F10**、または**に次の呼び出しに移動**ナビゲーション余白。 ピンクの行が `j = AddInt(j);` 行に移ります。 **F10 キーを押して**ここで、次のコード行をステップはしません。 代わりに、次の関数呼び出しに移動します。 デバッグ履歴は呼び出しから呼び出しに移動し、関数呼び出しを含まないコード行はスキップされます。  
  
7.  ここで、`AddInt()` メソッドにステップ インします。 このコードにバグがあることがすぐにわかります。  

## <a name="next-steps"></a>次の手順

この手順ほんの一部のデバッグ履歴で行うことができます。

- デバッグ中にスナップショットを表示するを参照してください。 [IntelliTrace を使用して前のアプリ状態を検査](../debugger/view-historical-application-state.md)します。
- さまざまな設定とナビゲーション余白がさまざまなボタンの影響に関する詳細については、次を参照してください。 [IntelliTrace 機能](../debugger/intellitrace-features.md)します。