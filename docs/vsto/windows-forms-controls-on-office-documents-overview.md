---
title: Office ドキュメントの概要での Windows フォーム コントロール
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- old data showing in error [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], Word
- Windows Forms controls [Office development in Visual Studio], adding
- Windows Forms controls [Office development in Visual Studio], arranging
- data [Office development in Visual Studio], old data showing in error
- user controls [Office development in Visual Studio], Windows Forms
- Windows Forms controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], removing
- application development [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Windows Forms controls
- Office [Office development in Visual Studio], Windows Forms controls
- Office documents [Office development in Visual Studio, controls
- documents [Office development in Visual Studio], Windows Forms controls
- document-level customizations [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], about Windows Forms controls
- Office applications [Office development in Visual Studio], Windows Forms
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 51c671a583e4e96b51ae6627de1fce738696fe22
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892781"
---
# <a name="windows-forms-controls-on-office-documents-overview"></a>Office ドキュメントの概要での Windows フォーム コントロール
  Windows フォーム コントロールは、データを入力または操作するときにユーザーが取り扱うオブジェクトです。 Microsoft Office Excel および Microsoft Office Word のドキュメント レベルのプロジェクトで、プロジェクトで、デザイン時にドキュメントまたはブックに Windows フォーム コントロールを追加できますかプログラムで、実行時にこれらのコントロールを追加することができます。 プログラムで、任意の開いているドキュメントまたは VSTO アドインで実行時にワークシートに、Excel または Word のこれらのコントロールを追加することができます。  
  
 詳細については、次を参照してください。[方法: Office ドキュメントにコントロールを Windows フォームの追加](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)します。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="use-windows-forms-controls"></a>Windows フォーム コントロールを使用します。  
 Windows フォーム コントロールをドキュメントに、あるいは操作ウィンドウ、カスタム作業ウィンドウ、Windows フォームなどのカスタマイズ可能なユーザー インターフェイス (UI) 要素に追加できます。 Windows フォーム コントロールの動作は、ドキュメント上でも上述のその他の UI 要素上でも通常は同じですが、いくつかの相違点が存在します。 詳しくは、次を参照してください。[の制限事項の Windows フォーム コントロールの Office ドキュメント](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)します。  
  
 Windows フォーム コントロールをドキュメントに追加するか、その他の UI 要素に追加するかは、いくつかの要因を考慮して決定します。 ソリューションの UI を設計する場合は、次の表の説明に従って Windows フォーム コントロールの使用をご検討ください。  
  
 ドキュメント上  
 -   常時コントロールを表示する場合。  
  
- ユーザーにドキュメントに直接データを入力させる場合 (たとえば、編集サーフェスがロックされているフォーム ベースのドキュメント)。  
  
- コントロールをドキュメントのデータに沿って表示する場合。 たとえば、ボタンをリスト オブジェクトの各行に追加する場合、リストの各項目に沿って一直線に配置します。  
  
  操作ウィンドウまたはカスタム作業ウィンドウ上  
  -   コンテキスト情報をユーザーに提供する場合。  
  
- ドキュメントにクエリのコントロールやデータではなく、結果のみを表示する場合。  
  
- コントロールがドキュメントに印刷されないようにする場合。  
  
- コントロールがドキュメントの表示を妨げないようにする場合。  
  
  Windows フォーム上  
  -   UI のサイズを制御する場合。  
  
- ユーザーがコントロールを非表示にしたり、削除したりできないようにする場合。  
  
- ユーザーから入力を取得し、入力を受信するまではユーザーがドキュメントで何も処理できないようにする場合。  
  
## <a name="add-windows-forms-controls-programmatically"></a>Windows フォーム コントロールをプログラムで追加します。  
 Word 文書や実行時に Excel ワークシートには、Windows フォーム コントロールを追加できます。 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] は最も一般的な Windows フォーム コントロールを追加するためのヘルパー メソッドを提供します。 これらのヘルパー メソッドを使用すると、コントロールを Office ドキュメントにすばやく追加して、Windows フォーム コントロールの機能とこれらのコントロールの Office 関連機能とを組み合わせたものにアクセスできます。  
  
 詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)します。  
  
## <a name="use-windows-forms-controls-in-document-level-projects"></a>ドキュメント レベルのプロジェクトでの Windows フォーム コントロールを使用します。  
 ドキュメントでの Windows フォーム コントロールの使用方法のいくつかは、ドキュメント レベルのプロジェクトに固有です。これらにより、Visual Studio デザイナーを使用してドキュメントの UI をデザインできます。  
  
