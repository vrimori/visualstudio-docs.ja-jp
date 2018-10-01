---
title: 'チュートリアル: IntelliTrace の使用 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8cac83c1e036bb16eef60e9a93416d7096d3135b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536196"
---
# <a name="walkthrough-using-intellitrace"></a>チュートリアル: IntelliTrace の使用
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[チュートリアル: IntelliTrace を使用した](https://docs.microsoft.com/visualstudio/debugger/walkthrough-using-intellitrace)します。  
  
IntelliTrace を使用して、特定のイベントまたはイベントのカテゴリに関する情報、またはイベントだけでなく、個々の関数呼び出しに関する情報を収集することができます。 この操作を実行する手順を次に示します。  
  
 IntelliTrace は Visual Studio Enterprise Edition で使用できます (Professional Edition または Community Edition の場合は使用できません)。  
  
##  <a name="GettingStarted"></a> イベントのみで IntelliTrace を使用します。  
 IntelliTrace イベントのみでデバッグを実行することができます。 IntelliTrace イベントは、デバッガー イベント、例外、.NET Framework イベント、およびその他のシステム イベントです。 デバッグを開始する前に、IntelliTrace が記録するイベントを制御するために、特定のイベントをオンまたはオフにする必要があります。 詳細については、次を参照してください。 [IntelliTrace 機能](../debugger/intellitrace-features.md)します。  
  
 IntelliTrace イベントのみでデバッグする方法を次の手順に示します。  
  
1.  ファイル アクセスで IntelliTrace イベントをオンにします。 **[ツール] / [オプション] / [IntelliTrace] / [IntelliTrace イベント]** ページに移動して、 **[ファイル]** カテゴリを展開します。 **[ファイル]** イベント カテゴリをチェックします。 これにより、すべてのファイル イベント (アクセス、閉じる、削除) がチェックされます。  
  
2.  C# コンソール アプリケーションを作成します。 Program.cs ファイルで、次の `using` ステートメントを追加します。  
  
    ```csharp  
    using System.IO;  
    ```  
  
3.  Main メソッドで <xref:System.IO.FileStream> を作成し、読み取り、閉じ、ファイルを削除します。 ブレークポイントを設定する場所を確保するだけの別の行を追加します。  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        FileStream fs = File.Create("WordSearchInputs.txt");  
        fs.ReadByte();  
        fs.Close();  
        File.Delete("WordSearchInputs.txt");  
  
        Console.WriteLine("done");  
    }  
    ```  
  
4.  `Console.WriteLine("done");`  
  
5.  通常どおりデバッグを開始します。 ( **F5** キーを押すか、 **[デバッグ] / [デバッグの開始]** をクリックします。  
  
    > [!TIP]
    >  これらのウィンドウに値を表示および記録するために、デバッグ中は **[ローカル]** ウィンドウおよび **[自動変数]** ウィンドウを開いたままにします。  
  
6.  ブレークポイントで実行が停止します。 **[診断ツール]** ウィンドウが表示されない場合は、 **[デバッグ] / [Windows] / [IntelliTrace イベント]** の順にクリックします。  
  
     **[診断ツール]** ウィンドウで、 **[イベント]** タブを見つけます ( **[イベント]**、 **[メモリ使用量]**、および **[CPU 使用率]** の 3 つのタブが表示されます)。 **[イベント]** タブは、デバッガーが実行を中断する直前のイベントで終わる、イベントの時系列の一覧を示しています。 **Access WordSearchInputs.txt**という名前のイベントが表示されます。  
  
     次のスクリーン ショットは Visual Studio 2015 Update 1 のものです。  
  
     ![IntelliTrace&#45;更新プログラム 1](../debugger/media/intellitrace-update1.png "IntelliTrace-更新プログラム 1")  
  
7.  イベント選択して詳細を展開します。  
  
     次のスクリーン ショットは Visual Studio 2015 Update 1 のものです。  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")  
  
     ファイルを開くには、パス名のリンクを選択します。 完全なパス名が使用できない場合、 **[ファイルを開く]** ダイアログ ボックスが表示されます。  
  
     **[デバッグの履歴の有効化]** をクリックします。ここで、デバッガーのコンテキストを、 **[呼び出し履歴]**、 **[ローカル]** 、およびその他の参加しているデバッガーのウィンドウに履歴データを表示しながら、選択したイベントが収集された時刻に設定します。 ソース コードが使用可能な場合、Visual Studio によってポインターがソース ウィンドウ内の対応するコードに移動されるため、そのコードを調査できます。  
  
     次のスクリーン ショットは Visual Studio 2015 Update 1 のものです。  
  
     ![HistoricalDebugging&#45;更新プログラム 1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-更新プログラム 1")  
  
8.  バグが見つからない場合は、バグが発生するまでの間に発生した他のイベントを確認します。 また、IntelliTrace で呼び出し情報を記録することで、関数呼び出しをステップ実行することもできます。  
  
## <a name="using-intellitrace-with-events-and-function-calls"></a>イベントと関数の呼び出しでの IntelliTrace の使用  
 IntelliTrace は、イベントと共に関数呼び出しを記録できます。 これにより、呼び出し履歴が表示され、コード内で呼び出しの前後を移動できるようになります。 IntelliTrace は、関数名、関数の開始ポイントと終了ポイント、および特定のパラメーター値と戻り値などのデータを記録します。 参照してください[IntelliTrace 機能](../debugger/intellitrace-features.md)します。  
  
1.  呼び出しコレクションをオンにします。 ( **[ツール] / [オプション] / [IntelliTrace] / [全般]** で、 **[IntelliTrace イベントと呼び出し情報]** を選択します。 IntelliTrace は、次回のデバッグ セッションの開始時にこの情報の収集を開始します。  
  
    > [!TIP]
    >  これにより、アプリケーションの実行速度が低下するだけでなく、ディスクに保存中の IntelliTrace ログ ファイル (.iTrace ファイル) のサイズが増大する場合があります。 影響を最小限に抑えながら大半の呼び出しデータを取得するには、関心のあるモジュールからのデータだけを記録します。 .iTrace ファイルの最大サイズを変更するには、 **[ツール] / [オプション] / [IntelliTrace] / [詳細設定]** の順に移動し、ディスクの最大空き容量を指定します。 既定値は 250 MB です。  
  
2.  前のセクションで作成された C# コンソール アプリケーションのデバッグを開始します。 ブレークポイントで実行が停止します。 **[診断ツール]** ウィンドウが表示されない場合は、 **[デバッグ] / [Windows] / [IntelliTrace イベント]** の順にクリックします。  
  
3.  **[呼び出し]** タブに切り替えます。  
  
     ルート呼び出しを先頭にして (現状では Main の開始ポイント)、および実行が中断した場所を最後として、アプリケーションの関数の呼び出しが表示されるようになりました。  
  
     関数呼び出しのいずれかを選択してダブルクリックします。 関数の開始ポイントと終了ポイントだけでなく、現在の呼び出しが他の関数に対して実行した呼び出し、および呼び出しによって発生する IntelliTrace イベントが表示されます。 デバッグ履歴が有効になっていない場合、このアクションでデバッグ履歴を有効にします。 デバッグ履歴の詳細については、「 [Historical Debugging](../debugger/historical-debugging.md)」を参照してください。  
  
    > [!NOTE]
    >  いくつかの呼び出しは淡色表示されていることが分かります。 これは、IntelliTrace が対応するモジュールのデータを記録しなかったためです。 このデータを表示するには、IntelliTrace がそのモジュールからデータを収集するようにします。 モジュールの指定方法の詳細については、次を参照してください。 [IntelliTrace 機能](../debugger/intellitrace-features.md)します。  
  
## <a name="next-steps"></a>次の手順






