---
title: Office プロジェクトをデバッグします。
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel projects [Office development in Visual Studio], debugging
- Word projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], debugging
- debugging [Office development in Visual Studio], Outlook projects
- Office projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], projects
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 59d9179bb0a3c3c2f08bbccafbca5db0202208e3
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867966"
---
# <a name="debug-office-projects"></a>Office プロジェクトをデバッグします。
  Office プロジェクトのデバッグは、他の [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] プロジェクトに使用するのと同じ Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tools を使用して実行できます。 Office プロジェクトのデバッグ時には、ブレークポイントの挿入や[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [ローカル] **ウィンドウでの変数の表示など、** デバッガーの機能も使用できます。 詳細については[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]デバッグ ツールを参照してください[Visual Studio でデバッグ](../debugger/debugging-in-visual-studio.md)します。

> [!TIP]
>  デバッグを簡略化するには、ビルドしてデバッグする前に、Office アプリケーションで開いているすべてのインスタンスを閉じます。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

> [!NOTE]
>  [複数のプラットフォーム](https://dev.office.com/add-in-availability)にまたがる Office を拡張するソリューション開発に関心がありますか？ 新しい [Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)をチェックして下さい。 Office アドインは VSTO アドインやソリューションと比較して、小さなフット プリントを持ち、HTML5、JavaScript、CSS3、XML などのほぼすべての web プログラミング テクノロジを使用して、ビルドすることができます。

## <a name="start-and-stop-the-debugger"></a>起動し、デバッガーを停止します
 その他のデバッグを開始するように、Office プロジェクトをデバッグすることができます[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]プロジェクト; たとえば、キーを押して、 **f5 キーを押して**キー。 VSTO アドイン プロジェクトのデバッグを開始するときに、対象となる Office アプリケーションの新しいプロセスが開始され、VSTO アドインが読み込まれます。

 ドキュメント レベルのプロジェクトのデバッグを開始すると、ドキュメントまたはブックは新しい Word または Excel プロセスで開かれます。

 デバッガーを停止すると、アプリケーション プロセスが即座に停止されます。また、デバッガーをデタッチするように設定してある場合にはデバッガーがデタッチされます。 停止する Office アプリケーション プロセスで開かれている他のすべてのドキュメントも警告を表示せずに閉じ、未保存の変更は失われます。 これには、デバッガーの実行中に開かれた文書やブックもすべて含まれます。

 一般に、通常の方法で Office アプリケーションを終了できるように、デバッガーを停止する前にプロセスからデタッチしておくことをお勧めします。 デバッガーを停止した後も開いているドキュメントやワークシートを操作する場合は、プロセスからデタッチすることもできます。

 Word のドキュメント レベルのカスタマイズ時に、デバッガーを何度も停止したり Word を突然終了したりすると、Normal テンプレートが破損する場合があります。 その場合は壊れた Normal テンプレートを削除します。テンプレートは、Word を次に開いたときに自動的に再作成されます。 ただし、Normal テンプレートに格納されていたマクロは再作成されません。

### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>Office 2013 または Office 2016 のいずれかを使用して Office 2013 VSTO アドインをデバッグする
 Visual Studio 2015 を使用している Office がインストールされて、並列の両方のバージョンがある場合は、Visual Studio は、Office 2016 を起動します。 Visual Studio 2013 を使用している場合、Visual Studio は、Office 2013 を起動します。

 別のバージョン (2013 または 2016) の Office を使用して VSTO アドインをデバッグする場合は、 **[プロジェクト デザイナー]** を開き、 **[デバッグ]** タブで **[外部プログラムの開始]** オプション ボタンをクリックします。 次に、適切な Office アプリケーションの実行可能ファイルの場所を参照します。

## <a name="f10-and-f11-behavior"></a>F10 および f11 キーの動作
 Office プロジェクトのデバッグを開始するときに**F10**と**F11**他の Visual Basic または c# プロジェクトのデバッグを開始するときと同じ動作にはありません。 Visual Basic や C# のプロジェクトの場合、デバッガーはメイン関数で停止しますが、Office プロジェクトの場合、Visual Studio では Office アプリケーションのメイン関数に対する制御権がありません。 ただし、デバッグ中に、 **F10**と**F11** Visual Basic および c# プロジェクトのように、同じ関数には。

## <a name="display-exceptions"></a>例外を表示します。
 Visual Studio では、マネージド コードによるアンマネージド コードの操作方法が原因で、Microsoft Office アプリケーションからスローされたエラーは表示されません。 たとえば、VSTO アドインを Visual Studio での Office 開発ツールを使用して作成された例外をスローする場合、Microsoft Office アプリケーションはエラーを表示せず続行されます。 これらのエラーを表示するには、デバッガーが共通言語ランタイムの例外で中断されるように設定します。 詳細については、次を参照してください。[デバッガーでの例外を管理](../debugger/managing-exceptions-with-the-debugger.md)します。

 共通言語ランタイム例外で中断するようにデバッガーを設定した場合、処理済みの例外や、プロジェクトに関係しない可能性もあるランタイム自体からのいくつかの初回例外も含め、すべての例外でデバッガーが中断されるようになります。 どのプロジェクトでも、不明な msosec を参照するエラーが表示されますが、これは無視してもかまいません。 このような msosec 例外はソリューションに影響しません。

 メソッドの周囲で **Try...Catch** ステートメントを使用して、例外をキャッチすることもできます。

 既定では、Visual Studio で Office プロジェクトの Just-In-Time デバッグ エラーも表示されませんが、発生したエラーを表示できるように、この機能を有効にすることができます。 詳細については、次を参照してください。[時間で Just Visual Studio でのデバッグ](../debugger/just-in-time-debugging-in-visual-studio.md)します。

## <a name="command-line-arguments"></a>コマンド ライン引数
 場合、**開始動作**上、**デバッグ**プロパティ ページに設定されている**スタート プロジェクト**、Visual Studio は使いませんコマンドライン引数、プロジェクトをデバッグするときにしている場合でも開始オプションのコマンドライン引数を指定してください。 デバッグを開始するときに、コマンドライン引数を使用する場合は、する必要があります、**開始動作**以外**スタート プロジェクト**します。

## <a name="source-control"></a>ソース管理
 デバッグ プロパティは、ソース管理で複数のユーザー間では共有されません。 Visual Basic プロジェクトや Visual C# プロジェクトでは、デバッグ プロパティはユーザー固有のファイル (*ProjectName*.vbproj.user または *ProjectName*.csproj.user) に格納されます。このファイルはソース管理されません。 複数のユーザーがデバッグを実行する場合は、各自が手動でデバッグ プロパティを入力する必要があります。

## <a name="debug-cached-datasets-in-a-document-level-project"></a>キャッシュされたデータセットのドキュメント レベルのプロジェクトのデバッグします。
 プロジェクトをビルドするたびに、データセットは空になり、再作成されます。 キャッシュされたデータセットをデバッグする場合は、Visual Studio の外部で文書を開いてからデバッガーをアタッチする必要があります。

## <a name="debug-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>Word 97-2003 ドキュメントに基づくデバッグ Word ドキュメント プロジェクト (* .doc) 形式
 Word 97-2003 ドキュメントに基づく Word 文書プロジェクトをデバッグする (*/*.doc *) 形式では、信頼できるフォルダー一覧に、プロジェクト フォルダーを追加する必要があります。 これを行う方法の詳細については、次を参照してください。[ドキュメントに信頼を付与](../vsto/granting-trust-to-documents.md)します。

## <a name="debug-disabled-add-ins"></a>デバッグには、アドインが無効になっています
 Microsoft Office アプリケーションにより、予期しない動作をする VSTO アドインが無効にされる場合があります。 Microsoft Office アプリケーションは、起動するたびに問題のあるコードが読み込まれないようにするため、VSTO アドインを無効にします。 しかし、通常のデバッグ時に、予期しない動作が発生することはよくあります。 VSTO アドインを再度有効にする方法については、次を参照してください。[方法。無効になっている VSTO アドインを再度有効にする](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)します。

 Microsoft Office アプリケーションで VSTO アドインに適用される無効化には、ハードな無効化とソフトな無効化の 2 種類があります。

### <a name="hard-disabling"></a>ハードな無効化
 ハードな無効化、VSTO アドインにより、アプリケーションは予期せず終了するときに発生します。 また、開発用コンピューターで VSTO アドインの <xref:Microsoft.Office.Tools.AddIn.Startup> イベント ハンドラーの実行中にデバッガーを停止した場合にも発生することがあります。 表示される VSTO アドインがハードに無効化、**できないアイテム**アプリケーションの一覧。

 VSTO アドインを Visual Studio での Office 開発ツールを使用して作成されたハード Office アプリケーションが無効化、のみ、VSTO アドインをエラーの原因となった、アプリケーションが無効にします。 Visual Studio の Office 開発ツールを使用してその Office アプリケーション用に作成されたその他の VSTO アドインの読み込みは続行されます。

### <a name="soft-disabling"></a>ソフトな無効化
 ソフトな無効化は、VSTO アドインによってエラーが発生したが、アプリケーションが予期せずに終了するということがなかったという場合に発生する可能性があります。 たとえば、 <xref:Microsoft.Office.Tools.AddIn.Startup> イベント ハンドラーの実行中に VSTO アドインによってハンドルされない例外がスローされた場合に、アプリケーションによってそのアドインがソフトに無効化されることがあります。 表示される VSTO アドインがソフトに無効化、**アクティブでないアプリケーション アドイン**アプリケーション、およびアプリケーションの一覧の値を変更する、 **LoadBehavior** VSTO アドインのレジストリ エントリ示すはアンロードされます。 詳細については、 **LoadBehavior**レジストリ エントリを参照してください[VSTO アドインのレジストリ エントリ](../vsto/registry-entries-for-vsto-add-ins.md)します。

## <a name="troubleshoot-installation-errors-by-using-the-event-viewer"></a>イベント ビューアーを使用してインストール エラーをトラブルシューティングします。
 Office ソリューションのインストール時またはアンインストール時にスローされたすべての例外のメッセージは、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] によって Windows のイベント ビューアーに書き込まれます。 これらのメッセージを使用して、インストールと配置の問題を解決できます。

## <a name="troubleshoot-startup-errors-by-using-a-log-file-and-error-messages"></a>ログ ファイルとエラー メッセージを使用してスタートアップ エラーをトラブルシューティングします。
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] では、起動時に発生するすべてのエラーをログ ファイルに書き込んだり、エラーが発生するたびにメッセージ ボックスに表示したりできます。 既定では、これらのオプションはオフになっています。 オプションは、環境変数を作成して有効にすることができます。

 エラーが発生するたびにメッセージ ボックスに表示するには、 `VSTO_SUPPRESSDISPLAYALERTS` という環境変数を作成し、0 (ゼロ) に設定します。 メッセージが表示されないようにするには、環境変数を削除するか、1 に設定します。

 エラーをログ ファイルに書き込むには、 `VSTO_LOGALERTS` という環境変数を作成し、1 に設定します。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] によって、VSTO アドインの配置マニフェストを含むフォルダーまたはカスタマイズに関連付けられている文書またはブックを含むフォルダーにログ ファイルが作成されます。 失敗した場合は、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 、ローカルのログ ファイルを作成します。 *%temp%* フォルダー。 アプリケーション レベルの VSTO アドインの場合、既定の名前は *add-in name*.vsto.log です。 ドキュメント レベルのプロジェクトの場合、ログ ファイルの名前は *document name*.*extension*.log です (例: ExcelWorkbook1.xlsx.log)。 エラーのログ記録を停止するには、この環境変数を 0 (ゼロ) に設定します。

## <a name="see-also"></a>関連項目

- [Office ソリューションを構築します。](../vsto/building-office-solutions.md)
- [方法: 無効になっている VSTO アドインを再度有効にします。](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)
- [VSTO アドインをプログラミングします。](../vsto/programming-vsto-add-ins.md)