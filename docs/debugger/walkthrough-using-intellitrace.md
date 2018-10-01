---
title: IntelliTrace を使用したイベントの表示 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f46113365b66a75d3f9e149181637c79068645ab
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542326"
---
# <a name="view-events-with-intellitrace-in-visual-studio"></a>Visual Studio での IntelliTrace を使用したイベントの表示
IntelliTrace を使用して、特定のイベントまたはイベントのカテゴリに関する情報、またはイベントだけでなく、個々の関数呼び出しに関する情報を収集することができます。 この操作を実行する手順を次に示します。  
  
 Visual Studio Enterprise edition、Professional または Community edition いないで IntelliTrace を使用できます。  
  
##  <a name="GettingStarted"></a> Intellitrace を構成します。  
 IntelliTrace イベントのみでデバッグを実行することができます。 IntelliTrace イベントは、デバッガー イベント、例外、.NET Framework イベント、およびその他のシステム イベントです。 デバッグを開始する前に、IntelliTrace が記録するイベントを制御するために、特定のイベントをオンまたはオフにする必要があります。 詳細については、次を参照してください。 [IntelliTrace 機能](../debugger/intellitrace-features.md)します。  
  
 - ファイル アクセスで IntelliTrace イベントをオンにします。 移動して、**ツール > オプション > IntelliTrace > IntelliTrace イベント**ページ、および展開し、**ファイル**カテゴリ。 **[ファイル]** イベント カテゴリをチェックします。 これにより、すべてのファイル イベント (アクセス、閉じる、削除) がチェックされます。

## <a name="create-your-app"></a>アプリを作成します。
  
1.  C# コンソール アプリケーションを作成します。 Program.cs ファイルで、次の `using` ステートメントを追加します。  
  
    ```csharp  
    using System.IO;  
    ```  
  
2.  Main メソッドで <xref:System.IO.FileStream> を作成し、読み取り、閉じ、ファイルを削除します。 ブレークポイントを設定する場所を確保するだけの別の行を追加します。  
  
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
  
3.  `Console.WriteLine("done");`  

## <a name="start-debugging-and-view-intellitrace-events"></a>デバッグを開始し、IntelliTrace イベントを表示
  
1.  通常どおりデバッグを開始します。 (キーを押して**F5**  をクリックしてまたは**デバッグ > デバッグ開始**します。  
  
    > [!TIP]
    >  保持、**ローカル**と **[自動変数]** 表示およびこれらのウィンドウで、値を記録する、デバッグ中に windows が開きます。  
  
2.  ブレークポイントで実行が停止します。 表示されない場合、**診断ツール**ウィンドウで、をクリックして**デバッグ > Windows > IntelliTrace イベント**します。  
  
     **[診断ツール]** ウィンドウで、 **[イベント]** タブを見つけます ( **[イベント]**、 **[メモリ使用量]**、および **[CPU 使用率]** の 3 つのタブが表示されます)。 **[イベント]** タブは、デバッガーが実行を中断する直前のイベントで終わる、イベントの時系列の一覧を示しています。 **Access WordSearchInputs.txt**という名前のイベントが表示されます。  
  
     次のスクリーン ショットは Visual Studio 2015 Update 1 のものです。  
  
     ![IntelliTrace&#45;更新プログラム 1](../debugger/media/intellitrace-update1.png "IntelliTrace-更新プログラム 1")  
  
3.  イベント選択して詳細を展開します。  
  
     次のスクリーン ショットは Visual Studio 2015 Update 1 のものです。  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")  
  
     ファイルを開くには、パス名のリンクを選択します。 完全なパス名が使用できない場合、 **[ファイルを開く]** ダイアログ ボックスが表示されます。  
  
     クリックして**履歴デバッグの有効化**、デバッガーのコンテキストに設定が選択したイベント時刻が表示された履歴データを収集、**呼び出し履歴**、 **[ローカル]** および、その他の参加している windows のデバッガーです。 ソース コードが使用可能な場合、Visual Studio によってポインターがソース ウィンドウ内の対応するコードに移動されるため、そのコードを調査できます。  
  
     次のスクリーン ショットは Visual Studio 2015 Update 1 のものです。  
  
     ![HistoricalDebugging&#45;更新プログラム 1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-更新プログラム 1")  
  
4.  バグが見つからない場合は、バグが発生するまでの間に発生した他のイベントを確認します。 また、IntelliTrace で呼び出し情報を記録することで、関数呼び出しをステップ実行することもできます。 
  
## <a name="next-steps"></a>次の手順

デバッグ履歴では、いくつかの IntelliTrace の高度な機能を使用できます。

 - スナップショットを表示するを参照してください[IntelliTrace を使用して前のアプリ状態を調べる。](../debugger/view-historical-application-state.md)
 - 変数を検査して、コードを移動する方法については、次を参照してください[デバッグ履歴を使用してアプリを調べる。](../debugger/historical-debugging-inspect-app.md)