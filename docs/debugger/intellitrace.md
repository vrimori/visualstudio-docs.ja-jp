---
title: "IntelliTrace |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace, collecting data from Test Manager
- IntelliTrace
- Test Manager, debugging with IntelliTrace
- IntelliTrace, debugging after a crash
ms.assetid: 486bfec2-39bd-4d78-892a-42352128ee52
caps.latest.revision: "135"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 789c2317fcb1bc46b5708f1810563b20fe8895ed
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="intellitrace"></a>[IntelliTrace]
IntelliTrace を使用して実行履歴を記録およびトレースすると、アプリのデバッグにかかる時間を短縮できます。 IntelliTrace には以下の機能があるので、バグを簡単に見つけることができます。  
  
-   特定のイベントを記録する  
  
     関連するコードに表示されるデータを調べて、**ローカル**デバッガー イベント、および関数呼び出し情報の中にウィンドウ  
  
-   再現が困難な場合、または配置で発生する場合のエラーをデバッグする  
  
 IntelliTrace は Visual Studio Enterprise Edition で使用できます (Professional Edition または Community Edition の場合は使用できません)。  
  
## <a name="what-do-you-want-to-do"></a>実行する操作  
  
|||  
|-|-|  
|**IntelliTrace を使用したアプリケーションをデバッグするには。**<br /><br /> -過去のイベント表示します。<br />-呼び出し過去のイベント情報を表示します。<br />IntelliTrace セッションを保存します。<br />IntelliTrace で収集するデータを制御します。|-   [チュートリアル: IntelliTrace の使用](../debugger/walkthrough-using-intellitrace.md)<br />- [IntelliTrace の機能](../debugger/intellitrace-features.md)<br />-   [デバッグ履歴](../debugger/historical-debugging.md)<br />-   [IntelliTrace 手順バックを利用したスナップショットの表示](../debugger/how-to-use-intellitrace-step-back.md)|  
|**Test Manager でのテスト セッション中に IntelliTrace データを収集します。**|-   [手動テストでの複数の診断データを収集します。](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)|  
|**展開済みのアプリケーションから IntelliTrace データを収集します。**|-   [IntelliTrace スタンドアロン コレクターを使用します。](../debugger/using-the-intellitrace-stand-alone-collector.md)|  
|**IntelliTrace ログ ファイル (.iTrace ファイル) からデバッグを開始します。**|-   [保存された IntelliTrace データを使用します。](../debugger/using-saved-intellitrace-data.md)|  
  
##  <a name="IntelliTraceSupport"></a>IntelliTrace でデバッグするどのようなアプリには  
  
|||  
|-|-|  
|**サポート状況**|、.NET Framework 2.0 または以降のバージョンを使用する Visual Basic および Visual c# のアプリケーションです。<br />     ASP.NET、Microsoft Azure、Windows フォーム、WCF、WPF、Windows Workflow、SharePoint 2010、SharePoint 2013、および 64 ビットのアプリを含むほとんどのアプリケーションをデバッグできます。<br />     IntelliTrace を使用した SharePoint アプリケーションをデバッグするを参照してください。[チュートリアル: IntelliTrace を使用した、SharePoint アプリケーションのデバッグ](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)です。<br />     IntelliTrace を使用した Microsoft Azure のアプリをデバッグするを参照してください。 [IntelliTrace および Visual Studio で発行されたクラウド サービスのデバッグ](/azure/vs-azure-tools-intellitrace-debug-published-cloud-services)です。|  
|**制限付きサポート**|.NET core とイベントについてのみサポートされている ASP.NET Core アプリケーション<br />の f# 試用前提アプリ<br />UWP アプリのイベントについてのみサポートされています。|  
|**サポートされていません**|C++、その他の言語、およびスクリプト<br />Windows サービス、Silverlight、Xbox、または[!INCLUDE[winmobile](../debugger/includes/winmobile_md.md)]アプリ|  
  