### <a name="create-custom-user-controls"></a>カスタム ユーザー コントロールを作成します。  
 ユーザー コントロールをプロジェクトに追加してから、それを **ツールボックス**に追加します。 ドキュメントに Windows フォーム コントロールを追加するのと同じ方法で、ドキュメントにユーザー コントロールを直接ドラッグできます。 ユーザー コントロールを作成するときには、以下の点にご注意ください。  
  
-   **sealed** ユーザー コントロールは作成しないでください。 ドキュメントにコントロールをドラッグすると、Visual Studio はユーザー コントロールから派生するラッパー クラスを生成して、そのクラスを拡張したり、ドキュメントでの使用をサポートしたりします。 ユーザー コントロールが **sealed**である場合、Visual Studio はラッパー クラスを生成することができません。  
  
-   ユーザー コントロールでは、 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 属性を **true**」を参照してください。 Office プロジェクト内で作成されたユーザー コントロールでは、この属性は既定で **true** に設定されますが、プロジェクト外部のユーザー コントロールでは、この属性は **true**に設定されていない場合があります。  
  
-   ユーザー コントロールをドキュメントに追加した後は、 <xref:System.Windows.Forms.UserControl> クラスの名前を変更したり、プロジェクトから削除したりしないでください。 ユーザー コントロールの名前を変更する必要がある場合は、ドキュメントからまず削除し、名前を変更した後でもう一度追加する必要があります。  
  
### <a name="arrange-controls-at-design-time"></a>デザイン時にコントロールを配置します。  
 デザイン時に Word および Excel のドキュメントに複数のコントロールを追加する場合、Visual Studio の **Microsoft Office Word** および **Microsoft Office Excel** ツール バーを使用して、選んだすべてのコントロールの配置をすばやく設定することができます。 これらのツール バーは、ドキュメントまたはワークシートがデザイナーで開かれている場合にのみ使用できます。  
  
 デザイナーで複数のコントロールを選ぶ場合、コントロールを配置するために、それらのツール バーにある以下のボタンを使用できます。  
  
-   **[左揃え]**  
  
-   **[中央揃え]**  
  
-   **[右揃え]**  
  
-   **[上揃え]**  
  
-   **[上下中央揃え]**  
  
-   **[下揃え]**  
  
-   **左右の間隔を均等にする**  
  
-   **上下の間隔を均等にする**  
  
> [!NOTE]  
>  Word プロジェクトでは、選んだコントロールが行内にない場合にのみ、これらのボタンが有効になります。 既定では、デザイン時にドキュメントに追加したコントロールは、行内にあります。  
  
### <a name="prevent-old-data-from-appearing-in-excel-workbooks-during-loading"></a>古いデータが読み込み中に Excel ブックに表示するを防ぐ  
 デザイン時にドキュメントやワークシートに Windows フォーム コントロールを追加すると、ユーザーがドキュメントを閉じても、コントロールはドキュメント内に残ります。 デザイン時に追加されたコントロールは、 *スタティック コントロール*とも呼ばれます。  
  
 スタティック コントロールが格納されている Excel ブックを開くと、カスタマイズ コードが実行されて実際のコントロールが読み込まれるまで、ブックでは ActiveX コントロールにコントロールのビットマップが表示されます。 Excel はこのビットマップを作成し、ブックが保存されるたびに、このブックにそのビットマップを格納します。 ビットマップには、ブックを最後に保存したときの状態でコントロールが表示され、コントロールに表示されていたすべてのデータも一緒に含められます。 Windows フォーム コントロールとビットマップを含んだ ActiveX コントロールの詳細については、次を参照してください。[の制限事項の Windows フォーム コントロールの Office ドキュメント](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)します。  
  
 ユーザーがデザイン モードでブックを開くとなど特定の条件では、コードは読み込まれず、ビットマップのみが表示されます。 また、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] がインストールされていないコンピューターでユーザーがブックを開く場合、コントロールを読み込むためのカスタマイズは実行できず、コントロールのビットマップのみが表示されます。 個人情報が誤って公開されないようにするため、ブックを保存して別のユーザーに送信する前に、必ず個人情報をブックのコントロールから削除する必要があります。  
  
