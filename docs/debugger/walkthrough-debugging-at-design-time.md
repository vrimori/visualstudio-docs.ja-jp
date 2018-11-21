---
title: デザイン時に Visual Studio でのデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 452b4045357db12c4b4cff1a5b6e27035cf85d82
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257200"
---
# <a name="debug-at-design-time-in-visual-studio-c-c-visual-basic-f"></a>Visual Studio でデザイン時にデバッグ (C#、C++、Visual Basic、 F#)

一部のシナリオでデザイン時のコードをデバッグすることがあります、アプリケーションの実行中の代わりに時刻します。 これを行うを使用して、**イミディ エイト**ウィンドウ。 データ バインド コードなどの他のコードと対話する XAML コードをデバッグする場合は、使用**デバッグ** > **プロセスにアタッチ**そのためにします。
  
### <a name="debug-at-design-time-using-the-immediate-window"></a>イミディ エイト ウィンドウを使用して、デザイン時にデバッグします。  

Visual Studio を使用する**イミディ エイト**ウィンドウで、アプリケーションが実行されていないときに、関数またはサブルーチンを実行します。 関数またはサブルーチンにブレークポイントが含まれているとき、適切なポイントで実行を中断します。 デバッガー ウィンドウを使用して、プログラムの状態を確認できます。 この機能は、デザイン時のデバッグと呼ばれます。  

次の例は、Visual Basic では。 使用、**イミディ エイト**デザイン時にウィンドウでもサポートC#、C++、およびF#アプリケーション。
  
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
  
5.  **デバッグ** メニューのをクリックして**続行**、まだデザイン モードであることを確認します。  
  
6.  次の入力、**イミディ エイト**ウィンドウ。 `?MyFunction<enter>`  
  
7.  次の入力、**イミディ エイト**ウィンドウ。 `?MySub<enter>`  
  
8.  ブレークポイントにヒットし、静的変数の値を確認することを確認`i`で、**ローカル**ウィンドウ。 3 という値が表示されます。  
  
9. 呼び出し履歴が正確であることを確認します。  
  
10. **デバッグ** メニューのをクリックして**続行**、まだデザイン モードであることを確認します。  

## <a name="debug-at-design-time-from-the-xaml-designer"></a>XAML デザイナーのデザイン時にデバッグします。

一部の宣言型データ バインディング シナリオでの XAML デザイナーからの背後にあるコードをデバッグすることができます。

1. プロジェクトで、追加など、新しい XAML ページでは、 *temp.xaml*します。 新しい XAML ページは空のままにします。 

1. ソリューションをコンパイルします。

1. 開いている*temp.xaml*、デザイナーが読み込まれます (*UwpSurface.exe*で UWP アプリの場合または*XDesProc.exe*) 後の手順に接続できるようにします。 

1. Visual Studio の新しいインスタンスを開きます。 新しいインスタンスで開く、**プロセスにアタッチ** ダイアログ ボックス (**デバッグ** > **プロセスにアタッチ**)、設定、**にアタッチ**などの正しいコードの種類にフィールド**マネージ コード (CoreCLR)** または .NET のバージョンに基づいて、適切なコードの種類。 一覧から正しいデザイナー プロセスを選択して、**アタッチ**します。

    UWP を対象とするプロジェクトがビルド 16299 またはデザイナー プロセスは、上記*UwpSurface.exe*します。 デザイナーのプロセスは、WPF や UWP の 16299 より前のバージョンでは、 *XDesProc.exe*します。

1. プロセスにアタッチされている、間をプロジェクトに切り替えるをデバッグする分離コードを開いてブレークポイントを設定します。

1. 最後に、データ バインディングを含む XAML コードを含むページを開きます。

    たとえば、次の XAML は、デザイン時に、TextBlock のバインドの型コンバーターのコードでブレークポイントを設定でした。

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   ページが読み込まれると、ブレークポイントにヒットします。
  
## <a name="see-also"></a>関連項目  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [デバッガーの基本事項](../debugger/getting-started-with-the-debugger.md)