> [!NOTE]
>  既に実行されているプロセスをデバッグする場合は、IntelliTrace イベントのみ (呼び出し情報なし) を収集できます。 ローカル マシンのみの 32 ビットまたは 64 ビットのプロセスにアタッチすることができます。 プロセスにアタッチする前に発生するイベントが収集されません。
  
##  <a name="IntelliTraceVSTraditional"></a>IntelliTrace でデバッグなぜですか。  
 従来型または*live*のみ、アプリケーションの現在の状態、過去のイベントに関する限定されたデータとデバッグでは表示します。 アプリケーションの現在の状態に基づいてこれらのイベントを推測するか、またはアプリケーションを再実行することによってこれらのイベントを再作成する必要があります。  
  
 IntelliTrace は、これらの時点で特定のイベントやデータを記録することによってこの従来のデバッグを拡大します。 これにより、特にバグの箇所を通り越してステップ実行した場合に、再起動せずにこれらのアプリケーションで起こったことを確認できます。 IntelliTrace は従来のデバッグ中に既定で有効になっているため、自動的に非表示の状態でデータを収集します。 これにより、従来のデバッグと IntelliTrace デバッグを簡単に切り替えて、記録された情報を見ることができます。 参照してください[IntelliTrace 機能の](../debugger/intellitrace-features.md)と[IntelliTrace に収集するデータ。](#WhatData)  
  
 また、IntelliTrace は再現が困難なエラーや配置で発生するエラーのデバッグに役立ちます。 IntelliTrace データを収集し、IntelliTrace ログ ファイル (.iTrace ファイル) に保存できます。 .iTrace ファイルには、例外、パフォーマンス イベント、Web 要求、テスト データ、スレッド、モジュール、およびその他のシステム情報に関する詳細情報が含まれています。 Visual Studio Enterprise でこのファイルを開き、項目を選択し、IntelliTrace でデバッグを開始できます。 これにより、ファイル内の任意のイベントに移動して、その時点のアプリケーションに関する特定の詳細を表示できます。  
  
 次のソースからの IntelliTrace データを保存できます。  
  
-   Visual Studio 2017 Enterprise、Visual Studio 2015 Enterprise、または以前のバージョンの Visual Studio Ultimate の IntelliTrace セッション。  
  
-   Microsoft Test Manager のテスト セッション  
  
-   Microsoft Monitoring Agent を単独、または System Center 2012 と連携して使用する場合の、IIS でホストされている ASP.NET Web アプリ、または配置されて実行中の SharePoint 2010 アプリケーションと SharePoint 2013 アプリケーション。 参照してください[IntelliTrace スタンドアロン コレクターを使用して](../debugger/using-the-intellitrace-stand-alone-collector.md)と[Microsoft Monitoring Agent による監視](http://technet.microsoft.com/library/dn465153.aspx)です。  
  
 IntelliTrace を使用したデバッグがどのように役立つかの例を次に示します。  
  
-   アプリケーションのデータ ファイルが破損していますが、このイベントの発生場所を特定できません。  
  
     IntelliTrace がなければ、コード全体を確認して可能性のあるファイルのアクセスをすべて見つけ、それらのアクセスにブレークポイントを設定してから、アプリケーションを再実行して、問題の発生箇所を探さなければなりません。 IntelliTrace を使用すると、各イベントが発生したときに収集されたアプリケーションに関するファイル アクセス イベントや特定の詳細をすべて表示できます。  
  
-   例外が発生します。  
  
     IntelliTrace がなければ、例外に関するメッセージを取得するが、例外の原因となったイベントに関する情報を多くする必要はありません。 例外を引き起こした呼び出しのチェーンを表示するコール スタックを調べることができますが、それらの呼び出し中に発生したイベントのシーケンスを表示できません。 IntelliTrace を使用すると、例外の前に発生したイベントを確認できます。  
  
-   アプリケーションは、テスト コンピューターではクラッシュしますが、開発用コンピューターでは正常に実行されます。  
  
     Microsoft Test Manager から IntelliTrace データを収集して、.iTrace ファイルにデータを保存し、後日確認できるようにこのファイルを Team Foundation Server の作業項目に添付することができます。 参照してください[手動テストでの複数の診断データの収集](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests)と[保存された IntelliTrace データを使用して](../debugger/using-saved-intellitrace-data.md)です。  
  
-   展開されたアプリケーションでバグまたはクラッシュが発生しています。  
  
     Microsoft Azure ベースのアプリケーションの場合、アプリケーションを発行する前に IntelliTrace データの収集を構成できます。 アプリケーションの実行中、IntelliTrace はデータを .iTrace ファイルに保存します。 参照してください[IntelliTrace および Visual Studio で発行済みのクラウド サービスをデバッグ](http://go.microsoft.com/fwlink/?LinkID=262248)です。  
  
     IIS 7.0、7.5、および 8.0 でホストされる ASP.NET Web アプリ、および SharePoint 2010 アプリケーションや SharePoint 2013 アプリケーションの場合、Microsoft Monitoring Agent を単独で、または System Center 2012 と連携して使用して、IntelliTrace データを .iTrace ファイルに保存できます。  
  
     これは、配置されたアプリの問題を診断する場合に便利です。 参照してください[IntelliTrace スタンドアロン コレクターを使用して](../debugger/using-the-intellitrace-stand-alone-collector.md)です。  
  
##  <a name="WhatData"></a>IntelliTrace で収集するデータ  
 **イベント情報を収集します。**  
  
 既定では、IntelliTrace は、IntelliTrace イベント (デバッガー イベント、例外、.NET Framework イベント、およびデバッグに役立つその他のシステム イベント) のみを記録します。 常に収集されるデバッガー イベントと例外を除き、収集する IntelliTrace イベントの種類を選択できます。 参照してください[IntelliTrace 機能の](../debugger/intellitrace-features.md)します。  
  
-   **デバッガーのイベント**  
  
     IntelliTrace は、Visual Studio デバッガーに発生するイベントを常に記録します。 たとえば、アプリケーションの起動はデバッガー イベントです。 その他のデバッガー イベントは、アプリケーションの実行を中断する停止イベントです。 たとえば、プログラムに、ブレークポイントにヒット トレース ポイント、またはを実行、**ステップ**コマンド。  

     パフォーマンスに役立てるためには既定では、IntelliTrace がデバッガー イベントのすべての値を記録しません。 代わりに、次の値を記録します。  
  
    -   値が、**ローカル**ウィンドウです。 保持、**ローカル**これらの値を表示する開いているウィンドウ。  
  
    -   値が、 **[自動変数]**ウィンドウ場合にのみ、 **[自動変数]**ウィンドウが開いています。  
  
    -   値を表示するためにソース ウィンドウの変数の上にマウス ポインターを移動すると表示されるデータヒントの値。 IntelliTrace は、固定されたデータヒントの値は収集しません。  

    IntelliTrace が各デバッガーでアプリケーションのプロセスのスナップショットを取っては IntelliTrace イベントとスナップショット モードを有効にすると、**ブレークポイント**と**ステップ**イベント。 これには、内の値を記録、**ローカル**、 **[自動変数]**、および**ウォッチ**かどうか、ウィンドウが開いているかに関係なく、windows です。 固定されたデータヒントの値は収集されます。 
  
-   **例外**  
  
     IntelliTrace は、次のような種類の例外の種類とメッセージを記録します。  
  
    -   例外がスローおよびキャッチされた場合の処理済みの例外  
  
    -   ハンドルされない例外  
  
-   **.NET framework イベント**  
  
     既定では、IntelliTrace は最も一般的な .NET Framework のイベントを記録します。 例:  
  
    -   チェック ボックスの確認イベントの場合、IntelliTrace はチェック ボックスの状態とテキストを収集します。  
  
-   **SharePoint 2010 および SharePoint 2013 のアプリケーション イベント**  
  
     Visual Studio の外部で実行されている SharePoint 2010 アプリケーションと SharePoint 2013 アプリケーションのユーザー プロファイル イベントと Unified Logging System (ULS) イベントのサブセットを記録できます。 これらのイベントを .iTrace ファイルに保存できます。 Visual Studio Enterprise 2017、Visual Studio Enterprise 2015、以前のバージョンの Visual Studio Ultimate が必要ですか[Microsoft Monitoring Agent](http://go.microsoft.com/fwlink/?LinkId=320384)で実行されている**トレース**モード。  
  
     .iTrace ファイルを開いたら、SharePoint 相関 ID を入力して対応する Web 要求を見つけ、記録されたイベントを表示し、特定のイベントからのデバッグを開始します。 ファイルにハンドルされない例外が含まれている場合は、相関 ID を選択して例外のデバッグを開始できます。  
  
     参照トピック  
  
    -   [IntelliTrace スタンドアロン コレクターを使用する](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
    -   [保存された IntelliTrace データを使用する](../debugger/using-saved-intellitrace-data.md)  
  
    -   [チュートリアル: IntelliTrace を使用した SharePoint アプリケーションのデバッグ](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)  
 
 **スナップショットをキャプチャします。**
 
 すべてのブレークポイントでスナップショットをキャプチャし、デバッガーのステップのイベントの IntelliTrace を構成することができます。 IntelliTrace は、各スナップショットは、により複合型の変数を表示して、式の評価で完全なアプリケーションの状態を記録します。

 参照してください[IntelliTrace ステップ ライトバックを使用してスナップショットを表示する](../debugger/how-to-use-intellitrace-step-back.md)です。

 **関数呼び出し情報を収集します。**  
  
 関数の呼び出し情報を収集するように IntelliTrace を構成することができます。 この情報は、呼び出し履歴を表示したり、コードの呼び出しで前後に移動できます。 各関数呼び出しについて、IntelliTrace は次のデータを記録します。  
  
-   関数名  
  
-   関数のエントリ ポイントでパラメーターとして渡され、関数の終了ポイントで返されるプリミティブ データ型の値  
  
-   読み取りまたは変更されたときの自動プロパティの値  
  
-   null かどうかの場合以外の値を除く、1 番目のレベルの子オブジェクトへのポインター  
  
> [!NOTE]
>  IntelliTrace は、配列の最初の 256 個のオブジェクトと文字列の最初の 256 文字のみを収集します。  
  
 参照してください[デバッグ履歴でアプリを検査](../debugger/historical-debugging-inspect-app.md)です。
  
 **モジュール情報を収集します。**  
  
 IntelliTrace で収集される呼び出し情報の量を制御するには、目的のモジュールのみを指定します。 これにより、収集時のアプリケーションのパフォーマンスを向上させることができます。 セクションを参照して[IntelliTrace が収集される情報量を制御](../debugger/intellitrace-features.md#ControlCallData)で IntelliTrace の機能です。  
  
##  <a name="AffectPerformance"></a>IntelliTrace のアプリケーションの速度が遅いですか?  
 既定では、選択された IntelliTrace イベントについてのみ情報が収集されます。 これが原因でアプリケーションの速度が低下するかどうかは、コードの構造と構成によって決まります。 たとえば、IntelliTrace がイベントを頻繁に記録する場合、アプリケーションの速度が低下する可能性があります。 また、アプリケーションのリファクタリングを検討する必要に迫られる場合があります。  
  
 呼び出し情報を収集すると、アプリケーションの速度が大幅に低下する可能性があります。 さらに、ディスクに保存される IntelliTrace ログ ファイル (.iTrace ファイル) のサイズが増加する可能性があります。 これらの影響を最小限に抑えるには、必要なモジュールのみから呼び出し情報を収集するようにします。  .ITrace ファイルの最大サイズを変更するには**ツール**、**オプション**、 **IntelliTrace**、**詳細**です。 
  
## <a name="in-this-section"></a>このセクションの内容  
 [IntelliTrace の機能](../debugger/intellitrace-features.md)  
  
 [配置後の問題の診断](../debugger/diagnose-problems-after-deployment.md)  
  
 [保存された IntelliTrace データを使用する](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="blogs"></a>ブログ  
 [Visual Studio ALM および Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)  
  
### <a name="forums"></a>フォーラム  
 [Visual Studio の診断](http://go.microsoft.com/fwlink/?LinkId=262263)