### <a name="match-control-size-to-cell-size-on-an-excel-worksheet"></a>Excel ワークシートのセルのサイズに一致するコントロールのサイズ  
 親のセルのサイズが変更されたときに、自動的にサイズ変更されるようにコントロールを設定することができます。 詳細については、次を参照してください。[方法: ワークシートのセル内のコントロールをサイズ変更](../vsto/how-to-resize-controls-within-worksheet-cells.md)します。  
  
### <a name="add-components-that-are-shared-by-all-worksheets"></a>すべてのワークシートによって共有されるコンポーネントを追加します。  
 <xref:System.Data.DataSet>などすべてのワークシート間で共有するコンポーネントを、ワークシートではなくブックのデザイナーに追加することができます。 このコンポーネントは、コンポーネント トレイに表示されます。  
  
### <a name="formula-for-embedding-controls-on-an-excel-worksheet"></a>Excel ワークシート上のコントロールを埋め込むための数式  
 Excel 内でコントロールを選択すると、 **数式バー** に  " **=EMBED("WinForms.Control.Host","")**" と表示されます。 このテキストは必要なので、削除しないでください。  
  
### <a name="layout-style-of-controls-on-a-word-document"></a>Word 文書上のコントロールのレイアウト スタイル  
 Visual Studio デザイナーを使用してコントロールをドキュメント レベルのプロジェクトの Word 文書に追加する場合、コントロールは行内に追加されます。 コントロールのレイアウト スタイルを変更するには、コントロールを右クリックし、 **[コントロールの書式設定]** をクリックします。 **[オブジェクトの書式設定]** ダイアログ ボックスの **[レイアウト]** ページで折り返しのスタイルを選びます。  
  
 さまざまなを使用して、新しいコントロールのレイアウト スタイルを指定するには実行時に Word 文書にコントロールを追加するときに`Add` \<*コントロール クラス*> のメソッドのオーバー ロード、<xref:Microsoft.Office.Tools.Word.ControlCollection>クラス。  
  
- 行内のコントロールを追加するには、コントロールの場所を指定する <xref:Microsoft.Office.Interop.Word.Range> を受け取るオーバーロードを使用します。  
  
- 固定されていない図形としてコントロールを追加するには、コントロールの左と上の座標を受け入れるオーバーロードを使用します。  
  
  詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)します。  
  
  Visual Studio デザイナーで Word テンプレートを開く場合、Visual Studio でテンプレートが **標準** 表示で開かれるために、テンプレートのインラインでないコントロールを表示できない可能性があります。 コントロールを表示するには、表示を **印刷レイアウト**に変更します。  
  
### <a name="controls-outside-the-main-document-body"></a>ドキュメント本体外部コントロール  
 Windows フォーム コントロールは、ヘッダーまたはフッター内、あるいはサブドキュメント内ではサポートされません。  
  
### <a name="add-components-at-design-time"></a>デザイン時にコンポーネントを追加します。  
 特定のコントロールやコンポーネントは、ドキュメントに表示されずに、コンポーネント トレイに表示されます。 Visual Studio では、各ドキュメント ウィンドウに対して 1 つのコンポーネント トレイが提供されます。 コンポーネント トレイは、コンポーネントがドキュメントに存在する場合にのみ画面に表示されます。  
  
## <a name="see-also"></a>関連項目  
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [操作ウィンドウの概要](../vsto/actions-pane-overview.md)   
 [Windows フォーム コントロール](/dotnet/framework/winforms/controls/index)   
 [Office ドキュメントに Windows フォーム コントロールの制限事項](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [方法: Windows フォーム コントロールを Office ドキュメントに追加します。](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [方法: ワークシートのセル内のコントロールをサイズ変更](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [方法: 印刷時にワークシートのコントロールを非表示にします。](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [チュートリアル: CheckBox コントロールを使用してワークシートの書式設定を変更します。](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [チュートリアル: CheckBox コントロールを使用してドキュメントの書式設定を変更します。](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)   
 [チュートリアル: ボタンを使用してワークシート内のテキスト ボックスでテキストを表示します。](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [チュートリアル: ボタンを使用して文書内のテキスト ボックスでテキストを表示します。](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md)   
 [Office ドキュメントに Windows フォーム コントロールの制限事項](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)   
 [チュートリアル: オプション ボタンを使用してドキュメントのグラフを更新します。](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md)   
 [チュートリアル: オプション ボタンを使用してワークシートのグラフを更新します。](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  