---
title: "Office ドキュメントでの Windows フォーム コントロールの制限事項 | Microsoft Docs"
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
  - "ActiveX コントロール [Visual Studio での Office 開発]"
  - "コントロール [Visual Studio での Office 開発], Windows フォーム コントロール"
  - "Office ドキュメント [Visual Studio での Office 開発, Windows フォーム コントロール"
  - "ツールボックス [Visual Studio での Office 開発], サポートされていないコントロール"
  - "ユーザー コントロール [Visual Studio での Office 開発], グループ化 (コントロールを)"
  - "Windows フォーム コントロール [Visual Studio での Office 開発], ActiveX レガシ"
  - "Windows フォーム コントロール [Visual Studio での Office 開発], 制限事項"
  - "Windows フォーム コントロール [Visual Studio での Office 開発], ツールボックス"
  - "Windows フォーム コントロール [Visual Studio での Office 開発], サポートされていないプロパティとメソッド"
ms.assetid: 95ff473e-4952-4977-bc88-c77289c9fb0b
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Office ドキュメントでの Windows フォーム コントロールの制限事項
  Microsoft Office Word 文書または Microsoft Office Excel ワークシートに追加されている Windows フォーム コントロールと、Windows フォームに追加されている Windows フォーム コントロールには相違点があります。  たとえば、<xref:Microsoft.Office.Tools.Word.Controls.Button> コントロールを Word 文書に追加すると、<xref:Microsoft.Office.Tools.Word.Controls.Button.Dock%2A>、<xref:Microsoft.Office.Tools.Word.Controls.Button.Anchor%2A>、<xref:Microsoft.Office.Tools.Word.Controls.Button.TabIndex%2A> などのプロパティは、予測したようには動作しません。  
  
 相違点の多くは、Windows フォーム コントロールがドキュメントでホストされる方法の違いによるものです。  Windows フォーム コントロールをドキュメントに追加した場合は、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] によって ActiveX コントロールが埋め込まれ、これがドキュメント内の Windows フォーム コントロールをホストします。  Windows フォーム コントロールはドキュメントには直接埋め込まれません。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Windows フォーム コントロールのメソッドおよびプロパティの制限事項  
 Windows フォーム コントロールのメソッドおよびプロパティには、ドキュメント上では Windows フォーム上で使用する場合と同じようには動作しないものが多数あり、これらはドキュメント上では使用しないことをお勧めします。  たとえば、`Dock` や `Anchor` などのプロパティを設定した場合、これらはドキュメントではなくコンテナー ActiveX コントロールに対する Windows フォーム コントロールの位置にのみ作用します。  Word および Excel ではサポートされていない Windows フォーム コントロールのメソッドおよびプロパティの一覧を次に示します。  
  
-   Excel のコントロールでサポートされていないメソッドおよびプロパティ  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
-   Word のコントロールでサポートされていないメソッドおよびプロパティ  
  
    -   `Hide`  
  
    -   `Show`  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
    -   `Visible`  
  
 Word 文書でテキスト行内に挿入されている Windows フォーム コントロールの `Left` プロパティまたは `Top` プロパティも設定できません。  Windows フォーム コントロールは、次のような場合に、テキスト行内に追加されます。  
  
-   コントロールをプログラムで Word 文書に追加し、場所の範囲を指定するメソッドを使用する場合。  
  
-   デザイン時に Word 文書に Windows フォーム コントロールを追加する場合。  これは、デザイナーでコントロールを修正することで、変更できます。  
  
## Office ドキュメントでの Windows フォーム コントロールの相違点  
 一般に、Windows フォーム コントロールは、Office ドキュメント上にあっても Windows フォーム上にある場合と同じように動作しますが、いくつか相違点があります。  Office ドキュメントにおける Windows フォーム コントロールの相違点を次の表に示します。  
  
