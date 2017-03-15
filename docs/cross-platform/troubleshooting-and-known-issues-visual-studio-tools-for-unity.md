---
title: "トラブルシューティングと既知の問題 (Visual Studio Tools for Unity) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# トラブルシューティングと既知の問題 (Visual Studio Tools for Unity)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このセクションには、Visual Studio Tools for Unity における一般的な問題の解決法、既知の問題についての説明、およびエラー報告によって Visual Studio Tools for Unity を改善する方法について記されています。  
  
## トラブルシューティング  
 Visual Studio Tools for Unity の一般的な問題を解決するには、以下のセクションを参照してください。  
  
### UnityVS から UnityVS to Visual Studio Tools for Unity への移行  
 UnityVS から Visual Studio Tools for Unity に移行している場合、Unity プロジェクト用の新しい Visual Studio ソリューションを生成する必要があります。  
  
##### Unity プロジェクトを UnityVS 1.8 から Visual Studio Tools for Unity 1.9 に移行する方法  
  
1.  古いソリューションとプロジェクト ファイルを Unity プロジェクトから削除します。 Unity プロジェクトのルート ディレクトリで、Visual Studio .sln と \*proj ファイルを見つけてすべて削除します。  
  
2.  Visual Studio Tools for Unity パッケージを Unity プロジェクトにインポートします。 VSTU パッケージをインポートする方法については、「[作業の開始](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md)」ページの「Visual Studio Tools for Unity の構成」をご覧ください。  
  
3.  新しいソリューションとプロジェクト ファイルを生成します。 今すぐに作成する場合は、Unity エディターのメイン メニューで、\[**Visual Studio Tools**\]、\[**Generate Project Files**\] を選択します。 あるいは、この手順をスキップすることもできます。その場合、\[**Visual Studio Tools**\]、\[**Open in Visual Studio**\] と選択すると新しいファイルが自動的に Visual Studio Tools for Unity によって作成されます。  
  
### Visual Studio が Visual Studio Tools for Unity によって作成されたソリューションを読み込まない  
 詳細については、[この stackoverflow の質問に対する回答](http://stackoverflow.com/a/24035907/36702)を参照してください。  
  
### Windows 8 の場合に Unity ターゲット フレームワークをダウンロードするよう Visual Studio から求められる  
 UnityVS には .NET Framework 3.5 が必要ですが、Windows 8 では既定でインストールされません。 この問題を解決するには、.NET Framework 3.5 のダウンロードとインストールに関する手順に従ってください。  
  
## 既知の問題  
 デバッガーが Unity の古いバージョンの C\# コンパイラとやり取りする方法に起因する、Visual Studio Tools for Unity の既知の問題があります。 これらの問題を修正するために作業中ですが、修正されるまでは以下の問題が発生する可能性があります。  
  
-   デバッグ時に Unity がクラッシュすることがあります。  
  
-   デバッグ時に Unity がフリーズすることがあります。  
  
-   メソッドのステップインとステップアウトが正しく動作しないことがあります。特に、反復子または switch ステートメント内でこれが生じる可能性があります。  
  
## エラーの報告  
 クラッシュ、フリーズ、またはその他のエラーが発生する場合、エラー レポートを送信することによって、Visual Studio Tools for Unity の品質向上にご協力ください。 Visual Studio Tools for Unity における問題の調査と解決に役立ちます。 ご協力に感謝いたします。  
  
### Visual Studio がフリーズする場合にエラーを報告する方法  
 Visual Studio Tools for Unity でデバッグすると Visual Studio がフリーズするという報告を受け取っていますが、問題を把握するためにさらにデータを必要としています。 次の手順を実行していただくと、調査に役立ちます。  
  
##### Visual Studio Tools for Unity でデバッグすると Visual Studio がフリーズすることを報告する方法  
  
1.  Visual Studio の新しいインスタンスを開きます。  
  
2.  \[プロセスにアタッチ\] ダイアログ ボックスを開きます。 Visual Studio の新しいインスタンスのメイン メニューで、\[**デバッグ**\]、\[**プロセスにアタッチ**\] を選択します。  
  
3.  Visual Studio のフリーズしたインスタンスに、デバッガーをアタッチします。 \[**プロセスにアタッチ**\] ダイアログ ボックスで、\[**選択可能なプロセス**\] テーブルからフリーズした Visual Studio インスタンスを選択し、\[**アタッチ**\] ボタンを選択します。  
  
4.  デバッガーを一時停止します。 Visual Studio の新しいインスタンスのメイン メニューで、\[**デバッグ**\]、\[**すべて中断**\] を選択するか、単に **Ctrl\+Alt\+Break** 押します。  
  
5.  スレッド ダンプを作成します。 コマンド ウィンドウで、次のコマンドを入力して **Enter** を押します。  
  
    ```powershell  
    Debug.ListCallStack /AllThreads /ShowExternalCode  
    ```  
  
     最初に \[**コマンド**\] ウィンドウを表示しなければならない場合もあります。 Visual Studio のメイン メニューで、\[**ビュー**\]、\[**その他のウィンドウ**\]、\[**コマンド ウィンドウ**\] の順に選択します。  
  
6.  最後に、Visual Studio がフリーズ状態になったときに実行していた作業内容に関する説明を添えて、スレッド ダンプを [vstusp@microsoft.com](mailto:vstusp@microsoft.com) に送信します。