---
title: デザイン時にデバッグ |Microsoft Docs
ms.custom: seodec18
ms.date: 11/21/2018
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
ms.openlocfilehash: d9c4b0996faf26279ff8018e0e072fd25a33d783
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063423"
---
# <a name="debug-at-design-time-in-visual-studio-c-c-visual-basic-f"></a>Visual Studio でデザイン時にデバッグ (C#、C++、Visual Basic、 F#)

アプリの中にではなく、デザイン時にコードをデバッグするには、実行されている、使用することができます、**イミディ エイト**ウィンドウ。 

使用することができます、データ バインドのコードなど、XAML デザイナーからのアプリの背後にある XAML コードをデバッグする**デバッグ** > **プロセスにアタッチ**します。
  
## <a name="use-the-immediate-window"></a>イミディ エイト ウィンドウを使用します。  

Visual Studio を使用する**イミディ エイト**ウィンドウで、アプリを実行することがなく、関数またはサブルーチンを実行します。 関数またはサブルーチンにブレークポイントが含まれる場合は、Visual Studio がブレークポイントで中断されます。 デバッガー ウィンドウを使用して、プログラムの状態を確認できます。 この機能は、*デザイン時のデバッグ*と呼ばれます。  

次の例は、Visual Basic では。 使用することも、**イミディ エイト**でデザイン時にウィンドウC#、 F#、および C++ アプリ。

1. 空の Visual Basic コンソール アプリケーションには、次のコードを貼り付けます。  
   
   ```vb  
   Module Module1
   
       Sub Main()
           MySub()
       End Sub
   
       Function MyFunction() As Decimal
           Static i As Integer
           i = i + 1
           Return i
       End Function
   
       Sub MySub()
           MyFunction()
   
       End Sub
   End Module
   ```  
   
1. 行にブレークポイントを設定**End Function**します。  
   
1. 開く、**イミディ エイト**ウィンドウを選択して**デバッグ** > **Windows** > **イミディ エイト**します。 型`?MyFunction`ウィンドウ、およびキーを押します**Enter**します。   
   
   ブレークポイントがヒットし、値の**MyFunction**で、**ローカル**ウィンドウが**1**します。 アプリが中断モード中には、呼び出し履歴や他のデバッグ ウィンドウを調べることができます。 
   
1. 選択**続行**Visual Studio のツールバー。 アプリが終了し、 **1**で返される、**イミディ エイト**ウィンドウ。 デザイン モードのままでいることを確認します。  
   
1. 型`?MyFunction`で、**イミディ エイト**ウィンドウをもう一度、およびキーを押して**Enter**。 ブレークポイントがヒットし、値の**MyFunction**で、**ローカル**ウィンドウが**2**します。 
   
1. 選択することがなく**続行**、型`?MySub()`で、**イミディ エイト**ウィンドウ、およびキーを押します **」と入力**します。 ブレークポイントがヒットし、値の**MyFunction**で、**ローカル**ウィンドウが**3**します。 アプリが中断モード中には、アプリの状態を確認できます。 
   
1. **[続行]** を選択します。 ブレークポイントがヒットをもう一度、しの値**MyFunction**で、**ローカル**ウィンドウが**2**します。 **イミディ エイト**ウィンドウに返されます**式が評価された、値はありません**します。
   
1. 選択**続行**もう一度です。 アプリが終了し、 **2**で返される、**イミディ エイト**ウィンドウ。 デザイン モードのままであることを確認します。
   
1. 内容を消去する、**イミディ エイト**ウィンドウを右クリックし、ウィンドウの**すべてクリア**します。 

## <a name="attach-to-an-app-from-the-xaml-designer"></a>XAML デザイナーからアプリにアタッチします。

いくつか宣言型データ バインディングのシナリオで XAML デザイナーでの背後にあるコードをデバッグすることができます。

1. Visual Studio プロジェクトで、追加など、新しい XAML ページでは、 *temp.xaml*します。 新しい XAML ページは空のままにします。 
   
1. ソリューションをビルドします。
   
1. 開いている*temp.xaml*、XAML デザイナーが読み込まれます*XDesProc.exe*、または*UwpSurface.exe* UWP アプリでします。 
   
1. Visual Studio の新しいインスタンスを開きます。 新しいインスタンスで次のように選択します。**デバッグ** > **プロセスにアタッチ**します。 
   
1. **プロセスにアタッチ** ダイアログ ボックスで、処理するデザイナー、select、**選択可能なプロセス**一覧。
   
   UWP 用 Windows を対象とするプロジェクトがビルド 16299 またはデザイナー プロセスは、上記*UwpSurface.exe*します。 デザイナーのプロセスは、16299 より前の WPF や UWP のバージョン、 *XDesProc.exe*します。
   
1. 確認、**にアタッチ**フィールドがなどの .NET のバージョンの正しいコードの種類に設定されて**マネージ コード (CoreCLR)** します。 
   
1. 選択**アタッチ**します。
   
1. プロセスにアタッチされている、間、他の Visual Studio インスタンスに切り替えるし、アプリの背後にあるコードをデバッグするブレークポイントを設定します。
   
   たとえば、次の XAML は、デザイン時に、TextBlock のバインドの型コンバーターのコードでブレークポイントを設定でした。
   
    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   ページが読み込まれると、ブレークポイントにヒットします。
  
## <a name="see-also"></a>関連項目  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [デバッガーの基本事項](../debugger/getting-started-with-the-debugger.md)
