---
title: デバッグ履歴 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e10387a775c13fd67218b0a52626b4537b01273a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938475"
---
# <a name="historical-debugging"></a>デバッグ履歴
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

デバッグ履歴は、IntelliTrace で収集された情報に依存するデバッグのモードです。 アプリケーションの実行内を前後に移動して、実行の状態を調べることができます。  
  
 IntelliTrace は Visual Studio Enterprise Edition で使用できます (Professional Edition または Community Edition の場合は使用できません)。  
  
## <a name="why-use-historical-debugging"></a>デバッグ履歴を使用する理由  
 ブレークポイントを設定してバグを探すのは、どちらかというと行き当たりばったりな方法です。 バグがありそうな場所のコードの近くにブレークポイントを設定し、デバッガーでアプリケーションを実行して、ブレークポイントがヒットし、実行が中断した場所でバグの原因が明らかになることを期待します。 原因がわからない場合は、コードの別の場所にブレークポイントを設定し、デバッガーを再実行して、問題が見つかるまで繰り返しテスト手順を実行する必要があります。  
  
 ![ブレークポイントを設定する](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 IntelliTrace とデバッグ履歴を使用すると、アプリケーション内を移動して状態を調べることができ (呼び出し履歴およびローカル変数)、ブレークポイントを設定し、デバッグを再実行し、テスト手順を繰り返す必要はありません。 これにより多くの時間を節約できます。実行に時間がかかるテスト シナリオの深い場所にバグがある場合は特に有効です。  
  
## <a name="how-do-i-start-using-historical-debugging"></a>デバッグ履歴の使用を始める方法  
 IntelliTrace は既定で有効になります。 決定する必要があるのは、調査対象のイベントと関数呼び出しだけです。 検索する対象の定義の詳細については、次を参照してください。 [IntelliTrace 機能](../debugger/intellitrace-features.md)します。 IntelliTrace によるデバッグのステップ バイ ステップ アカウントは、次を参照してください。[チュートリアル: IntelliTrace を使用した](../debugger/walkthrough-using-intellitrace.md)します。  
  
## <a name="navigating-your-code-with-historical-debugging"></a>デバッグ履歴でのコード内の移動  
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
  
 `AddAll()` を呼び出した後の `resultInt` の予想される値が 20 であるものとします (`testInt` を 20 回インクリメントした結果)  (また、`AddInt()` 内のバグはわからないものします)。しかし、実際の結果は 44 です。 `AddAll()` を 10 回ステップ実行しないでバグを見つけるにはどうすればよいでしょう。 デバッグ履歴を使うと、迅速かつ簡単にバグを発見できます。 次の手順に従います。  
  
1. [ツール]、[オプション]、[IntelliTrace]、[一般] で、IntelliTrace が有効になっていることを確認し、[IntelliTrace イベントと呼び出し情報] オプションを選択します。 このオプションを選択しないと、ナビゲーション余白が表示されません (後で説明します)。  
  
2. `Console.WriteLine(resultInt);` の行にブレークポイントを設定します。  
  
3. デバッグを開始します。 コードがブレークポイントまで実行されます。 **ローカル**ウィンドウで、ことを確認の値`resultInt`は 44 です。  
  
4. 開く、**診断ツール**ウィンドウ (**/show デバッグ診断ツール**)。 コード ウィンドウは、次のようになります。  
  
    ![コード ウィンドウのブレークポイントで](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5. ブレークポイントのすぐ上の左余白の横に双方向矢印が表示されます。 この領域はナビゲーション余白と呼ばれ、履歴デバッグに使用されます。 矢印をクリックします。  
  
    コード ウィンドウでは、上記のコード行 (`int resultInt = AddIterative(testInt);`) がピンク色で表示されます。 ウィンドウの上には、現在デバッグ履歴中であることを示すメッセージが表示されます。  
  
    コード ウィンドウは、次のようになります。  
  
    ![デバッグ履歴モードでのコード ウィンドウ](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6. ステップ インできますので、`AddAll()`メソッド (**F11**、または**ステップ イン**ナビゲーション余白のボタン。 ステップ前進 (**F10**、または**に次の呼び出しに移動**ナビゲーション余白。 ピンクの行が `j = AddInt(j);` 行に移ります。 **F10 キーを押して**ここで、次のコード行をステップはしません。 代わりに、次の関数呼び出しに移動します。 デバッグ履歴は呼び出しから呼び出しに移動し、関数呼び出しを含まないコード行はスキップされます。  
  
7. ここで、`AddInt()` メソッドにステップ インします。 このコードにバグがあることがすぐにわかります。  
  
   この手順では、デバッグ履歴でできることの表面的な部分のみを見ています。 さまざまな設定とナビゲーション余白がさまざまなボタンの影響に関する詳細については、次を参照してください。 [IntelliTrace 機能](../debugger/intellitrace-features.md)します。





