---
title: ListObject コントロール
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.List
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- lists, events
- ListObject control
- ListObject control, events
- ListObject control, data binding
- ListObject control, improving performance when bound to data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 46e7eeac888225a779856aac57aaccbf8fcb1c56
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34573012"
---
# <a name="listobject-control"></a>ListObject コントロール
  <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールは、イベントを公開するリストであり、データにバインドすることができます。 ワークシートにリストを追加すると、ユーザーが Microsoft Office Excel オブジェクト モデルを走査する必要なく、直接、プログラムできる <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールが Visual Studio により作成されます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="create-the-control"></a>コントロールを作成します。  
 ドキュメント レベルのプロジェクトでは、デザイン時または実行時に、ワークシートに <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールを追加できます。 追加することができます、VSTO アドイン プロジェクトで<xref:Microsoft.Office.Tools.Excel.ListObject>コントロールをワークシートが実行時にのみにします。 詳細については、次を参照してください。[する方法: ワークシートにコントロールを追加 ListObject](../vsto/how-to-add-listobject-controls-to-worksheets.md)です。  
  
> [!NOTE]  
>  既定では、動的に作成されたリスト オブジェクトは、ワークシートを閉じる際に、ホスト コントロールとしてワークシートに残りません。 詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)です。  
  
## <a name="bind-data-to-the-control"></a>コントロールにデータをバインドします。  
 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールでは、単純または複雑なデータ バインディングがサポートされます。 <xref:Microsoft.Office.Tools.Excel.ListObject>コントロールを使用して、データ ソースにバインドすることができます、<xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A>と<xref:Microsoft.Office.Tools.Excel.ListObject.DataMember%2A>デザイン時プロパティまたは<xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A>メソッド実行時にします。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.ListObject> は、データが変更されるとイベントを発生させる <xref:System.Data.DataTable>などのデータ ソースにバインドされると自動的に更新されます。 データが変更されたときにイベントを発生させないデータ ソースに <xref:Microsoft.Office.Tools.Excel.ListObject> をバインドする場合、 <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRow%2A> を更新するには <xref:Microsoft.Office.Tools.Excel.ListObject.RefreshDataRows%2A> または <xref:Microsoft.Office.Tools.Excel.ListObject>メソッドを呼び出す必要があります。  
  
 繰り返されるスキーマ要素をワークシート セルにマップして <xref:Microsoft.Office.Tools.Excel.ListObject> をそのセルに追加する場合、Visual Studio は <xref:Microsoft.Office.Tools.Excel.ListObject> を生成されたデータセットに自動的にマップします。 ただし、 <xref:Microsoft.Office.Tools.Excel.ListObject> はデータに自動的にバインドされません。 バインドする手順を行う、<xref:Microsoft.Office.Tools.Excel.ListObject>デザイン時またはドキュメント レベルのプロジェクトの実行時に、データセットにします。 プログラムでバインドすることができます、 <xref:Microsoft.Office.Tools.Excel.ListObject> VSTO アドインで実行時に、データセットにします。  
  
 データは <xref:Microsoft.Office.Tools.Excel.ListObject>とは分離されているため、データの追加と削除は、 <xref:Microsoft.Office.Tools.Excel.ListObject>から直接的にではなく、バインドされたデータセットを介して行う必要があります。 バインドされたデータセット内のデータが任意のメカニズムにより更新された場合に、 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールが変更を自動的に反映します。 詳細については、次を参照してください。 [Office ソリューションでのコントロールにデータをバインド](../vsto/binding-data-to-controls-in-office-solutions.md)です。  
  
 <xref:Microsoft.Office.Tools.Excel.ListObject> をデータ ソースにバインドすれば、 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールにすぐにデータを設定することができます。 データにバインドされた <xref:Microsoft.Office.Tools.Excel.ListObject>のデータを編集すると、データ ソースでも自動的に変更されます。 <xref:Microsoft.Office.Tools.Excel.ListObject> にデータを設定し、ユーザーがデータ ソースを変更せずに <xref:Microsoft.Office.Tools.Excel.ListObject> のデータを変更できるようにする場合、 <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> メソッドを使用してデータ ソースから <xref:Microsoft.Office.Tools.Excel.ListObject> をデタッチすることができます。 詳細については、次を参照してください。[する方法: ListObject の入力がデータをコントロール](../vsto/how-to-fill-listobject-controls-with-data.md)です。  
  
> [!NOTE]  
>  重複する <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールでは、データ バインディングはサポートされません。  
  
### <a name="improve-performance-in-listobject-controls"></a>ListObject コントロールでのパフォーマンスを向上させる  
 まずコントロールをバインドしてから <xref:Microsoft.Office.Tools.Excel.ListObject> を呼び出してデータセットにデータを設定する場合、データにバインドされた <xref:System.Data.DataSet.ReadXml%2A> コントロールに XML ファイルから読み込むときに時間がかかる傾向があります。 パフォーマンスを向上させるには、コントロールをバインドする前に <xref:System.Data.DataSet.ReadXml%2A> を呼び出します。  
  
### <a name="disconnect-listobject-controls-from-the-data-source"></a>ListObject コントロールをデータ ソースから切断します。  
 データ ソースにバインドして <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールにデータを設定した後に、リスト オブジェクトのデータに加えられた変更がデータ ソースに影響しないように、そのデータソースから切断することができます。 詳細については、次を参照してください。[する方法: ListObject の入力がデータをコントロール](../vsto/how-to-fill-listobject-controls-with-data.md)です。  
  
