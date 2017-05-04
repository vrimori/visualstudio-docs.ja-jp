---
title: "Office Project のデバッグ | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Excel プロジェクト [Visual Studio での Office 開発]、デバッグ"
  - "Word プロジェクト [Visual Studio での Office 開発]、デバッグ"
  - "Outlook [Visual Studio での Office 開発]、デバッグ"
  - "デバッグ [Visual Studio での Office 開発]、Outlook プロジェクト"
  - "Office プロジェクト [Visual Studio での Office 開発]、デバッグ"
  - "Outlook [Visual Studio での Office 開発]、プロジェクト"
ms.assetid: e360b9e9-9f36-48f0-a0c5-a6980fb47a87
caps.latest.revision: 52
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Office Project のデバッグ
  Office プロジェクトのデバッグは、他の [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] プロジェクトに使用するのと同じ Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tools を使用して実行できます。 Office プロジェクトのデバッグ時には、ブレークポイントの挿入や **\[ローカル\]** ウィンドウでの変数の表示など、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デバッガーの機能も使用できます。[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のデバッグ ツールの詳細については、「[Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)」を参照してください。  
  
> [!TIP]  
>  デバッグを簡略化するには、ビルドしてデバッグする前に、Office アプリケーションで開いているすべてのインスタンスを閉じます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## デバッガーの起動と停止  
 Office プロジェクトのデバッグの開始方法は、他の [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] プロジェクトのデバッグの開始方法と同じです \(F5 キーを押すなど\)。 VSTO アドイン プロジェクトのデバッグを開始すると、対象となる Office アプリケーションの新しいプロセスが開始され、VSTO アドインが読み込まれます。  
  
 ドキュメント レベルのプロジェクトのデバッグを開始すると、ドキュメントまたはブックは新しい Word または Excel プロセスで開かれます。  
  
 デバッガーを停止すると、アプリケーション プロセスが即座に停止されます。また、デバッガーをデタッチするように設定してある場合にはデバッガーがデタッチされます。 停止する Office アプリケーション プロセスで開かれている他のすべてのドキュメントも警告を表示せずに閉じ、未保存の変更は失われます。 これには、デバッガーの実行中に開かれた文書やブックもすべて含まれます。  
  
 一般に、通常の方法で Office アプリケーションを終了できるように、デバッガーを停止する前にプロセスからデタッチしておくことをお勧めします。 デバッガーを停止した後も開いているドキュメントやワークシートを操作する場合は、プロセスからデタッチすることもできます。  
  
 Word のドキュメント レベルのカスタマイズ時に、デバッガーを何度も停止したり Word を突然終了したりすると、Normal テンプレートが破損する場合があります。 その場合は壊れた Normal テンプレートを削除します。テンプレートは、Word を次に開いたときに自動的に再作成されます。 ただし、Normal テンプレートに格納されていたマクロは再作成されません。  
  
### Office 2013 または Office 2016 のいずれかを使用して Office 2013 VSTO アドインをデバッグする  
 Visual Studio 2015 を使用しており、Office の両方のバージョンが並列でインストールされている場合、Visual Studio は Office 2016 を起動します。 Visual Studio 2013 を使用している場合、Visual Studio は Office 2013 を起動します。  
  
 別のバージョン \(2013 または 2016\) の Office を使用して VSTO アドインをデバッグする場合は、**\[プロジェクト デザイナー\]** を開き、**\[デバッグ\]** タブで **\[外部プログラムの開始\]** オプション ボタンをクリックします。 次に、適切な Office アプリケーションの実行可能ファイルの場所を参照します。  
  
## F10 および F11 キーの動作  
 Office プロジェクトのデバッグ開始における F10 および F11 キーの動作は、他の Visual Basic または C\# プロジェクトのデバッグ開始の場合と同じではありません。 Visual Basic や C\# のプロジェクトの場合、デバッガーはメイン関数で停止しますが、Office プロジェクトの場合、Visual Studio では Office アプリケーションのメイン関数に対する制御権がありません。 ただし、デバッグ実行中の F10 および F11 キーの機能は、Visual Basic および C\# のプロジェクトの場合と同じです。  
  
## 例外の表示  
 Visual Studio では、マネージ コードによるアンマネージ コードの操作方法が原因で、Microsoft Office アプリケーションからスローされたエラーは表示されません。 たとえば、Visual Studio の Office 開発ツールで作成された VSTO アドインが例外をスローした場合、Microsoft Office アプリケーションはエラーを表示せずに動作を継続します。 これらのエラーを表示するには、デバッガーが共通言語ランタイムの例外で中断されるように設定します。 詳細については、「[方法 : 例外がスローされたときに中断する](../Topic/How%20to:%20Break%20When%20an%20Exception%20is%20Thrown.md)」を参照してください。  
  
 共通言語ランタイム例外で中断するようにデバッガーを設定した場合、処理済みの例外や、プロジェクトに関係しない可能性もあるランタイム自体からのいくつかの初回例外も含め、すべての例外でデバッガーが中断されるようになります。 どのプロジェクトでも、不明な msosec を参照するエラーが表示されますが、これは無視してもかまいません。 このような msosec 例外はソリューションに影響しません。  
  
 メソッドの周囲で **Try...Catch** ステートメントを使用して、例外をキャッチすることもできます。  
  
 既定では、Visual Studio で Office プロジェクトの Just\-In\-Time デバッグ エラーも表示されませんが、発生したエラーを表示できるように、この機能を有効にすることができます。 詳細については、「[Just-In-Time Debugging in Visual Studio &#40;Visual Studio での Just-In-Time デバッグ&#41;](../debugger/just-in-time-debugging-in-visual-studio.md)」を参照してください。  
  
## コマンド ライン引数  
 **\[デバッグ\]** プロパティ ページの **\[開始動作\]** が **\[スタート プロジェクト\]** に設定されている場合、Visual Studio ではプロジェクトのデバッグ時にコマンド ライン引数を使用しません。起動オプションでコマンド ライン引数を指定した場合でも同様です。 デバッグの開始時にコマンド ライン引数を使用するには、**\[開始動作\]** を **\[スタート プロジェクト\]** 以外に設定する必要があります。  
  
## ソース管理  
 デバッグ プロパティは、ソース管理で複数のユーザー間では共有されません。 Visual Basic プロジェクトや Visual C\# プロジェクトでは、デバッグ プロパティはユーザー固有のファイル \(*ProjectName*.vbproj.user または *ProjectName*.csproj.user\) に格納されます。このファイルはソース管理されません。 複数のユーザーがデバッグを実行する場合は、各自が手動でデバッグ プロパティを入力する必要があります。  
  
## ドキュメント レベルのプロジェクトのキャッシュされたデータセットのデバッグ  
 プロジェクトをビルドするたびに、データセットは空になり、再作成されます。 キャッシュされたデータセットをデバッグする場合は、Visual Studio の外部で文書を開いてからデバッガーをアタッチする必要があります。  
  
## Word 97 ～ Word 2003 の文書 \(\*.doc\) 形式に基づく Word 文書プロジェクトのデバッグ  
 Word 97 ～ Word 2003 の文書 \(\*.doc\) 形式に基づく Word 文書プロジェクトをデバッグするには、信頼できるフォルダー一覧にプロジェクト フォルダーを追加する必要があります。 この手順の詳細については、「[ドキュメントへの信頼の付与](../vsto/granting-trust-to-documents.md)」を参照してください。  
  
## 無効化されたアドインのデバッグ  
 Microsoft Office アプリケーションにより、予期しない動作をする VSTO アドインが無効にされる場合があります。 Microsoft Office アプリケーションは、起動するたびに問題のあるコードが読み込まれないようにするため、VSTO アドインを無効にします。 しかし、通常のデバッグ時に、予期しない動作が発生することはよくあります。 VSTO アドインを再び有効にする方法の詳細については、「[方法: 無効にされた VSTO アドインを再度有効にする](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)」を参照してください。  
  
 Microsoft Office アプリケーションで VSTO アドインに適用される無効化には、ハードな無効化とソフトな無効化の 2 種類があります。  
  
### ハードな無効化  
 ハード的な無効化は、VSTO アドインによってアプリケーションが予期せずに終了した場合に発生する可能性があります。 また、開発用コンピューターで VSTO アドインの <xref:Microsoft.Office.Tools.AddIn.Startup> イベント ハンドラーの実行中にデバッガーを停止した場合にも発生することがあります。 VSTO アドインがハードに無効化されると、そのアドインがアプリケーションの **\[使用できないアイテム\]** ボックスの一覧に表示されます。  
  
 Office アプリケーションが Visual Studio の Office 開発ツールで作成された VSTO アドインをハードに無効化する場合、このアプリケーションは、エラーの原因となった VSTO アドインのみを無効化します。 Visual Studio の Office 開発ツールを使用してその Office アプリケーション用に作成されたその他の VSTO アドインの読み込みは続行されます。  
  
### ソフトな無効化  
 ソフトな無効化は、VSTO アドインによってエラーが発生したが、アプリケーションが予期せずに終了するということがなかったという場合に発生する可能性があります。 たとえば、<xref:Microsoft.Office.Tools.AddIn.Startup> イベント ハンドラーの実行中に VSTO アドインによってハンドルされない例外がスローされた場合に、アプリケーションによってそのアドインがソフトに無効化されることがあります。 VSTO アドインがソフトに無効化されると、そのアドインがアプリケーションの **\[アクティブでないアプリケーション アドイン\]** ボックスの一覧に表示され、アンロードされていないことを示すために、その VSTO アドインの **LoadBehavior** レジストリ エントリの値が変更されます。**LoadBehavior** レジストリ エントリの詳細については、「[VSTO アドインのレジストリ エントリ](../vsto/registry-entries-for-vsto-add-ins.md)」を参照してください。  
  
## イベント ビューアーを使用したインストールのエラーのトラブルシューティング  
 Office ソリューションのインストール時またはアンインストール時にスローされたすべての例外のメッセージは、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] によって Windows のイベント ビューアーに書き込まれます。 これらのメッセージを使用して、インストールと配置の問題を解決できます。  
  
## ログ ファイルおよびエラー メッセージを使用したスタートアップのエラーのトラブルシューティング  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] では、起動時に発生するすべてのエラーをログ ファイルに書き込んだり、エラーが発生するたびにメッセージ ボックスに表示したりできます。 既定では、これらのオプションはオフになっています。 オプションを有効にするには、環境変数を作成します。  
  
 エラーが発生するたびにメッセージ ボックスに表示するには、`VSTO_SUPPRESSDISPLAYALERTS` という環境変数を作成し、0 \(ゼロ\) に設定します。 メッセージが表示されないようにするには、環境変数を削除するか、1 に設定します。  
  
 エラーをログ ファイルに書き込むには、`VSTO_LOGALERTS` という環境変数を作成し、1 に設定します。[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] によって、VSTO アドインの配置マニフェストを含むフォルダーまたはカスタマイズに関連付けられている文書またはブックを含むフォルダーにログ ファイルが作成されます。 作成できない場合は、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] によって、ローカルの %TEMP% フォルダーにログ ファイルが作成されます。 アプリケーション レベルの VSTO アドインの場合、既定の名前は *add\-in name*.vsto.log です。 ドキュメント レベルのプロジェクトの場合、ログ ファイルの名前は *document name*.*extension*.log です \(例: ExcelWorkbook1.xlsx.log\)。 エラーのログ記録を停止するには、この環境変数を 0 \(ゼロ\) に設定します。  
  
## 参照  
 [Office ソリューションのビルド](../vsto/building-office-solutions.md)   
 [方法: 無効にされた VSTO アドインを再度有効にする](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)   
 [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)  
  
  