|機能|相違点|  
|--------|---------|  
|コントロールのタブ オーダー|Excel ワークシートまたは Word 文書上にあるコントロール間はタブ移動できません。|  
|コントロールのグループ化|Office ドキュメント上のコントロールは、<xref:System.Windows.Forms.GroupBox> コントロールを使用してグループ化することはできません。  ドキュメントに直接複数のオプション ボタンを追加した場合は、これらは一度に 1 つしか選択できないオプション ボタンにはなりません。  複数のオプション ボタンを同時に選択できないようにコードを作成することもできますが、オプション ボタンをユーザー コントロールに追加してから、そのユーザー コントロールを文書に追加する方法をお勧めします。  詳細については、「[Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)」の Word コントロールのサンプルおよび Excel コントロールのサンプルを参照してください。|  
|コントロールの型|ドキュメント上で使用される Windows フォーム コントロールは、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] で提供されるクラスにラップされており、それによって Excel ワークシートまたは Word 文書に固有の機能がコントロールに追加されています。  たとえば、Excel ワークシートの `Button` コントロールをオブジェクトとして参照またはキャストするときは、<xref:System.Windows.Forms.Button> 型ではなく必ず <xref:Microsoft.Office.Tools.Excel.Controls.Button> 型を指定します。|  
|コントロールの位置およびサイズ|コントロールのサイズおよび位置は、コンテナー ActiveX コントロールに含まれる各種プロパティによって決定されます。  ActiveX コントロールのプロパティは、Windows フォーム コントロールの同等のプロパティとは異なる値を持ちます。  コントロールの `Top`、`Left`、`Height`、または `Width` の各プロパティに設定する値は、ピクセル単位ではなくポイント単位になります。|  
|Word 文書のコントロールの位置|前後の流れのあるレイアウトにコントロールを追加すると、内容が変更された場合にはその内容の流れに従ってコントロールも移動します。  **ツールボックス**からコントロールをドラッグして追加した場合、そのコントロールは Word 文書内のテキスト行内に挿入されるので、特定の段落には固定できません。  コントロールをダブルクリックするなど別の方法でコントロールを追加した場合は、画像の挿入について設定してある Word のオプションに従ってコントロールが挿入されます。<br /><br /> テキスト行内に挿入されているコントロールの `Left` プロパティまたは `Top` プロパティは設定できません。<br /><br /> コントロールは、ヘッダーやフッターの内部、またはサブドキュメントの内部には配置できません。|  
|コントロールのイベント|コントロールを選択すると、次の順番でイベントが発生します。<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> コントロールの選択を解除すると、次の順番でイベントが発生します。<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|  
|コントロールの拡大と縮小|ドキュメントのズーム設定を 100% 以外に変更すると、コントロールはドキュメントと同じ倍率で表示されますが、無効になります。  たとえば、130% ズームでドキュメントを表示しているときにボタンをクリックすると、ズームを 100% に設定しないとコントロールが無効であることを示すメッセージが表示されます。  ズームを 100% に変更すると、コントロールは正常に動作します。|  
|コントロールのプロパティ値|Windows フォーム上のコントロールのプロパティには整数値が設定されますが、Word 文書上のコントロールのプロパティには単精度浮動小数点数型 \(Single\) の値が設定されます。  Excel では、コントロールのプロパティ値には倍精度浮動小数点数型 \(Double\) の値が設定されます。  ワークシート上のコントロールの `Height` プロパティおよび `Width` プロパティの値がそのワークシートまたは画面のサイズを超える場合、その値は切り捨てられます。|  
|コントロールのサイズ変更|8 つのサイズ変更ハンドルのいずれかを使ってドキュメント上のコントロールのサイズを変更した場合は、そのコントロールを再度選択するまで新しいサイズが **\[プロパティ\]** ウィンドウに反映されません。|  
|コントロールの動作|Excel ワークシート上のコントロールは、ワークシート ウィンドウが分割されていると予期しない動作をすることがあります。  たとえば、ワークシート上の <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> には、ウィンドウのうち 1 つからしかアクセスできない場合があります。|  
|コントロールの名前付け|コントロールの名前に予約語は使用できません。  たとえば、ワークシートに <xref:Microsoft.Office.Tools.Excel.Controls.Button> コントロールを追加し、名前を「**System**」に変更すると、そのプロジェクトをビルドするときにエラーが発生します。|  
|プログラミングによるコントロールの追加|実行時にコントロールのコンストラクターを使用してドキュメントにコントロールを追加することはできません。  その代わり、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] で提供されているヘルパー メソッドを使用します。  たとえば、ワークシートにボタンを追加するには、<xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> メソッドを使用します。  ヘルパー メソッドでサポートされていないコントロールを追加するには、AddControl メソッドを使用できます。  詳細については、「[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。|  
|コントロールのコピー|実行時に Windows フォーム コントロールをコピーしてドキュメントに貼り付けると、ドキュメントに空のコンテナー ActiveX コントロールが貼り付けられます。  貼り付けた先に Windows フォーム コントロールは表示されず、元のコントロールの背後にあるコードはコンテナー ActiveX コントロールにコピーされません。|  
  
## ドキュメント レベルのプロジェクトの制限  
 ドキュメントで Windows フォーム コントロールを使用する場合、ドキュメント レベルのプロジェクトに固有の制限があります。  
  
### デザイン時のコントロールのサポート  
 Visual Studio デザイナーで Excel ワークシートまたは Word 文書を開いているときは、一部の Windows フォーム コントロールは **\[ツールボックス\]** から削除されます。  これは技術的な制限があったり、機能が既に Word または Excel 内で使用可能であったりするためです。  Excel および Word プロジェクトでは、文書にフォーカスがあるときに **\[ツールボックス\]** に表示されるすべての Windows フォーム コントロールおよび他のコンポーネントがサポートされ、サードパーティ製のコントロールをワークシートまたは文書に追加することもできます。  
  
> [!NOTE]  
>  ドキュメントが保護されている場合は、すべてのコントロールが **\[ツールボックス\]** から削除されます。  ドキュメントの保護については、「[ドキュメント レベルのソリューションにおけるドキュメントの保護](../vsto/document-protection-in-document-level-solutions.md)」を参照してください。  
  
> [!NOTE]  
>  サードパーティ製のコントロールの場合、Office ソリューションで使用するためには、<xref:System.Runtime.InteropServices.ComVisibleAttribute> 属性が **true** に設定されている必要があります。  
  
 次のコントロールとコンポーネントは **\[ツールボックス\]** にはありません。  
  
-   <xref:System.Windows.Forms.BindingNavigator>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.DataGrid>  
  
-   <xref:System.DirectoryServices.DirectoryEntry>  
  
-   <xref:System.DirectoryServices.DirectorySearcher>  
  
-   <xref:System.Windows.Forms.ErrorProvider>  
  
-   <xref:System.Diagnostics.EventLog>  
  
-   <xref:System.IO.FileSystemWatcher>  
  
-   <xref:System.Windows.Forms.FlowLayoutPanel>  
  
-   <xref:System.Windows.Forms.GroupBox>  
  
-   <xref:System.Windows.Forms.MainMenu>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Messaging.MessageQueue>  
  
-   <xref:System.Windows.Forms.NotifyIcon>  
  
-   <xref:System.Windows.Forms.PageSetupDialog>  
  
-   <xref:System.Windows.Forms.Panel>  
  
-   <xref:System.Diagnostics.PerformanceCounter>  
  
-   <xref:System.Windows.Forms.PrintDialog>  
  
-   <xref:System.Drawing.Printing.PrintDocument>  
  
-   <xref:System.Windows.Forms.PrintPreviewControl>  
  
-   <xref:System.Diagnostics.Process>  
  
-   <xref:System.Windows.Forms.RichTextBox>  
  
-   <xref:System.IO.Ports.SerialPort>  
  
-   <xref:System.ServiceProcess.ServiceController>  
  
-   <xref:System.Windows.Forms.SplitContainer>  
  
-   <xref:System.Windows.Forms.Splitter>  
  
-   <xref:System.Windows.Forms.StatusBar>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
-   <xref:System.Windows.Forms.TableLayoutPanel>  
  
-   <xref:System.Timers.Timer>  
  
-   <xref:System.Windows.Forms.Timer>  
  
-   <xref:System.Windows.Forms.ToolBar>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.ToolStripContainer>  
  
-   <xref:System.Windows.Forms.ToolStripDropDown>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownMenu>  
  
-   <xref:System.Windows.Forms.ToolStripPanel>  
  
### レガシ ActiveX コントロールのサポート  
 ActiveX コントロールが含まれた既存の Word 文書または Excel ブックを使用するドキュメント レベルの Office プロジェクトを作成した場合、その ActiveX コントロールの機能は失われませんが、Visual Studio 内からのドキュメントへの新しい ActiveX コントロールの追加はサポートされていません。  たとえば、**\[コントロール ツールボックス\]** から追加され、VBA \(Visual Basic for Applications\) マクロを実行するボタンが Word 文書にある場合、その文書が Office プロジェクトで使用された後も、引き続きそのボタンはマクロを実行します。  ただし、ActiveX コントロールおよび VBA マクロを削除し、Windows フォーム コントロールおよびマネージ コードに置き換えることをお勧めします。  
  
## 参照  
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [Office ドキュメントでの Windows フォーム コントロールの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [方法 : Office ドキュメントに Windows フォーム コントロールを追加する](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)  
  
  