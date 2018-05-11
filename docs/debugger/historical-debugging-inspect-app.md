---
title: デバッグ履歴でアプリを検査 |Microsoft ドキュメント
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
ms.openlocfilehash: d6a8e4ec27c73516d2eb4ea79ee8beee91dfd19c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio"></a>Visual Studio でデバッグ履歴の IntelliTrace を使用したアプリを検査します。
使用することができます[デバッグ履歴](../debugger/historical-debugging.md)を後方へ移動し、アプリケーションの実行を介して転送状態を調べる。  
  
Visual Studio Enterprise edition、Professional または Community edition を除くで IntelliTrace を使用することができます。  
  
## <a name="navigate-your-code-with-historical-debugging"></a>デバッグ履歴で、コード内を移動します。  
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
  
 いるものとの予期される値`resultInt`呼び出した後`AddAll()`20 (インクリメントした結果`testInt`20 倍)。 (またものとにバグを表示できない`AddInt()`)。結果は 44 実際にします。 `AddAll()` を 10 回ステップ実行しないでバグを見つけるにはどうすればよいでしょう。 デバッグ履歴迅速かつ簡単にバグを発見を使用できます。 次の手順に従います。  
  
1.  **ツール > オプション > IntelliTrace > 全般**IntelliTrace が有効になっていることを確認し、選択**IntelliTrace イベントと呼び出し情報**です。 このオプションを選択しないと、ナビゲーション余白が表示されません (後で説明します)。  
  
2.  `Console.WriteLine(resultInt);` の行にブレークポイントを設定します。  
  
3.  デバッグを開始します。 コードがブレークポイントまで実行されます。 **[ローカル]**ウィンドウがの値`resultInt`44。  
  
4.  開く、**診断ツール**ウィンドウ (**デバッグ > 診断ツールを表示する**)。 コード ウィンドウは、次のようになります。  
  
     ![ブレークポイントでコード ウィンドウ](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5.  ブレークポイントのすぐ上の左余白の横に双方向矢印が表示されます。 この領域は、ナビゲーション余白が呼び出され、履歴デバッグに使用します。 矢印をクリックします。  
  
     コード ウィンドウでは、上記のコード行 (`int resultInt = AddIterative(testInt);`) がピンク色で表示されます。 ウィンドウの上は、現在デバッグ履歴になっているメッセージが表示されます。  
  
     コード ウィンドウは、次のようになります。  
  
     ![デバッグ履歴モードのコード ウィンドウ](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6.  これで、ステップ インすることができます、`AddAll()`メソッド (**F11**、または**ステップ イン**余白で、ナビゲーション ボタンをクリックします。 ステップ前進 (**F10**、または**次の呼び出しに移動**ナビゲーション余白。 ピンクの行が `j = AddInt(j);` 行に移ります。 **F10 キーを押して**ここでは、次のコード行をステップはありません。 代わりに、次の関数呼び出しに移動します。 デバッグ履歴は呼び出しから呼び出しに移動し、関数呼び出しを含まないコード行はスキップされます。  
  
7.  ここで、`AddInt()` メソッドにステップ インします。 このコードにバグがあることがすぐにわかります。  

## <a name="next-steps"></a>次の手順

この手順にすぎませんのデバッグ履歴で行うことができます。

- デバッグ中にスナップショットを表示するを参照してください。 [IntelliTrace ステップ ライトバックを使用してスナップショットを表示する](../debugger/how-to-use-intellitrace-step-back.md)です。
- 他の設定およびナビゲーション余白がさまざまなボタンの影響の詳細についてを参照してください。 [IntelliTrace 機能の](../debugger/intellitrace-features.md)します。