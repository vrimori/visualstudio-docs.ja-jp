---
title: Office ドキュメントに Windows フォーム コントロールの制限事項
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 610ee5e18054b6da35a3098b851d1585c70b6bc3
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863553"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Office ドキュメントに Windows フォーム コントロールの制限事項

Microsoft Office Word ドキュメントまたは Microsoft Office Excel のワークシートに追加される Windows フォーム コントロールと Windows フォームに追加される Windows フォーム コントロールの間には、いくつか違いがあります。 たとえば、追加、<xref:Microsoft.Office.Tools.Word.Controls.Button>など、ドキュメントのプロパティを制御<xref:System.Windows.Forms.Control.Dock>、 <xref:System.Windows.Forms.Control.Anchor>、および<xref:System.Windows.Forms.Control.TabIndex>予想どおりに動作しません。

これらの相違点の多くは方法に起因してその Windows フォームのコントロールがホストされているドキュメントにします。 Windows フォーム コントロールがドキュメントに追加されたときに、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]し、ドキュメント内の Windows フォーム コントロールをホストする ActiveX コントロールが埋め込まれます。 Windows フォームのコントロールがドキュメントに直接埋め込まれません。

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Windows フォーム コントロールのメソッドとプロパティの制限事項

さまざまな方法と動作しないと同じ方法でドキュメントを Windows フォームの場合し、そのため、お勧めする使用できない場合が Windows フォーム コントロールのプロパティがあります。 たとえばなどのプロパティを設定<xref:System.Windows.Forms.Control.Dock>と<xref:System.Windows.Forms.Control.Anchor>に関して、ドキュメントではなく、コンテナーの ActiveX コントロール、コントロールの位置にのみ影響します。 Word および Excel 用の Windows フォーム コントロールのサポートされていないメソッドとプロパティの一覧を次には。

- Excel のコントロールのサポートされていないプロパティ:

    - <xref:System.Windows.Forms.Control.Anchor>
    - <xref:System.Windows.Forms.Control.Dock>
    - <xref:System.Windows.Forms.Control.Location>
    - <xref:System.Windows.Forms.Control.TabIndex>
    - <xref:System.Windows.Forms.Control.TabStop>
    - <xref:System.Windows.Forms.Control.TopLevelControl>

- サポートされていないメソッド、および Word コントロールのプロパティ:

    - <xref:System.Windows.Forms.Control.Hide%2A>
    - <xref:System.Windows.Forms.Control.Show%2A>
    - <xref:System.Windows.Forms.Control.Anchor>
    - <xref:System.Windows.Forms.Control.Dock>
    - <xref:System.Windows.Forms.Control.Location>
    - <xref:System.Windows.Forms.Control.TabIndex>
    - <xref:System.Windows.Forms.Control.TabStop>
    - <xref:System.Windows.Forms.Control.TopLevelControl>
    - <xref:System.Windows.Forms.Control.Visible>

設定することもできない、<xref:System.Windows.Forms.Control.Left>または<xref:System.Windows.Forms.Control.Top>Word 文書でテキストの範囲にある Windows フォーム コントロールのプロパティ。 Windows フォーム コントロールは、次の場合にテキストの範囲に追加されます。

- Word 文書にコントロールを追加して位置の範囲を指定するメソッドを使用するプログラムでは。

- デザイン時に、Word 文書に Windows フォーム コントロールを追加します。 これは、デザイナーでコントロールを変更することで変更できます。

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Office ドキュメントでの Windows フォーム コントロールの違い

Windows フォーム コントロール通常がある動作は同じ Office ドキュメントのように Windows フォーム上でこれらの操作を行いますが、いくつかの違いがあります。 次の表では、Office ドキュメントでの Windows フォーム コントロール用に存在する違いについて説明します。

