---
title: ".NET Framework 4 または .NET Framework 4.5 に移行する Excel プロジェクトおよび Word プロジェクトの更新 | Microsoft Docs"
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
  - "Office プロジェクト [Visual Studio での Office 開発]、.NET Framework 4 への移行"
ms.assetid: 282c8876-fd49-462e-875b-4a0a79ad951c
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# .NET Framework 4 または .NET Framework 4.5 に移行する Excel プロジェクトおよび Word プロジェクトの更新
  次の機能を使用する Excel プロジェクトまたは Word プロジェクトのターゲット フレームワークを [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更する場合は、コードを変更する必要があります。  
  
-   [GetVstoObject メソッドと HasVstoObject メソッド](#GetVstoObject)  
  
-   [ドキュメント レベルのプロジェクトで生成されるクラス](#generatedclasses)  
  
-   [ドキュメント上の Windows フォーム コントロール](#winforms)  
  
-   [Word コンテンツ コントロールのイベント](#ccevents)  
  
-   [OLEObject クラスと OLEControl クラス](#ole)  
  
-   [Controls.Item\(Object\) プロパティ](#itemproperty)  
  
-   [CollectionBase から派生するコレクション](#collections)  
  
 また、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降にターゲットを変更する Excel プロジェクトからは、Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute を削除し、Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy クラスへの参照を削除する必要もあります。 Visual Studio では、この属性や、クラスへの参照が自動的に削除されることはありません。  
  
## Excel プロジェクトからの ExcelLocale1033 属性の削除  
 Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute は、Visual Studio 2010 Tools for Office Runtime のうち、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットにするソリューションで使用される部分から削除されました。[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降の共通言語ランタイム \(CLR\) は、Excel オブジェクト モデルに対しては常にロケール ID 1033 を渡します。この動作を無効にするために、この属性を使用することはできなくなりました。 詳細については、「[Excel ソリューションのグローバリゼーションとローカリゼーション](../vsto/globalization-and-localization-of-excel-solutions.md)」を参照してください。  
  
#### ExcelLocale1033Attribute を削除するには  
  
1.  Visual Studio でプロジェクトを開き、**ソリューション エクスプローラー**を開きます。  
  
2.  **\[プロパティ\]** ノード \(C\# の場合\) または **\[マイ プロジェクト\]** ノード \(Visual Basic の場合\) の下で、AssemblyInfo コード ファイルをダブルクリックしてコード エディターで開きます。  
  
    > [!NOTE]  
    >  Visual Basic プロジェクトで AssemblyInfo コード ファイルを表示するには、**ソリューション エクスプローラー**の **\[すべてのファイルの表示\]** ボタンをクリックする必要があります。  
  
3.  Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute を探し、ファイルから削除するか、コメント アウトします。  
  
    ```vb  
    <Assembly: ExcelLocale1033Proxy(True)>  
    ```  
  
    ```csharp  
    [assembly: ExcelLocale1033Proxy(true)]  
    ```  
  
## ExcelLocal1033Proxy クラスへの参照の削除  
 Microsoft Visual Studio 2005 Tools for the Microsoft Office System を使用して作成されたプロジェクトでは、Excel の <xref:Microsoft.Office.Interop.Excel.Application> オブジェクトをインスタンス化するために Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy クラスを使用します。 このクラスは、Visual Studio 2010 Tools for Office Runtime のうち、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするソリューションのために使用される部分から削除されました。 そのため、このクラスを参照するコード行を削除するか、コメント アウトする必要があります。  
  
#### ExcelLocal1033Proxy クラスへの参照を削除するには  
  
1.  Visual Studio でプロジェクトを開き、**\[ソリューション エクスプローラー\]** を開きます。  
  
2.  **\[ソリューション エクスプローラー\]** で ThisAddin.cs \(C\# の場合\) または ThisAddin.vb \(Visual Basic の場合\) のショートカット メニューを開き、**\[コードの表示\]** を選択します。  
  
3.  コード エディターの `VSTO generated code` 領域で、次のコード行を削除するか、コメント アウトします。  
  
    ```vb  
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)  
  
    ```  
  
    ```csharp  
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);  
  
    ```  
  
##  <a name="GetVstoObject"></a> GetVstoObject メソッドと HasVstoObject メソッドを使用するコードの更新  
 .NET Framework 3.5 をターゲットとするプロジェクトでは、GetVstoObject メソッドまたは HasVstoObject メソッドを、プロジェクトのネイティブ オブジェクト \(<xref:Microsoft.Office.Interop.Word.Document>、<xref:Microsoft.Office.Interop.Excel.Workbook>、<xref:Microsoft.Office.Interop.Excel.Worksheet>、または <xref:Microsoft.Office.Interop.Excel.ListObject>\) の拡張メソッドとして使用できます。 これらのメソッドを呼び出すときに、パラメーターを渡す必要はありません。 次のコード例は、.NET Framework 3.5 をターゲットとする Word VSTO アドインで GetVstoObject メソッドを使用する方法を示しています。  
  
```vb  
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _ Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()  
```  
  
```csharp  
Microsoft.Office.Tools.Word.Document vstoDocument = Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();  
```  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトでは、次のいずれかの方法でこれらのメソッドにアクセスするようにコードを変更する必要があります。  
  
-   これらのメソッドに、<xref:Microsoft.Office.Interop.Word.Document>、<xref:Microsoft.Office.Interop.Excel.Workbook>、<xref:Microsoft.Office.Interop.Excel.Worksheet>、または <xref:Microsoft.Office.Interop.Excel.ListObject> オブジェクトの拡張メソッドとして、今でもアクセスできます。 ただし、Globals.Factory プロパティによって返されるオブジェクトをこれらのメソッドに渡す必要があります。  
  
    ```vb  
    Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _ Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)  
    ```  
  
    ```csharp  
    Microsoft.Office.Tools.Word.Document vstoDocument = Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);  
    ```  
  
-   または、Globals.Factory プロパティによって返されるオブジェクトに対してこれらのメソッドにアクセスすることもできます。 この方法でこれらのメソッドにアクセスする場合は、拡張するネイティブ オブジェクトをメソッドに渡す必要があります。  
  
    ```vb  
    Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _ Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)  
    ```  
  
    ```csharp  
    Microsoft.Office.Tools.Word.Document vstoDocument = Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);  
    ```  
  
 詳細については、「[VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)」を参照してください。  
  
##  <a name="generatedclasses"></a> ドキュメント レベルのプロジェクトで生成されるクラスのインスタンスを使用するコードの更新  
 .NET Framework 3.5 をターゲットとするドキュメント レベルのプロジェクトでは、プロジェクト内で生成されるクラスは、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] の次のクラスから派生します。  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.Worksheet>  
  
-   `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheet>  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトにおいて、上記の [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] の型は、クラスではなくインターフェイスです。[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクト内で生成されるクラスは、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] の次の新しいクラスから派生します。  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.WorksheetBase>  
  
-   `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheetBase>  
  
 プロジェクトのコードで、生成されるいずれかのクラスのインスタンスを派生元の基底クラスとして参照している場合は、コードを変更する必要があります。  
  
 たとえば、.NET Framework 3.5 をターゲットとする Excel ブック プロジェクトでは、プロジェクトで生成される `Sheet`*n* クラスのインスタンスに何かの操作を実行するヘルパー メソッドを使用する場合があります。  
  
```vb  
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet) ' Do something to the worksheet object. End Sub  
```  
  
```csharp  
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet) { // Do something to the worksheet object. }  
```  
  
 プロジェクトのターゲットを [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降に変更する場合は、次の変更のいずれかをコードに加える必要があります。  
  
-   `DoSomethingToSheet` メソッドを呼び出すすべてのコードを変更し、プロジェクトの <xref:Microsoft.Office.Tools.Excel.WorksheetBase> オブジェクトの <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> プロパティを渡すようにします。 このプロパティは、<xref:Microsoft.Office.Tools.Excel.Worksheet> オブジェクトを返します。  
  
    ```vb  
    DoSomethingToSheet(Globals.Sheet1.Base)  
    ```  
  
    ```csharp  
    DoSomethingToSheet(Globals.Sheet1.Base);  
    ```  
  
-   `DoSomethingToSheet` メソッドのパラメーターを変更し、代わりに <xref:Microsoft.Office.Tools.Excel.WorksheetBase> オブジェクトを使用します。  
  
    ```vb  
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase) ' Do something to the worksheet object. End Sub  
    ```  
  
    ```csharp  
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet) { // Do something to the worksheet object. }  
    ```  
  
##  <a name="winforms"></a> ドキュメント上で Windows フォーム コントロールを使用するコードの更新  
 Controls プロパティを使用して文書またはワークシートにプログラムで Windows フォーム コントロールを追加するすべてのコード ファイルの先頭に、<xref:Microsoft.Office.Tools.Excel> 名前空間または <xref:Microsoft.Office.Tools.Word> 名前空間に対する **using** \(c\#\) または **Imports** \(Visual Basic\) ステートメントを追加する必要があります。  
  
 .NET Framework 3.5 をターゲットとするプロジェクトでは、Windows フォーム コントロールを追加するメソッド \(AddButton メソッドなど\) は、<xref:Microsoft.Office.Tools.Excel.ControlCollection> クラスおよび <xref:Microsoft.Office.Tools.Word.ControlCollection> クラスで定義されています。  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトでは、これらのメソッドは Controls プロパティで使用できる拡張メソッドです。 これらの拡張メソッドを使用するには、メソッドを使用するコード ファイルに、<xref:Microsoft.Office.Tools.Excel> 名前空間または <xref:Microsoft.Office.Tools.Word> 名前空間に対する **using** ステートメントまたは **Imports** ステートメントが必要です。 このステートメントは、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとする新しいプロジェクトでは、自動的に生成されます。 ただし、このステートメントは.NET Framework 3.5 をターゲットとするプロジェクトでは自動的に追加されないため、プロジェクトのターゲットを変更するときに自分で追加する必要があります。  
  
 詳細については、「[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
##  <a name="ccevents"></a> Word コンテンツ コントロールのイベントを処理するコードの更新  
 .NET Framework 3.5 をターゲットとするプロジェクトでは、Word コンテンツ コントロールのイベントは汎用の <xref:System.EventHandler%601> デリゲートによって処理されます。[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトでは、これらのイベントは他のデリゲートによって処理されるようになりました。  
  
 Word コンテンツ コントロールのイベントと、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトでこれらのイベントに関連付けられているデリゲートを次の表に示します。  
  
|イベント|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降のプロジェクトで使用するデリゲート|  
|----------|---------------------------------------------------------------------------------|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|  
  
##  <a name="ole"></a> OLEObject クラスと OLEControl クラスを使用するコードの更新  
 .NET Framework 3.5 をターゲットとするプロジェクトでは、Microsoft.Office.Tools.Excel.OLEObject クラスと Microsoft.Office.Tools.Word.OLEControl クラスを使用して、カスタム コントロール \(Windows フォームのユーザー コントロールなど\) を文書またはワークシートに追加できます。  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトでは、これらのクラスは <xref:Microsoft.Office.Tools.Excel.ControlSite> インターフェイスと <xref:Microsoft.Office.Tools.Word.ControlSite> インターフェイスに置き換えられました。Microsoft.Office.Tools.Excel.OLEObject および Microsoft.Office.Tools.Word.OLEControl を参照するコードは、<xref:Microsoft.Office.Tools.Excel.ControlSite> および <xref:Microsoft.Office.Tools.Word.ControlSite> を参照するように変更する必要があります。 新しい名前になったこと以外には、これらのコントロールの動作は .NET Framework 3.5 をターゲットとするプロジェクトでの動作と同じです。  
  
 詳細については、「[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」を参照してください。  
  
##  <a name="itemproperty"></a> Controls.Item\(Object\) プロパティを使用するコードの更新  
 .NET Framework 3.5 をターゲットとするプロジェクトでは、Microsoft.Office.Tools.Word.Document.Controls コレクションまたは Microsoft.Office.Tools.Excel.Worksheet.Controls コレクションの Item\(Object\) プロパティを使用することにより、指定されたコントロールが文書またはワークシートにあるかどうかを判断できます。  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするでプロジェクトでは、Item\(Object\) プロパティはこれらのコレクションから削除されました。 指定されたコントロールが文書またはワークシートに含まれているかどうかを判断するには、代わりに <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> コレクションまたは <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> コレクションの Contains\(System.Object\) メソッドを使用します。  
  
 文書またはワークシートの Controls コレクションについて詳しくは、「[実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)」をご覧ください。  
  
##  <a name="collections"></a> CollectionBase から派生するコレクションを使用するコードの更新  
 .NET Framework 3.5 をターゲットとするプロジェクトでは、Microsoft.Office.Tools.SmartTagCollection、Microsoft.Office.Tools.Excel.ControlCollection、Microsoft.Office.Tools.Word.ControlCollection など、[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] のいくつかのコレクション型が <xref:System.Collections.CollectionBase> クラスから派生します。  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以降をターゲットとするプロジェクトでは、これらのコレクション型はインターフェイスであり、<xref:System.Collections.CollectionBase> からは派生しません。<xref:System.Collections.CollectionBase.Capacity%2A>、<xref:System.Collections.CollectionBase.List%2A>、<xref:System.Collections.CollectionBase.InnerList%2A> などの一部のメンバーは、これらのコレクション型で使用できなくなりました。  
  
## 参照  
 [.NET Framework 4 以降への Office ソリューションの移行](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [コンテンツ コントロール](../vsto/content-controls.md)   
 [VSTO アドインにおける実行時の Word 文書と Excel ブックの拡張](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [実行時の Office ドキュメントへのコントロールの追加](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)  
  
  