---
title: "Excel プロジェクトおよび Word プロジェクトの .NET Framework 4 または .NET Framework 4.5 に移行する更新 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
ms.assetid: 282c8876-fd49-462e-875b-4a0a79ad951c
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ab2fb40485e92ff097e0c39102024528125dfc72
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="updating-excel-and-word-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>.NET Framework 4 または .NET Framework 4.5 に移行する Excel プロジェクトおよび Word プロジェクトの更新
  次の機能を使用する Excel プロジェクトまたは Word プロジェクトのターゲット フレームワークを [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更する場合は、コードを変更する必要があります。  
  
-   [GetVstoObject メソッドと HasVstoObject メソッド](#GetVstoObject)  
  
-   [ドキュメント レベルのプロジェクトで生成されるクラス](#generatedclasses)  
  
-   [ドキュメント上の Windows フォーム コントロール](#winforms)  
  
-   [Word コンテンツ コントロールのイベント](#ccevents)  
  
-   [OLEObject クラスと OLEControl クラス](#ole)  
  
-   [Controls.Item(Object) プロパティ](#itemproperty)  
  
-   [CollectionBase から派生するコレクション](#collections)  
  
 Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute およびに再ターゲットされた Excel プロジェクトから Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy クラスへの参照を削除することも必要があります、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]またはそれ以降。 Visual Studio では、この属性またはクラスの参照を削除しません。  
  
## <a name="removing-the-excellocale1033-attribute-from-excel-projects"></a>Excel プロジェクトからの ExcelLocale1033 属性の削除  
 For Office ランタイムを対象とするソリューションに使用される、Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute、Visual Studio 2010 Tools の部分から削除されましたが、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]またはそれ以降。 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降の共通言語ランタイム (CLR) は、Excel オブジェクト モデルに対しては常にロケール ID 1033 を渡します。この動作を無効にするために、この属性を使用することはできなくなりました。 詳細については、「 [Globalization and Localization of Excel Solutions](../vsto/globalization-and-localization-of-excel-solutions.md)」を参照してください。  
  
#### <a name="to-remove-the-excellocale1033attribute"></a>ExcelLocale1033Attribute を削除するには  
  
1.  Visual Studio でプロジェクトを開き、 **ソリューション エクスプローラー**を開きます。  
  
2.  **[プロパティ]** ノード (C# の場合) または **[マイ プロジェクト]** ノード (Visual Basic の場合) の下で、AssemblyInfo コード ファイルをダブルクリックしてコード エディターで開きます。  
  
    > [!NOTE]  
    >  Visual Basic プロジェクトで AssemblyInfo コード ファイルを表示するには、 **ソリューション エクスプローラー** の **[すべてのファイルの表示]** ボタンをクリックする必要があります。  
  
3.  Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute を見つけて、ファイルから削除するか、またはコメント アウトします。  
  
    ```vb  
    <Assembly: ExcelLocale1033Proxy(True)>  
    ```  
  
    ```csharp  
    [assembly: ExcelLocale1033Proxy(true)]  
    ```  
  
## <a name="removing-a-reference-to-the-excellocal1033proxy-class"></a>ExcelLocal1033Proxy クラスへの参照の削除  
 Microsoft Office System 用 Microsoft Visual Studio 2005 Tools を使用して作成されたプロジェクトは、Excel をインスタンス化<xref:Microsoft.Office.Interop.Excel.Application>Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy クラスを使用してオブジェクト。 このクラスは for Office Runtime をターゲットとするソリューションの使用は、Visual Studio 2010 Tools の部分から削除されました、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]またはそれ以降。 そのため、このクラスを参照するコード行を削除するか、コメント アウトする必要があります。  
  
#### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>ExcelLocal1033Proxy クラスへの参照を削除するには  
  
1.  Visual Studio でプロジェクトを開き、 **[ソリューション エクスプローラー]**を開きます。  
  
2.  **[ソリューション エクスプローラー]**で ThisAddin.cs (C# の場合) または ThisAddin.vb (Visual Basic の場合) のショートカット メニューを開き、 **[コードの表示]**を選択します。  
  
3.  コード エディターの `VSTO generated code` 領域で、次のコード行を削除するか、コメント アウトします。  
  
    ```vb  
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)  
  
    ```  
  
    ```csharp  
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);  
  
    ```  
  
##  <a name="GetVstoObject"></a> GetVstoObject メソッドと HasVstoObject メソッドを使用するコードの更新  
 プロジェクトでは、.NET Framework 3.5 を対象とする、GetVstoObject または HasVstoObject メソッドは、プロジェクト内の次のネイティブ オブジェクトのいずれかの拡張メソッドとして使用できます: <xref:Microsoft.Office.Interop.Word.Document>、 <xref:Microsoft.Office.Interop.Excel.Workbook>、 <xref:Microsoft.Office.Interop.Excel.Worksheet>、または<xref:Microsoft.Office.Interop.Excel.ListObject>です。 これらのメソッドを呼び出すときに、パラメーターを渡す必要はありません。 次のコード例では、.NET Framework 3.5 を対象とする Word VSTO アドインで GetVstoObject メソッドを使用する方法を示します。  
  
```vb  
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()  
```  
  
```csharp  
Microsoft.Office.Tools.Word.Document vstoDocument =   
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();  
```  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトでは、次のいずれかの方法でこれらのメソッドにアクセスするようにコードを変更する必要があります。  
  
-   これらのメソッドに、 <xref:Microsoft.Office.Interop.Word.Document>、 <xref:Microsoft.Office.Interop.Excel.Workbook>、 <xref:Microsoft.Office.Interop.Excel.Worksheet>、または <xref:Microsoft.Office.Interop.Excel.ListObject> オブジェクトの拡張メソッドとして、今でもアクセスできます。 ただし、これらのメソッドに Globals.Factory プロパティによって返されるオブジェクトを渡すようになりました必要があります。  
  
    ```vb  
    Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
        Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)  
    ```  
  
    ```csharp  
    Microsoft.Office.Tools.Word.Document vstoDocument =   
        Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);  
    ```  
  
-   または Globals.Factory プロパティによって返されるオブジェクトでこれらのメソッドにアクセスすることができます。 この方法でこれらのメソッドにアクセスする場合は、拡張するネイティブ オブジェクトをメソッドに渡す必要があります。  
  
    ```vb  
    Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
        Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)  
    ```  
  
    ```csharp  
    Microsoft.Office.Tools.Word.Document vstoDocument =   
        Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);  
    ```  
  
 詳細については、「 [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
##  <a name="generatedclasses"></a> ドキュメント レベルのプロジェクトで生成されるクラスのインスタンスを使用するコードの更新  
 .NET Framework 3.5 をターゲットとするドキュメント レベルのプロジェクトでは、プロジェクト内で生成されるクラスは、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]の次のクラスから派生します。  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.Worksheet>  
  
-   `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheet>  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトにおいて、上記の [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] の型は、クラスではなくインターフェイスです。 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクト内で生成されるクラスは、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] の次の新しいクラスから派生します。  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.WorksheetBase>  
  
-   `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheetBase>  
  
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
  
##  <a name="winforms"></a> ドキュメント上で Windows フォーム コントロールを使用するコードの更新  
 追加する必要があります、**を使用して**(c#) または**Imports** (Visual Basic) ステートメント、<xref:Microsoft.Office.Tools.Excel>または<xref:Microsoft.Office.Tools.Word>コントロール プロパティを使用して Windows フォームを追加するすべてのコード ファイルの先頭に名前空間文書またはワークシートにプログラムで制御します。  
  
 プロジェクトでは、.NET Framework 3.5 を対象とする、(、AddButton メソッドなど) の Windows フォーム コントロールを追加するメソッドが定義されている、<xref:Microsoft.Office.Tools.Excel.ControlCollection>と<xref:Microsoft.Office.Tools.Word.ControlCollection>クラスです。  
  
 対象とするプロジェクトで、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]または後で、これらのメソッドは、コントロールのプロパティで使用できる拡張メソッド。 これらの拡張メソッドを使用するには、メソッドを使用するコード ファイルに、 **Controls** メソッドまたは **N:Microsoft.Office.Tools.Excel** 名前空間に対する <xref:Microsoft.Office.Tools.Excel> メソッドまたは <xref:Microsoft.Office.Tools.Word> ステートメントが必要です。 このステートメントは、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとする新しいプロジェクトでは、自動的に生成されます。 ただし、このステートメントは.NET Framework 3.5 をターゲットとするプロジェクトでは自動的に追加されないため、プロジェクトのターゲットを変更するときに自分で追加する必要があります。  
  
 詳細については、「 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
##  <a name="ccevents"></a> Word コンテンツ コントロールのイベントを処理するコードの更新  
 .NET Framework 3.5 をターゲットとするプロジェクトでは、Word コンテンツ コントロールのイベントは汎用の <xref:System.EventHandler%601> デリゲートによって処理されます。 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトでは、これらのイベントは他のデリゲートによって処理されるようになりました。  
  
 Word コンテンツ コントロールのイベントと、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトでこれらのイベントに関連付けられているデリゲートを次の表に示します。  
  
|event|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降のプロジェクトで使用するデリゲート|  
|-----------|---------------------------------------------------------------------------------------------------|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|  
  
##  <a name="ole"></a> OLEObject クラスと OLEControl クラスを使用するコードの更新  
 プロジェクトで .NET Framework 3.5 を対象とするカスタム コントロールを追加できます (Windows フォーム ユーザー コントロールなど) 文書またはワークシート Microsoft.Office.Tools.Excel.OLEObject と Microsoft.Office.Tools.Word.OLEControl クラスを使用しています。  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトでは、これらのクラスは <xref:Microsoft.Office.Tools.Excel.ControlSite> インターフェイスと <xref:Microsoft.Office.Tools.Word.ControlSite> インターフェイスに置き換えられました。 参照先を参照するには、Microsoft.Office.Tools.Excel.OLEObject と Microsoft.Office.Tools.Word.OLEControl コードを変更する必要があります<xref:Microsoft.Office.Tools.Excel.ControlSite>と<xref:Microsoft.Office.Tools.Word.ControlSite>です。 新しい名前になったこと以外には、これらのコントロールの動作は .NET Framework 3.5 をターゲットとするプロジェクトでの動作と同じです。  
  
 詳細については、「 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
##  <a name="itemproperty"></a> Controls.Item(Object) プロパティを使用するコードの更新  
 プロジェクトでは、.NET Framework 3.5 を対象とする、文書またはワークシートがあるかどうかを確認する Microsoft.Office.Tools.Word.Document.Controls または Microsoft.Office.Tools.Excel.Worksheet.Controls コレクションの Item(Object) プロパティを使用することができます、指定されたコントロール。  
  
 対象とするプロジェクトで、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]か Item(Object) プロパティを後で、これらのコレクションから削除されています。 文書またはワークシートに、指定されたコントロールが含まれるかどうかを判断するのには、Contains(System.Object) 方法を使用して、<xref:Microsoft.Office.Tools.Word.Document.Controls%2A>または<xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A>コレクション代わりにします。  
  
 文書またはワークシートのコントロール コレクションの詳細については、次を参照してください。[を実行時に Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)です。  
  
##  <a name="collections"></a> CollectionBase から派生するコレクションを使用するコードの更新  
 プロジェクトでは、.NET Framework 3.5 を対象とする、いくつかのコレクション型、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]から派生して、 <xref:System.Collections.CollectionBase> Microsoft.Office.Tools.SmartTagCollection など、Microsoft.Office.Tools.Excel.ControlCollection のクラスとMicrosoft.Office.Tools.Word.ControlCollection です。  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトでは、これらのコレクション型はインターフェイスであり、 <xref:System.Collections.CollectionBase>からは派生しません。 <xref:System.Collections.CollectionBase.Capacity%2A>、 <xref:System.Collections.CollectionBase.List%2A>、 <xref:System.Collections.CollectionBase.InnerList%2A>などの一部のメンバーは、これらのコレクション型で使用できなくなりました。  
  
## <a name="see-also"></a>参照  
 [Migrating Office Solutions to the .NET Framework 4 or later](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [コンテンツ コントロール](../vsto/content-controls.md)   
 [実行時の Word 文書と VSTO アドイン内の Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [実行時に Office ドキュメントにコントロールを追加します。](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)  
  
  