|機能|相違点|
|-------------------|----------------|
|コントロールのタブ オーダー|Excel のワークシートまたは Word 文書上のコントロール間を移動することはできません。|
|コントロールのグループ化|使用することはできません、 <xref:System.Windows.Forms.GroupBox> Office ドキュメントの他のコントロールを格納するコントロール。 ドキュメントを直接に複数のオプション ボタンを追加するときにラジオ ボタンが相互に排他的なされません。 相互に排他的です。 オプション ボタンを作成するコードを記述することができます。ただし、推奨されるアプローチは、ユーザー コントロールへのラジオ ボタンを追加し、ドキュメントにユーザー コントロールを追加するは。 詳細については、コントロールのサンプルを Word または Excel コントロールのサンプルで参照してください[Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)します。|
|コントロール型|ドキュメントで使用される Windows フォーム コントロールが用意されているクラスにラップされます、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Word 文書、Excel ワークシートにコントロール固有の追加機能を提供します。 ある場合など、**ボタン**Excel ワークシートにコントロールを型と型を指定してください<xref:Microsoft.Office.Tools.Excel.Controls.Button>なく<xref:System.Windows.Forms.Button>参照またはオブジェクトをキャストするときにします。|
|コントロールの位置とサイズ|コントロールの位置とサイズについては、ActiveX コントロール コンテナーの一部であるプロパティによって決まります。 ActiveX コントロールのプロパティは、異なる Windows フォーム コントロールの同等のプロパティ値を取得します。 設定すると、 `Top`、 `Left`、 `Height`、または`Width`単位で、コントロールのプロパティは、ピクセル単位ではなく、ポイントします。|
|Word 文書にコントロールの位置|フロー レイアウトにコントロールを追加する場合は、コントロールの内容、コンテンツの変更フローされることに留意してください。 ドラッグしたときに、段落にコントロールを固定することはできません、**ツールボックス**行内の Word 文書にコントロールが追加されるためです。 など、コントロールをダブルクリックすると、コントロールを追加する別のメソッドを使用する場合は、Word の画像の挿入に設定したオプションに従って、コントロールが挿入されます。<br /><br /> 設定することはできません、`Left`または`Top`行内にあるコントロールのプロパティ。<br /><br /> または、サブドキュメント内のヘッダーまたはフッターでは、コントロールを配置することはできません。|
|コントロールのイベント|コントロールがオンの場合、次の順序でイベントを発生させます。<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> コントロールの選択を解除すると、次の順序でイベントが発生します。<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|コントロールのスケーリング|100% 以外に、ドキュメントのズーム設定を変更するときにコントロールが無効になっている、ように見えますが、ドキュメントを使用して拡張します。 たとえば、ドキュメントが 130% ズーム ボタンをクリックした場合、メッセージが表示されます、ズームが 100% に設定されるまで、コントロールが無効されていること。 ズームを 100% に変更すると、コントロールは正しく機能します。|
|コントロール プロパティの値|Windows フォームのコントロールのプロパティは、整数値に設定は、Word 文書上のコントロールの 1 つに設定されます。 Excel では、コントロールのプロパティの値が double 型の値に設定されます。 場合、`Height`と`Width`ワークシート上のコントロールのプロパティは、ワークシートまたは画面のサイズを超えています。、、の値は切り捨てられます。|
|コントロールのサイズ変更|8 つのサイズ変更ハンドルのいずれかを使用して、ドキュメント上のコントロールのサイズを変更する場合、新しいサイズには反映されません、**プロパティ**ウィンドウ コントロールが再度選択するまでです。|
|コントロールの動作|Excel ワークシート上のコントロールは、ワークシート ウィンドウを分割すると、予期しない動作可能性があります。 アクセスなど、<xref:Microsoft.Office.Tools.Excel.Controls.TextBox>ワークシートの可能性がありますのみ取得できる、windows のいずれか。|
|コントロールの名前付け|コントロールの名前に予約語を使用することはできません。 追加する場合など、<xref:Microsoft.Office.Tools.Excel.Controls.Button>ワークシートに名を変更して、**システム**プロジェクトをビルドするときにエラーが発生します。|
|プログラムでコントロールを追加します。|実行時にドキュメントにコントロールを追加するのにコントロールのコンス トラクターを使用しないでください。 代わりに、によって提供されるヘルパー メソッドを使用して、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]します。 たとえば、使用して、<xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A>ワークシートにボタンを追加するメソッド。 これらのヘルパー メソッドでサポートされていないコントロールを追加する場合は、使用、`AddControl`メソッド。 詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)します。|
|コントロールのコピー|Windows フォーム コントロールをコピーして実行時のドキュメントに貼り付けることをドキュメントに空の ActiveX コントロール コンテナーが貼り付けられます。 Windows フォームのコントロールが新しい場所に表示されないと、元のコントロールの分離コードは ActiveX コントロール コンテナーにコピーされません。|

