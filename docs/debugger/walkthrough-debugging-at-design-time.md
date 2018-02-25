---
title: "デザイン時に Visual Studio デバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/21/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 33e0210023de05047957e7fbf55a8f970fda19d9
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="debug-at-design-time-in-visual-studio"></a>Visual Studio では、デザイン時デバッグします。

一部のシナリオでをデザイン時のコードをデバッグすることがあります、アプリケーションの実行中の代わりに時刻します。 こうことを使用して、**イミディ エイト**ウィンドウです。 データ バインディング コードなどの他のコードと対話する XAML コードをデバッグする場合は、使用**デバッグ** > **プロセスにアタッチする**を行うには。
  
### <a name="debug-at-design-time-using-the-immediate-window"></a>イミディ エイト ウィンドウを使用してデザイン時にデバッグします。  

Visual Studio を使用することができます**イミディ エイト**ウィンドウで、アプリケーションが実行されていないときに、関数またはサブルーチンを実行します。 関数またはサブルーチンにブレークポイントが含まれているとき、適切なポイントで実行を中断します。 デバッガー ウィンドウを使用して、プログラムの状態を確認できます。 この機能は、デザイン時のデバッグと呼ばれます。  

Visual basic では、次の例ですが、**イミディ エイト**c# および C++ アプリケーション ウィンドウでもサポートされています。
  
1.  次のコードを Visual Basic コンソール アプリケーションに貼り付けます。  
  
    ```vb  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  `s="Add BreakPoint Here"` という行にブレークポイントを設定します。  
  
3.  開く、**イミディ エイト**ウィンドウ (**デバッグ** > **Windows** > **イミディ エイト**) では、次を入力し、ウィンドウ: `?MyFunction<enter>`  
  
4.  ブレークポイントにヒットしたことと、呼び出し履歴が正確であることを確認します。  
  
5.  **デバッグ** メニューのをクリックして**続行**、まだデザイン モードであることを確認してください。  
  
6.  次のように入力、**イミディ エイト**ウィンドウ。 `?MyFunction<enter>`  
  
7.  次のように入力、**イミディ エイト**ウィンドウ。 `?MySub<enter>`  
  
8.  ブレークポイントにヒットし、静的変数の値を調べることを確認`i`で、**ローカル**ウィンドウです。 3 という値が表示されます。  
  
9. 呼び出し履歴が正確であることを確認します。  
  
10. **デバッグ** メニューのをクリックして**続行**、まだデザイン モードであることを確認してください。  

## <a name="debug-at-design-time-from-the-xaml-designer"></a>XAML デザイナーのデザイン時デバッグします。

一部の宣言型データ バインディング シナリオで XAML デザイナーからの背後にあるコードをデバッグことができます。

1. プロジェクトなどの追加、新しい XAML ページ*temp.xaml*です。 新しい XAML ページは空のままにします。 

1. ソリューションをコンパイルします。

1. 開いている*temp.xaml*、デザイナーが読み込まれます (*UwpSurface.exe* UWP アプリで、または*XDesProc.exe*) 後の手順に接続できるようにします。 

1. Visual Studio の新しいインスタンスを開きます。 新しいインスタンスで開く、**プロセスにアタッチする** ダイアログ ボックス (**デバッグ** > **プロセスにアタッチする**)、設定、**にアタッチ**などの正しいコードの種類にフィールド**マネージ コード (CoreCLR)**または .NET のバージョンに基づいて、正しいコードの種類。 一覧から正しいデザイナー プロセスを選択して、**アタッチ**です。

    UWP を対象とするプロジェクト ビルド 16299 またはデザイナー プロセスは、上記の*UwpSurface.exe*です。 デザイナーのプロセスは、WPF または UWP の 16299 より前のバージョンでは、 *XDesProc.exe*です。

1. プロセスにアタッチされている、間、プロジェクトに切り替えるをデバッグする分離コードを開き、ブレークポイントを設定します。

1. 最後に、データ バインディングを含む XAML コードを含むページを開きます。

    たとえばで TextBlock をデザイン時にバインドする次の XAML の型コンバーター コードにブレークポイントを設定可能性があります。

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   ページが読み込まれると、ブレークポイントにヒットします。
  
## <a name="see-also"></a>参照  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [デバッガーの基本事項](../debugger/debugger-basics.md)
