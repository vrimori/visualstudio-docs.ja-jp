---
title: Office ドキュメントでの Windows フォーム コントロールの制限事項
ms.date: 02/02/2017
ms.technology: office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 104b8b3449b2ffb689caf66d5c180817b633f83e
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572960"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Office ドキュメントでの Windows フォーム コントロールの制限事項

Microsoft Office Word ドキュメントまたは Microsoft Office Excel ワークシートに追加される Windows フォーム コントロールと Windows フォームに追加される Windows フォーム コントロールの間には、いくつか違いがあります。 たとえば、追加、<xref:Microsoft.Office.Tools.Word.Controls.Button>など、ドキュメントのプロパティを制御<xref:System.Windows.Forms.Control.Dock>、 <xref:System.Windows.Forms.Control.Anchor>、および<xref:System.Windows.Forms.Control.TabIndex>期待どおりに動作しません。

これらの相違点の多くは方法に起因してその Windows フォームのコントロールがホストされているドキュメントでします。 Windows フォーム コントロールがドキュメントに追加されたときに、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]文書内の Windows フォーム コントロールをホストする ActiveX コントロールが埋め込まれます。 Windows フォーム コントロールはドキュメントに直接埋め込まれません。

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Windows フォーム コントロールのメソッドとプロパティの制限事項

いくつかのメソッドとは機能が同じドキュメントのように Windows フォームで場合、そのためをお勧めするを使用しないこと、Windows フォーム コントロールのプロパティがあります。 たとえばなどのプロパティの設定<xref:System.Windows.Forms.Control.Dock>と<xref:System.Windows.Forms.Control.Anchor>に関するドキュメントではなく、コンテナーの ActiveX コントロール、コントロールの位置にのみ影響します。 Word と Excel 用の Windows フォーム コントロールのサポートされていないメソッドとプロパティの一覧を次に示します。

- Excel のコントロールのサポートされていないプロパティ:

    - <xref:System.Windows.Forms.Control.Anchor>
    - <xref:System.Windows.Forms.Control.Dock>
    - <xref:System.Windows.Forms.Control.Location>
    - <xref:System.Windows.Forms.Control.TabIndex>
    - <xref:System.Windows.Forms.Control.TabStop>
    - <xref:System.Windows.Forms.Control.TopLevelControl>

- サポートされていないメソッドと Word コントロールのプロパティ:

    - <xref:System.Windows.Forms.Control.Hide%2A>
    - <xref:System.Windows.Forms.Control.Show%2A>
    - <xref:System.Windows.Forms.Control.Anchor>
    - <xref:System.Windows.Forms.Control.Dock>
    - <xref:System.Windows.Forms.Control.Location>
    - <xref:System.Windows.Forms.Control.TabIndex>
    - <xref:System.Windows.Forms.Control.TabStop>
    - <xref:System.Windows.Forms.Control.TopLevelControl>
    - <xref:System.Windows.Forms.Control.Visible>

設定することもできない、<xref:System.Windows.Forms.Control.Left>または<xref:System.Windows.Forms.Control.Top>Word 文書のテキストの範囲内である Windows フォーム コントロールのプロパティです。 Windows フォーム コントロールは、次の場合、テキストの範囲内に追加されます。

- プログラムによって Word 文書にコントロールを追加して場所の範囲を指定するメソッドを使用します。

- Windows フォーム コントロールは、デザイン時に Word 文書に追加します。 デザイナーでコントロールを変更することで、これを変更することができます。

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Office ドキュメントでの Windows フォーム コントロールの違い

Windows フォーム コントロール、通常がある動作は同じ Office ドキュメントに Windows フォームで、操作を行いますが、いくつかの相違点があります。 次の表では、Windows フォーム上のコントロールに Office ドキュメントに存在する違いについて説明します。