## <a name="limitations-in-document-level-projects"></a>ドキュメント レベルのプロジェクトでの制限事項

ドキュメントで Windows フォーム コントロールを使用するいくつかの制限は、ドキュメント レベルのプロジェクトに固有です。

### <a name="control-support-at-design-time"></a>デザイン時にコントロールのサポート

特定の Windows フォーム コントロールから削除されます、**ツールボックス**は Excel のワークシートまたは Word 文書の Visual Studio デザイナーで開きます。 これは、技術的な制限により、機能は、既に Word または Excel 内で使用できるため、または。 Excel および Word プロジェクトでは、すべての Windows フォーム コントロールおよびその他のコンポーネントに表示されるサポート、**ツールボックス**ときに、ドキュメントにフォーカスがあり、ワークシートまたは文書にサードパーティ製のコントロールを追加することもできます。

> [!NOTE]
> すべてのコントロールから削除されます、**ツールボックス**ドキュメントが保護されている場合。 ドキュメントの保護については、次を参照してください。[文書の保護をドキュメント レベルのソリューションで](../vsto/document-protection-in-document-level-solutions.md)します。

> [!NOTE]
> サードパーティ製のコントロールがあります、<xref:System.Runtime.InteropServices.ComVisibleAttribute>属性に設定**true** Office ソリューションで使用するためにします。

次のコントロールおよびコンポーネントでは使用できない、**ツールボックス**:

- <xref:System.Windows.Forms.BindingNavigator>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.DataGrid>

- <xref:System.DirectoryServices.DirectoryEntry>

- <xref:System.DirectoryServices.DirectorySearcher>

- <xref:System.Windows.Forms.ErrorProvider>

- <xref:System.Diagnostics.EventLog>

- <xref:System.IO.FileSystemWatcher>

- <xref:System.Windows.Forms.FlowLayoutPanel>

- <xref:System.Windows.Forms.GroupBox>

- <xref:System.Windows.Forms.MainMenu>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Messaging.MessageQueue>

- <xref:System.Windows.Forms.NotifyIcon>

- <xref:System.Windows.Forms.PageSetupDialog>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Diagnostics.PerformanceCounter>

- <xref:System.Windows.Forms.PrintDialog>

- <xref:System.Drawing.Printing.PrintDocument>

- <xref:System.Windows.Forms.PrintPreviewControl>

- <xref:System.Diagnostics.Process>

- <xref:System.Windows.Forms.RichTextBox>

- <xref:System.IO.Ports.SerialPort>

- <xref:System.ServiceProcess.ServiceController>

- <xref:System.Windows.Forms.SplitContainer>

- <xref:System.Windows.Forms.Splitter>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TableLayoutPanel>

- <xref:System.Timers.Timer>

- <xref:System.Windows.Forms.Timer>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.ToolStripContainer>

- <xref:System.Windows.Forms.ToolStripDropDown>

- <xref:System.Windows.Forms.ToolStripDropDownMenu>

- <xref:System.Windows.Forms.ToolStripPanel>

### <a name="support-for-legacy-activex-controls"></a>従来の ActiveX コントロールのサポート

既存の Word 文書または ActiveX コントロールを含む Excel ブックを使用するドキュメント レベルの Office プロジェクトを作成する場合、ActiveX コントロールの機能が失われます。ただし、Visual Studio 内からドキュメントを新しい ActiveX コントロールを追加するためのサポートされていません。 たとえば、Word 文書からボタンがある場合、**コントロール**Visual Basic for Applications (VBA) マクロを実行しているツールボックス、引き続き、ドキュメントを Office プロジェクトで使用した後、マクロを実行します。 ただし、ActiveX コントロールと VBA マクロを削除し、Windows フォーム コントロールで置き換えることをマネージ コードをお勧めしますが。

## <a name="see-also"></a>関連項目

- [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)
- [Office ドキュメントの概要での Windows フォーム コントロール](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [方法: Office ドキュメントへの Windows フォーム コントロールを追加します。](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)