### <a name="restore-column-and-row-order"></a>列と行の順序を復元します。  
 デザイン時にドキュメントに追加された <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールにデータをバインドする場合、ブックを保存するたびに Visual Studio は列と行の順序を追跡し続けます。 ユーザーが移動した場合、<xref:Microsoft.Office.Tools.Excel.ListObject>実行時に行または列次回ブックを開いたときは新しい順序が維持され、<xref:Microsoft.Office.Tools.Excel.ListObject>再度をデータ ソース コントロールにバインドします。  
  
 <xref:Microsoft.Office.Tools.Excel.ListObject> を元の列と行の順序に復元する場合、 <xref:Microsoft.Office.Tools.Excel.ListObject.ResetPersistedBindingInformation%2A> メソッドを呼び出すことができます。 このメソッドは、指定した <xref:Microsoft.Office.Tools.Excel.ListObject>の列と行の順序に関連付けられたカスタム ドキュメント プロパティを削除します。 <xref:Microsoft.Office.Tools.Excel.Workbook.Shutdown> の列と行の順序を維持しない場合は、ブックの <xref:Microsoft.Office.Tools.Excel.ListObject>イベントからこのメソッドを呼び出します。  
  
## <a name="format"></a>形式  
 <xref:Microsoft.Office.Interop.Excel.ListObject> に適用できる書式設定は、 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールに適用できます。 これには、罫線、フォント、番号形式、スタイルが含まれます。 エンド ユーザーは、データにバインドされた <xref:Microsoft.Office.Tools.Excel.ListObject>の列を再配置できます。 <xref:Microsoft.Office.Tools.Excel.ListObject> がデザイン時にドキュメントに追加された場合、これらの変更はドキュメントで永続化されます。 次にドキュメントを開くとき、リスト オブジェクトは、同じデータ ソースにバインドされますが、列の順序についてはユーザーの変更が反映されます。  
  
## <a name="add-and-remove-columns-at-runtime"></a>追加し、実行時に列を削除します。  
 手動で追加またはデータにバインドされた列を削除することはできません<xref:Microsoft.Office.Tools.Excel.ListObject>実行時のコントロールです。 エンド ユーザーが列を削除しようとすると、その列はすぐに復元されます。また追加した列も削除されます。 そのため、データにバインドされた <xref:Microsoft.Office.Tools.Excel.ListObject> でユーザーがこれらの操作を実行できない理由を説明するコードを記述しておくことは重要です。 Visual Studio では、データ バインディングに関連する <xref:Microsoft.Office.Tools.Excel.ListObject> の複数のイベントが提供されます。 たとえば、 <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored> イベントを使用すると、ユーザーが削除しようとしたデータは削除できず、復元されたことを示す警告をユーザーに表示できます。  
  
## <a name="add-and-remove-rows-at-runtime"></a>追加し、実行時に行を削除します。  
 データ ソースで新しい行の追加が許可されており、読み取り専用ではない場合、データにバインドされた <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールの行を手動で追加したり削除したりすることができます。 <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> などのイベントに対してコードを記述してデータを検証することができます。 詳細については、次を参照してください。[する方法: ListObject コントロールに新しい行が追加されたときにデータを検証](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)です。  
  
 リスト オブジェクトのデータ ソースとの関係が原因で、日常的にエラーが発生することがあります。 たとえば、 <xref:Microsoft.Office.Tools.Excel.ListObject>で表示する列をマップできますが、null 値を許容できないフィールドなどの制限がある列を省略する場合、行が作成されるたびにエラーが発生します。 <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow> イベントのイベント ハンドラーで、失われた値を追加するコードを記述することができます。  
  
## <a name="rename-listobject-controls-in-excel"></a>Excel での ListObject コントロールの名前を変更します。  
 Excel では、ユーザーを使用して実行時に Excel のテーブルの名前を変更する、**デザイン**タブです。ただし、 <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールではこの機能はサポートされていません。 ユーザーが <xref:Microsoft.Office.Tools.Excel.ListObject>に対応する Excel の表の名前を変更しようとした場合、ブックが保存されると、Excel の表の名前は自動的に元の名前に戻されます。  
  
## <a name="events"></a>イベント  
 次のイベントは <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールに対して利用できます。  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Change>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataBindingFailure>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataMemberChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.DataSourceChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Deselected>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.ErrorAddDataBoundRow>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.OriginalDataRestored>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.Selected>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectedIndexChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.ListObject.SelectionChange>  
  
## <a name="see-also"></a>関連項目  
 [拡張オブジェクトによる Excel を自動化します。](../vsto/automating-excel-by-using-extended-objects.md)   
 [方法: ワークシートに ListObject コントロールを追加します。](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [方法: ListObject コントロールのサイズを変更します。](../vsto/how-to-resize-listobject-controls.md)   
 [方法: ListObject コントロールに新しい行が追加されたときにデータの検証](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)   
 [方法: データへのマップ ListObject 列](../vsto/how-to-map-listobject-columns-to-data.md)   
 [方法: 塗りつぶし ListObject がデータをコントロール](../vsto/how-to-fill-listobject-controls-with-data.md)   
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [Office ソリューションでのコントロールにデータをバインドします。](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Word 文書と実行時に VSTO アドイン内の Excel ブックを拡張します。](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [方法: データベースからデータをワークシートに読み込む](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  