|機能|相違点|
|-------------------|----------------|
|コントロールのタブ オーダー|Excel のワークシートまたは Word 文書上のコントロール間を移動することはできません。|
|コントロールのグループ化|使用することはできません、 <xref:System.Windows.Forms.GroupBox> Office ドキュメントの他のコントロールを含めるにはコントロール。 ドキュメントに直接には、複数のオプション ボタンを追加するときにオプション ボタンは相互に排他的されません。 相互に排他的です。 オプション ボタンを作成するコードを記述することができます。ただし、推奨できるアプローチをラジオ ボタン コントロールに追加するユーザーとドキュメントに、ユーザー コントロールを追加します。 詳細については、コントロールのサンプルを Word または Excel でのコントロールのサンプルを参照してください[Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)です。|
|コントロール型|ドキュメントで使用される Windows フォーム コントロールは、によって提供されるクラスでラップされて、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Excel ワークシートまたは Word 文書にコントロール固有の追加機能を提供します。 ある場合など、**ボタン**Excel ワークシートにコントロールを型と型を指定してください<xref:Microsoft.Office.Tools.Excel.Controls.Button>なく<xref:System.Windows.Forms.Button>参照またはオブジェクトをキャストするときにします。|
|コントロールの位置とサイズ|コントロールの位置とサイズについては、ActiveX コントロール コンテナーの一部であるプロパティによって決まります。 ActiveX コントロールのプロパティは、Windows フォーム コントロールの同等のプロパティよりも異なる値を実行します。 設定すると、 `Top`、 `Left`、 `Height`、または`Width`単位でのコントロールのプロパティは、ピクセル単位ではなく、指しています。|
|Word 文書にコントロールの位置|フロー レイアウトにコントロールを追加する場合は、コントロールの内容が変更された内容でフローがあることに注意してください。 ドラッグしたときの段落にコントロールを固定することはできません、**ツールボックス**行内の Word 文書にコントロールが追加されるためです。 別のメソッドを使用して、コントロールをダブルクリックするなど、コントロールを追加する画像を挿入するために設定が Word のオプションに従って、コントロールが挿入されます。<br /><br /> 設定することはできません、`Left`または`Top`行内のテキストに挿入されているコントロールのプロパティです。<br /><br /> ヘッダーまたはページ フッター、または、サブドキュメント内でコントロールを配置することはできません。|
|コントロールのイベント|コントロールを選択すると、次の順序でイベントが発生します。<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> コントロールの選択を解除すると、次の順序でイベントが発生します。<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|コントロールのスケーリング|100% 以外に、ドキュメントのズーム設定を変更するときにコントロールを無効にするが、そのドキュメントでスケールを設定します。 たとえば、130% ズームでは、ドキュメントとボタンをクリックした場合、メッセージが表示されます、ズームを 100% に設定されるまでに、コントロールを無効になっていること。 ズームを 100% に変更する際に、コントロールが正しく機能します。|
|コントロールのプロパティ値|Windows フォームのコントロールのプロパティは、整数値に設定は、1 つの Word 文書上のコントロールに設定されます。 Excel では、コントロールのプロパティの値は、double 型の値に設定されます。 場合、`Height`と`Width`ワークシート上のコントロールのプロパティが、ワークシートまたは画面のサイズを超える場合、値は切り捨てられます。|
|コントロールのサイズ変更|8 つのサイズ変更ハンドルのいずれかを使用して、ドキュメント上のコントロールのサイズを変更する場合、新しいサイズには反映されません、**プロパティ**ウィンドウ、コントロールが再度選択するまでです。|
|コントロールの動作|Excel ワークシート上のコントロールは、ワークシート ウィンドウを分割すると、予期しない動作可能性があります。 たとえばへのアクセス、<xref:Microsoft.Office.Tools.Excel.Controls.TextBox>ワークシートでのみ使用可能ないずれかになります、windows のです。|
|コントロールの名前付け|コントロールの名前に予約語を使用することはできません。 追加する場合など、<xref:Microsoft.Office.Tools.Excel.Controls.Button>をワークシートに名前を変更し、**システム**プロジェクトをビルドするときにエラーが発生します。|
|コントロールをプログラムで追加します。|実行時にドキュメントにコントロールを追加するのにコントロールのコンス トラクターを使用しないでください。 代わりに、によって提供されるヘルパー メソッドを使用して、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]です。 たとえば、使用して、<xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A>ボタンをワークシートに追加するメソッド。 これらのヘルパー メソッドによってサポートされていないコントロールを追加する場合は、使用、`AddControl`メソッドです。 詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)です。|
|コントロールをコピー|Windows フォーム コントロールをコピーし、実行時にドキュメントに貼り付け、空のコンテナー ActiveX コントロールがドキュメントに貼り付けられます。 Windows フォーム コントロールが、新しい場所に表示されないと、元のコントロールの分離コードが ActiveX コントロール コンテナーにコピーされません。|

## <a name="limitations-in-document-level-projects"></a>ドキュメント レベルのプロジェクトでの制限事項

ドキュメント上で Windows フォーム コントロールを使用するいくつかの制限は、ドキュメント レベルのプロジェクトに固有です。

### <a name="control-support-at-design-time"></a>デザイン時にコントロールのサポート

特定の Windows フォーム コントロールから削除されます、**ツールボックス**Excel のワークシートまたは Word 文書が開いているとき、Visual Studio デザイナーでします。 これは、技術的な制限により、または機能は既に Word または Excel 内で使用できるためです。 Excel および Word プロジェクトのサポートのすべての Windows フォーム コントロールとその他のコンポーネントに表示される、**ツールボックス**、フォーカスのある文書とワークシートまたは文書にサード パーティ製コントロールを追加することもできます。

> [!NOTE]
> すべてのコントロールから削除されます、**ツールボックス**ドキュメントが保護されている場合。 ドキュメントの保護については、次を参照してください。[ドキュメント レベルのソリューションでの保護を文書化](../vsto/document-protection-in-document-level-solutions.md)です。

> [!NOTE]
> サード パーティ製コントロールがあります、<xref:System.Runtime.InteropServices.ComVisibleAttribute>属性に設定**true** Office ソリューションで使用するためにします。

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

既存の Word 文書または ActiveX コントロールを含む Excel ブックを使用するドキュメント レベルの Office プロジェクトを作成する場合の ActiveX コントロールの機能は失われます。ただし、Visual Studio 内からドキュメントに新しい ActiveX コントロールを追加するためのサポートされていません。 たとえば、Word 文書からボタンがある場合、**コントロール**Visual Basic for Applications (VBA) マクロを実行しているツールボックス、引き続き、ドキュメントを Office プロジェクトで使用した後、マクロを実行します。 ただし、ActiveX コントロールと VBA マクロを削除し、Windows フォーム コントロールに置き換えるをマネージ コードをお勧めはします。

## <a name="see-also"></a>関連項目

- [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)
- [Office ドキュメントの概要 Windows フォーム コントロール](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [方法: Office ドキュメントへの Windows フォーム コントロールの追加](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)