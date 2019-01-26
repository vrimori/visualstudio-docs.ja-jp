---
title: .NET Framework 4 または .NET Framework 4.5 に移行する Excel および Word プロジェクトを更新します。
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 67a04436c26f16b07e209ddb907a0e1e7d282548
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869058"
---
# <a name="update-excel-and-word-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>.NET Framework 4 または .NET Framework 4.5 に移行する Excel および Word プロジェクトを更新します。
  次の機能を使用する Excel プロジェクトまたは Word プロジェクトのターゲット フレームワークを [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更する場合は、コードを変更する必要があります。  
  
- [GetVstoObject メソッドと HasVstoObject メソッド](#GetVstoObject)  
  
- [ドキュメント レベルのプロジェクトで生成されるクラス](#generatedclasses)  
  
- [ドキュメント上の Windows フォーム コントロール](#winforms)  
  
- [Word コンテンツ コントロールのイベント](#ccevents)  
  
- [OLEObject クラスと OLEControl クラス](#ole)  
  
- [Controls.Item(Object) プロパティ](#itemproperty)  
  
- [CollectionBase から派生するコレクション](#collections)  
  
  削除することも必要があります、`Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute`およびへの参照、`Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy`クラスに再ターゲットされた Excel プロジェクトから、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]またはそれ以降。 Visual Studio では、この属性またはクラスの参照を削除しません。  
  
## <a name="remove-the-excellocale1033-attribute-from-excel-projects"></a>Excel プロジェクトからの ExcelLocale1033 属性を削除します。  
 `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute`の Visual Studio 2010 Tools for Office ランタイムを対象とするソリューションに使用される部分から削除されましたが、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]またはそれ以降。 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降の共通言語ランタイム (CLR) は、Excel オブジェクト モデルに対しては常にロケール ID 1033 を渡します。この動作を無効にするために、この属性を使用することはできなくなりました。 詳細については、次を参照してください。 [Excel ソリューションのグローバリゼーションとローカリゼーション](../vsto/globalization-and-localization-of-excel-solutions.md)します。  
  
### <a name="to-remove-the-excellocale1033attribute"></a>ExcelLocale1033Attribute を削除するには  
  
1.  Visual Studio でプロジェクトを開き、 **ソリューション エクスプローラー**を開きます。  
  
2.  **[プロパティ]** ノード (C# の場合) または **[マイ プロジェクト]** ノード (Visual Basic の場合) の下で、AssemblyInfo コード ファイルをダブルクリックしてコード エディターで開きます。  
  
    > [!NOTE]  
    >  Visual Basic プロジェクトで AssemblyInfo コード ファイルを表示するには、 **ソリューション エクスプローラー** の **[すべてのファイルの表示]** ボタンをクリックする必要があります。  
  
3.  `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` を探し、ファイルから削除するか、コメント アウトします。  
  
    ```vb  
    <Assembly: ExcelLocale1033Proxy(True)>  
    ```  
  
    ```csharp  
    [assembly: ExcelLocale1033Proxy(true)]  
    ```  
  
## <a name="remove-a-reference-to-the-excellocal1033proxy-class"></a>ExcelLocal1033Proxy クラスへの参照を削除します。  
 Microsoft Visual Studio 2005 Tools for the Microsoft Office System を使用して作成されたプロジェクトでは、Excel の <xref:Microsoft.Office.Interop.Excel.Application> オブジェクトをインスタンス化するために `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` クラスを使用します。 このクラスは、Visual Studio 2010 Tools for Office ランタイムを対象とするソリューションの使用の部分から削除されました、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]またはそれ以降。 そのため、このクラスを参照するコード行を削除するか、コメント アウトする必要があります。  
  
### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>ExcelLocal1033Proxy クラスへの参照を削除するには  
  
1.  Visual Studio でプロジェクトを開き、 **[ソリューション エクスプローラー]** を開きます。  
  
2.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き*ThisAddin.cs* (c#) のまたは*ThisAddin.vb* (Visual Basic の場合) を選び、 **コードの表示**.  
  
3.  コード エディターの `VSTO generated code` 領域で、次のコード行を削除するか、コメント アウトします。  
  
    ```vb  
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)  
  
    ```  
  
    ```csharp  
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);  
  
    ```  
  
##  <a name="GetVstoObject"></a> Getvstoobject メソッドと HasVstoObject メソッドを使用するコードを更新します。  
 .NET Framework 3.5 をターゲットとするプロジェクトでは、`GetVstoObject` メソッドまたは `HasVstoObject` メソッドを、プロジェクトのネイティブ オブジェクト (<xref:Microsoft.Office.Interop.Word.Document>、<xref:Microsoft.Office.Interop.Excel.Workbook>、<xref:Microsoft.Office.Interop.Excel.Worksheet>、または <xref:Microsoft.Office.Interop.Excel.ListObject>) の拡張メソッドとして使用できます。 これらのメソッドを呼び出すときに、パラメーターを渡す必要はありません。 次のコード例では、.NET Framework 3.5 を対象とする Word VSTO アドインで GetVstoObject メソッドを使用する方法を示します。  
  
```vb  
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()  
```  
  
```csharp  
Microsoft.Office.Tools.Word.Document vstoDocument =   
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();  
```  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトでは、次のいずれかの方法でこれらのメソッドにアクセスするようにコードを変更する必要があります。  
  
- これらのメソッドに、 <xref:Microsoft.Office.Interop.Word.Document>、 <xref:Microsoft.Office.Interop.Excel.Workbook>、 <xref:Microsoft.Office.Interop.Excel.Worksheet>、または <xref:Microsoft.Office.Interop.Excel.ListObject> オブジェクトの拡張メソッドとして、今でもアクセスできます。 ただし、`Globals.Factory` プロパティによって返されるオブジェクトをこれらのメソッドに渡す必要があります。  
  
  ```vb  
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)  
  ```  
  
  ```csharp  
  Microsoft.Office.Tools.Word.Document vstoDocument =   
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);  
  ```  
  
- または、`Globals.Factory` プロパティによって返されるオブジェクトに対してこれらのメソッドにアクセスすることもできます。 この方法でこれらのメソッドにアクセスする場合は、拡張するネイティブ オブジェクトをメソッドに渡す必要があります。  
  
  ```vb  
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)  
  ```  
  
  ```csharp  
  Microsoft.Office.Tools.Word.Document vstoDocument =   
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);  
  ```  
  
  詳細については、次を参照してください。[拡張 Word 文書や Excel ブックを実行時に VSTO アドインで](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)します。  
  
##  <a name="generatedclasses"></a> ドキュメント レベルのプロジェクトで生成されたクラスのインスタンスを使用するコードを更新します。  
 .NET Framework 3.5 をターゲットとするドキュメント レベルのプロジェクトでは、プロジェクト内で生成されるクラスは、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]の次のクラスから派生します。  
  
- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>  
  
- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>  
  
- `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.Worksheet>  
  
- `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheet>  
  
  [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトにおいて、上記の [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] の型は、クラスではなくインターフェイスです。 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクト内で生成されるクラスは、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]の次の新しいクラスから派生します。  
  
- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>  
  
- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>  
  
- `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.WorksheetBase>  
  
- `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheetBase>  
  
  プロジェクトのコードで、生成されるいずれかのクラスのインスタンスを派生元の基底クラスとして参照している場合は、コードを変更する必要があります。  
  
  たとえば、.NET Framework 3.5 をターゲットとする Excel ブック プロジェクトでは、プロジェクトで生成される `Sheet`*n* クラスのインスタンスに何かの操作を実行するヘルパー メソッドを使用する場合があります。  
  
```vb  
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet)  
    ' Do something to the worksheet object.  
End Sub  
```  
  
```csharp  
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet)  
{  
    // Do something to the worksheet object.  
}  
```  
  
 プロジェクトのターゲットを [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更する場合は、次の変更のいずれかをコードに加える必要があります。  
  
-   `DoSomethingToSheet` メソッドを呼び出すすべてのコードを変更し、プロジェクトの <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> オブジェクトの <xref:Microsoft.Office.Tools.Excel.WorksheetBase> プロパティを渡すようにします。 このプロパティは、 <xref:Microsoft.Office.Tools.Excel.Worksheet> オブジェクトを返します。  
  
    ```vb  
    DoSomethingToSheet(Globals.Sheet1.Base)  
    ```  
  
    ```csharp  
    DoSomethingToSheet(Globals.Sheet1.Base);  
    ```  
  
-   `DoSomethingToSheet` メソッドのパラメーターを変更し、代わりに <xref:Microsoft.Office.Tools.Excel.WorksheetBase> オブジェクトを使用します。  
  
    ```vb  
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase)  
        ' Do something to the worksheet object.  
    End Sub  
    ```  
  
    ```csharp  
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet)  
    {  
        // Do something to the worksheet object.  
    }  
    ```  
  
##  <a name="winforms"></a> ドキュメントで Windows フォーム コントロールを使用するコードを更新します。  
 追加する必要があります、**を使用して**(c#) または**Imports** (Visual Basic) ステートメント、<xref:Microsoft.Office.Tools.Excel>または<xref:Microsoft.Office.Tools.Word>コントロール プロパティを使用して Windows フォームを追加するすべてのコード ファイルの先頭に名前空間文書またはワークシートにプログラムで制御します。  
  
 .NET Framework 3.5 をターゲットとするプロジェクトでは、Windows フォーム コントロールを追加するメソッド (`AddButton` メソッドなど) は、<xref:Microsoft.Office.Tools.Excel.ControlCollection> クラスおよび <xref:Microsoft.Office.Tools.Word.ControlCollection> クラスで定義されています。  
  
 プロジェクトを対象とするで、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]または後で、これらのメソッドは、コントロールのプロパティで使用できる拡張メソッド。 これらの拡張メソッドを使用するには、メソッドを使用するコード ファイルに、 **Controls** メソッドまたは **N:Microsoft.Office.Tools.Excel** 名前空間に対する <xref:Microsoft.Office.Tools.Excel> メソッドまたは <xref:Microsoft.Office.Tools.Word> ステートメントが必要です。 このステートメントは、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとする新しいプロジェクトでは、自動的に生成されます。 ただし、このステートメントは.NET Framework 3.5 をターゲットとするプロジェクトでは自動的に追加されないため、プロジェクトのターゲットを変更するときに自分で追加する必要があります。  
  
 詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)します。  
  
##  <a name="ccevents"></a> Word コンテンツ コントロールのイベントを処理するコードを更新します。  
 .NET Framework 3.5 をターゲットとするプロジェクトでは、Word コンテンツ コントロールのイベントは汎用の <xref:System.EventHandler%601> デリゲートによって処理されます。 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトでは、これらのイベントは他のデリゲートによって処理されるようになりました。  
  
 Word コンテンツ コントロールのイベントと、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトでこれらのイベントに関連付けられているデリゲートを次の表に示します。  
  
|event|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降のプロジェクトで使用するデリゲート|  
|-----------| - |  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|  
  
##  <a name="ole"></a> Oleobject クラスと OLEControl クラスを使用するコードを更新します。  
 .NET Framework 3.5 をターゲットとするプロジェクトでは、`Microsoft.Office.Tools.Excel.OLEObject` クラスと `Microsoft.Office.Tools.Word.OLEControl` クラスを使用して、カスタム コントロール (Windows フォームのユーザー コントロールなど) を文書またはワークシートに追加できます。  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトでは、これらのクラスは <xref:Microsoft.Office.Tools.Excel.ControlSite> インターフェイスと <xref:Microsoft.Office.Tools.Word.ControlSite> インターフェイスに置き換えられました。 `Microsoft.Office.Tools.Excel.OLEObject` および `Microsoft.Office.Tools.Word.OLEControl` を参照するコードは、<xref:Microsoft.Office.Tools.Excel.ControlSite> および <xref:Microsoft.Office.Tools.Word.ControlSite> を参照するように変更する必要があります。 新しい名前になったこと以外には、これらのコントロールの動作は .NET Framework 3.5 をターゲットとするプロジェクトでの動作と同じです。  
  
 詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)します。  
  
##  <a name="itemproperty"></a> Controls.Item(Object) プロパティを使用するコードを更新します。  
 Microsoft.Office.Tools.Word.Document.Controls の Item(Object) プロパティを使用する .NET Framework 3.5 を対象とするプロジェクトでまたは`Microsoft.Office.Tools.Excel.Worksheet.Controls`文書またはワークシートに指定したコントロールがあるかどうかを確認します。  
  
 プロジェクトを対象とするで、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] Item(Object) プロパティがこれらのコレクションから削除された後で、または。 に文書またはワークシートに、指定したコントロールが含まれるかどうか確認するには、の Contains(System.Object) メソッドを使用して、<xref:Microsoft.Office.Tools.Word.Document.Controls%2A>または<xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A>コレクション代わりにします。  
  
 文書またはワークシートのコントロールのコレクションの詳細については、次を参照してください。[実行時に Office ドキュメントにコントロールを追加](../vsto/adding-controls-to-office-documents-at-run-time.md)します。  
  
##  <a name="collections"></a> CollectionBase から派生するコレクションを使用するコードを更新します。  
 .NET Framework 3.5 を対象とするプロジェクトでいくつかのコレクション型で、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]から派生、<xref:System.Collections.CollectionBase>クラスなど、 `Microsoft.Office.Tools.SmartTagCollection`、`Microsoft.Office.Tools.Excel.ControlCollection`と`Microsoft.Office.Tools.Word.ControlCollection`します。  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトでは、これらのコレクション型はインターフェイスであり、 <xref:System.Collections.CollectionBase>からは派生しません。 <xref:System.Collections.CollectionBase.Capacity%2A>、 <xref:System.Collections.CollectionBase.List%2A>、 <xref:System.Collections.CollectionBase.InnerList%2A>などの一部のメンバーは、これらのコレクション型で使用できなくなりました。  
  
## <a name="see-also"></a>関連項目  
 [.NET Framework 4 またはそれ以降の Office ソリューションを移行します。](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [コンテンツ コントロール](../vsto/content-controls.md)   
 [Word 文書と Excel ブックを実行時に VSTO アドインで拡張します。](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)  
