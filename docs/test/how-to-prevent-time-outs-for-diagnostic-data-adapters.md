---
title: Visual Studio の診断データ アダプターのタイムアウト
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, increasing time-outs
ms.assetid: 39fff4fc-9233-4f67-96ac-e81bbaf7ca82
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 093b937f7a957ef1d3a912c31d57a03f1a433ab0
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844239"
---
# <a name="how-to-prevent-time-outs-for-diagnostic-data-adapters"></a>方法: 診断データ アダプターがタイムアウトしないようにする

テストの設定で診断データ アダプターを使用する場合、次のいずれかの理由で、テストの実行を開始したときにタイムアウトが発生する場合があります。

-   テスト コントローラー コンピューターでテスト コントローラー サービスが実行されていない。 サービスの再起動が必要な場合もあります。 テスト コントローラーを決定および管理する方法の詳細については、「[Visual Studio でのテスト コントローラーおよびテスト エージェントの管理](../test/manage-test-controllers-and-test-agents.md)」を参照してください。

-   リモート コンピューターのデータを収集する場合、ファイアウォールによって Microsoft Test Manager がブロックされる可能性がある。 Microsoft Test Manager を実行するコンピューターは、テスト コントローラーからの受信接続を受け入れる必要があります。 Microsoft Test Manager がファイアウォールのブロックのためにコントローラーからのメッセージを受信できない場合、タイムアウトが発生します。 Microsoft Test Manager を実行するコンピューター上のファイアウォール設定を確認する必要があります。 ファイアウォール設定の詳細については、[Microsoft Web サイト](http://go.microsoft.com/fwlink/?LinkId=184980)を参照してください。

-   テスト コントローラーが Microsoft Test Manager を実行するコンピューターの名前を解決できない。 これは、DNS によって指定されたこのコンピューターのアドレスが誤っている場合に発生します。 この問題を解決するには、ネットワーク管理者に問い合わせることが必要な場合があります。

 大量のデータを収集する必要がある長いテストを実行する場合、データの収集がタイムアウトすることがあります。この問題を解決するには、次の手順を実行します。

 Microsoft Test Manager の構成ファイルまたはタイムアウトするテスト エージェントの構成ファイルを更新することで、タイムアウトの設定値を増やすことができます。

 Microsoft Test Manager では、構成ファイルは **mtm.exe.config** と呼ばれます。この構成ファイルは、*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE* ディレクトリにあります。

 テスト エージェントを更新するには、テスト エージェント コンピューター上で次の構成ファイルを更新する必要があります。 これらのファイルは、テスト エージェント コンピューターの同じ *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE* ディレクトリに格納されています。

-   QTAgent.exe.config

-   QTAgent32.exe.config

-   QTDCAgent.exe.config

-   QTDCAgent32.exe.config

 手動テストを実行して環境からデータを収集する場合、バグが発生するかテスト ケースが完了すると、診断データ アダプターによって収集されたすべてのデータは、手動テストを実行しているコンピューターに転送されます。 大量のデータを収集したか、ネットワーク接続速度が遅い場合、転送時間は既定値の 60 秒より長くなる場合があります。 たとえば、多数のプロセスの IntelliTrace イベントと呼び出し情報を収集するように IntelliTrace アダプターを構成した場合、このデータの転送時間は既定のタイムアウトを超過する可能性があります。この値を増やすには、次の手順に従って **mtm.exe.config** を更新します。

 テスト ランナーの動作がタイムアウトした場合やテスト エージェントがタイムアウトした場合、エラー メッセージが表示されます。テスト エージェントのエラー メッセージには、どのテスト エージェント コンピューターがタイムアウトしたかに関する情報が含まれます。出力されたエラー メッセージに応じて、次の手順を使用して構成ファイルを更新します。

## <a name="to-increase-the-time-outs-for-your-diagnostic-data-adapters"></a>診断データ アダプターのタイムアウトの設定値を増やすには

1.  エクスプローラー (ファイル エクスプローラー) のウィンドウを開きます。

     そのためには、**[スタート]** を右クリックし、**[エクスプローラー]** をポイントします。

    > [!NOTE]
    > ファイルを更新するには、管理特権が必要です。

2.  コンピューター上で、更新する必要のあるファイルが格納されている *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE* ディレクトリに移動します。

3.  ファイルを右クリックし、**[プログラムから開く]** をポイントします。 エディターを選択します。

     エディターにファイルが表示されます。 このファイルには、さまざまな設定が格納されています。 これらの設定のほとんどは、Microsoft Test Manager を使用して変更できます。 ただし、タイムアウトの設定値は、次の手順に従って手動で変更する必要があります。

4.  タイムアウト値を増やすには、テスト実行設定セクションを変更する必要があります。 このセクションは、次の形式になっています。

    ```text
    <!-- Begin: Test execution settings -->

        <!-- How long test runner will wait for an event raised to all local data collectors to complete.  Default is 300. -->
        <add key="DataCollectorEventTimeoutInSeconds" value="300"/>

        <!-- How long test runner will wait for test run operations, such as starting or stopping a test run, to complete.  Default is 60. -->
        <add key="RunOperationTimeoutInSeconds" value="60"/>

        <!-- End: Test execution settings -->
    ```

5.  診断データ アダプターがイベントの完了を待機する時間を増やすには、**DataCollectorEventTimeoutInSeconds** キーの値を増やします。

6.  テスト ランナーの動作に関してタイムアウト エラー メッセージが出力された場合は、**RunOperationTimeoutInSeconds** キーの値を増やす必要があります。

7.  バグが発生したかテストが終了したときに収集されたデータを、テストを実行しているコンピューターに転送する場合のタイムアウト値を増やすには、**mtm.exe.config** ファイルの appSettings セクションに次のタイムアウト値を追加する必要があります。

    ```text
    <!-- How long test runner waits for data collected by diagnostic data adapters to be transferred to the computer. Default is 60 seconds. -->
    <add key="GetCollectorDataTimeout" value="300"/>
    ```

    > [!NOTE]
    > タイムアウト値の単位は秒です。

8.  ファイルに加えた変更を保存した後、前回タイムアウトしたテストを再実行します。

## <a name="see-also"></a>関連項目

- [テスト設定を使用して診断情報を収集する](../test/collect-diagnostic-information-using-test-settings.md)