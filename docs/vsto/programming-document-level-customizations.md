---
title: "ドキュメント レベルのカスタマイズのプログラミング |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Sheet3
- thisWorkbook
- thisDocument
- Sheet1
- Sheet2
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ThisDocument class
- Sheet3 class
- ThisWorkbook class
- writing code for Office solutions
- programming [Office development in Visual Studio], document-level customizations
- Sheet1 class
- Office applications [Office development in Visual Studio], document-level customizations
- Sheet2 class
- document-level customizations [Office development in Visual Studio], programming
- application development [Office development in Visual Studio], document-level customizations
ms.assetid: 6c421055-7bea-4db4-a4c9-539b8c78d4ee
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 68d0cfbc96b72208eee26f3cc75dd9a19d1b63fc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="programming-document-level-customizations"></a>ドキュメント レベルのカスタマイズのプログラミング
  ドキュメント レベルのカスタマイズを使用して、Microsoft Office Word または Microsoft Office Excel を拡張する場合に、次のタスクを実行できます。  
  
-   オブジェクト モデルを使用してアプリケーションを自動化します。  
  
-   ドキュメントの画面にコントロールを追加します。  
  
-   カスタマイズ アセンブリから、ドキュメント内に Visual Basic for Applications (VBA) コードを呼び出します。  
  
-   VBA からカスタマイズ アセンブリ内のコードを呼び出します。  
  
-   Microsoft Office がインストールされていないサーバー上にドキュメントがあるときに、そのドキュメントの特定の要素を管理します。  
  
-   アプリケーションのユーザー インターフェイス (UI) をカスタマイズします。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 ドキュメント レベルのプロジェクトのコードの記述には、Visual Studio の他のプロジェクトの種類とは異なる点があります。 相違点の多くは、Office オブジェクト モデルがマネージ コードに公開される方法に起因しています。 詳細については、「 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)」を参照してください。  
  
 Visual Studio での Office 開発ツールを使用して作成できるドキュメント レベルのカスタマイズとソリューションの他の種類に関する全般については、次を参照してください。 [Office ソリューション開発の概要 &#40;です。VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## <a name="using-the-generated-classes-in-document-level-projects"></a>ドキュメント レベルのプロジェクトで生成されるクラスの使用  
 ドキュメント レベルのプロジェクトを作成するときに、Visual Studio は、コードの記述を開始できるプロジェクト クラスを自動的に生成します。 Visual Studio は、Word と Excel 用のさまざまなクラスを生成します。  
  
-   Word 用のドキュメント レベルのプロジェクトでは、クラスは既定で `ThisDocument` と呼ばれます。  
  
-   Excel 用のドキュメント レベルのプロジェクトには、生成されたクラスが複数あり、ワークブック自体のために 1 つ、各ワークシート用に 1 つずつです。 既定では、それらのクラスの名前は次のようになります。  
  
    -   `ThisWorkbook`  
  
    -   `Sheet1`  
  
    -   `Sheet2`  
  
    -   `Sheet3`  
  
 生成されたクラスには、ドキュメントを開いたり閉じたりしたときに呼び出されるイベント ハンドラーが含まれています。 ドキュメントを開いたときにコードを実行するには、 `Startup` イベント ハンドラーにコードを追加します。 ドキュメントを閉じたときにコードを実行するには、 `Shutdown` イベント ハンドラーにコードを追加します。 詳細については、「 [Events in Office Projects](../vsto/events-in-office-projects.md)」を参照してください。  
  
### <a name="understanding-the-design-of-the-generated-classes"></a>生成されたクラスの設計について  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]を対象とするプロジェクトでは、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] のホスト項目の種類はインターフェイスなので、生成されたクラスがそこから実装を派生させることはできません。 代わりに、生成されたクラスでは、次の基本クラスからそのほとんどのメンバーが派生します。  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>から派生します。  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>から派生します。  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.WorksheetBase>から派生します。  
  
 これらの基本クラスは、そのメンバーのすべての呼び出しを [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]の対応するホスト項目インターフェイスの内部実装にリダイレクトします。 たとえば、 <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> クラスの `ThisDocument` メソッドを呼び出す場合、 <xref:Microsoft.Office.Tools.Word.DocumentBase> クラスはこの呼び出しを <xref:Microsoft.Office.Tools.Word.Document> の [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]インターフェイスの内部実装にリダイレクトします。  
  
## <a name="accessing-the-object-model-of-the-host-application"></a>ホスト アプリケーションのオブジェクト モデルにアクセスする  
 ホスト アプリケーションのオブジェクト モデルにアクセスするには、プロジェクト内で生成されたクラスのメンバーを使用します。 これらの各クラスは Excel または Word のオブジェクト モデル内のオブジェクトに対応しており、同じプロパティ、メソッド、およびイベントのほとんどが含まれています。 たとえば、Word のドキュメント レベルのプロジェクトの `ThisDocument` クラスは、Word オブジェクト モデルの <xref:Microsoft.Office.Interop.Word.Document> オブジェクトとほとんど同じメンバーを提供します。  
  
 次のコード例では、Word オブジェクト モデルを使用して、Word のドキュメント レベルのカスタマイズの一部であるドキュメントを保存する方法を示します。 この例は `ThisDocument` クラスから実行することを意図しています。  
  
```vb  
Me.Save()  
```  
  
```csharp  
this.Save();  
```  
  
 同じ処理を `ThisDocument` クラスの外から行うには、 `Globals` オブジェクトを使用して `ThisDocument` クラスにアクセスします。 たとえば、[操作] ウィンドウ UI に **[保存]** ボタンUI を組み込む場合は、このコードを [操作] ウィンドウのコード ファイルに追加します。  
  
```vb  
Globals.ThisDocument.Save()  
```  
  
```csharp  
Globals.ThisDocument.Save();  
```  
  
 `ThisDocument` クラスはそのほとんどのメンバーを <xref:Microsoft.Office.Tools.Word.Document> ホストの項目から取得するので、実際には、このコードで呼び出される `Save` メソッドは <xref:Microsoft.Office.Tools.Word.Document.Save%2A> ホスト項目の <xref:Microsoft.Office.Tools.Word.Document> メソッドです。 このメソッドは、Word オブジェクト モデルの <xref:Microsoft.Office.Interop.Word._Document.Save%2A> オブジェクトの <xref:Microsoft.Office.Interop.Word.Document> メソッドに対応しています。  
  
 Word と Excel のオブジェクト モデルの使用方法の詳細については、「 [Word Object Model Overview](../vsto/word-object-model-overview.md) 」および「 [Excel Object Model Overview](../vsto/excel-object-model-overview.md)」を参照してください。  
  
 詳細については、`Globals`オブジェクトを参照してください[Office プロジェクト内のオブジェクトへのグローバル アクセス](../vsto/global-access-to-objects-in-office-projects.md)です。  
  
## <a name="adding-controls-to-documents"></a>ドキュメントへのコントロールの追加  
 ドキュメントの UI をカスタマイズするには、Windows フォーム コントロールまたは *ホスト コントロール* をドキュメントの画面に追加します。 さまざまな種類のコントロールを組み合わせ、コードを記述することによって、コントロールのデータへのバインド、ユーザー情報の収集、およびユーザーの操作への応答を実行できます。  
  
 ホスト コントロールは Word オブジェクト モデルと Excel オブジェクト モデルの一部のオブジェクトを拡張するクラスです。 たとえば、 <xref:Microsoft.Office.Tools.Excel.ListObject> ホスト コントロールには、Excel の <xref:Microsoft.Office.Interop.Excel.ListObject> のすべての機能が用意されています。 ただし、 <xref:Microsoft.Office.Tools.Excel.ListObject> ホスト コントロールには追加のイベントやデータ バインディング機能もあります。  
  
 詳細については、 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md) および [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md)を参照してください。  
  
## <a name="combining-vba-and-document-level-customizations"></a>VBA とドキュメント レベルのカスタマイズの結合  
 ドキュメント レベルのカスタマイズの一部であるドキュメントに VBA コードを使用できます。 カスタマイズ アセンブリからドキュメント内の VBA コードを呼び出したり、ドキュメント内の VBA コードがカスタマイズ アセンブリのコードを呼び出せるようにプロジェクトを構成したりすることができます。  
  
 詳細については、「 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)」を参照してください。  
  
## <a name="managing-documents-on-a-server"></a>サーバー上のドキュメントの管理  
 Microsoft Office Word または Microsoft Office Excel がインストールされていないサーバーで、ドキュメント レベルのカスタマイズのさまざまな要素を管理することができます。 たとえば、ドキュメントのデータ キャッシュにあるデータにアクセスし、変更することができます。 また、ドキュメントに関連付けられているカスタマイズ アセンブリも管理できます。 たとえば、プログラムを使用してドキュメントからアセンブリを削除して、ドキュメントがコードを実行しないようにしたり、プログラムを使用してアセンブリをドキュメントにアタッチすることができます。  
  
 詳細については、「 [Managing Documents on a Server by Using the ServerDocument Class](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)」を参照してください。  
  
## <a name="customizing-the-user-interface-of-microsoft-office-applications"></a>Microsoft Office アプリケーションのユーザー インターフェイスをカスタマイズする  
 ドキュメント レベルのカスタマイズを使用して、次の方法で、Excel や Word の UI をカスタマイズできます。  
  
-   ホスト コントロールまたは Windows フォーム コントロールをドキュメントの画面に追加します。  
  
     詳細については、「 [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md)「 [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)および「 [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md)」を参照してください。  
  
-   文書に操作ウィンドウを追加する。  
  
     詳細については、「 [Actions Pane Overview](../vsto/actions-pane-overview.md)」を参照してください。  
  
-   リボンにカスタム タブを追加します。  
  
     詳細については、次を参照してください。[リボンの概要](../vsto/ribbon-overview.md)です。  
  
-   リボン上の組み込みタブにカスタム グループを追加します。  
  
     詳細については、「 [How to: Customize a Built-in Tab](../vsto/how-to-customize-a-built-in-tab.md)」を参照してください。  
  
 詳細については、Microsoft Office アプリケーションの UI をカスタマイズする、次を参照してください。 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)です。  
  
## <a name="getting-extended-objects-from-native-office-objects-in-document-level-customizations"></a>ドキュメント レベルのカスタマイズでのネイティブの Office オブジェクトからの拡張オブジェクトの取得  
 Office イベントの多くのイベント ハンドラーでは、イベントが発生するワークブック、ワークシート、またはドキュメントを表すネイティブの Office オブジェクトを受け取ります。 場合によっては、いくつかのコードはドキュメント レベルのカスタマイズでワークブックやドキュメントによってイベントが発生した場合のみ実行します。 たとえば、Excel のドキュメント レベルのカスタマイズでは、カスタマイズされたワークブック内でワークシートを 1 つアクティブ化したときに一部のコードを実行し、同時に開いている他のワークブックでワークシートをアクティブ化したときには実行しないようにします。  
  
 ネイティブの Office オブジェクトがある場合は、そのオブジェクトがドキュメント レベルのカスタマイズで *ホスト項目* または *ホスト コントロール* に拡張されているかどうかをテストできます。 ホスト項目とホスト コントロールは、Word または Excel オブジェクト モデルにネイティブで存在するオブジェクト ( [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ネイティブの Office オブジェクト *) に機能を追加する*が提供する種類のインスタンスです。 総称して、ホスト項目とホスト コントロールは *拡張オブジェクト*とも呼ばれます。 ホスト項目とホスト コントロールの詳細については、「 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
## <a name="understanding-the-getvstoobject-and-hasvstoobject-methods"></a>GetVstoObject メソッドと HasVstoObject メソッドの理解  
 ネイティブな Office オブジェクトをテストするには、プロジェクトで HasVstoObject と GetVstoObject メソッドを使用します。  
  
-   HasVstoObject メソッドを使用して、カスタマイズ、拡張オブジェクトをネイティブな Office オブジェクトがあるかどうかを判断する場合。 このメソッドは、ネイティブの Office オブジェクトに拡張オブジェクトがある場合は **true** を返し、ない場合は **false** を返します。  
  
-   GetVstoObject メソッドは、ネイティブ Office オブジェクトに対して拡張オブジェクトを取得する場合に使用します。 このメソッドは、指定したネイティブの Office オブジェクトに拡張オブジェクトがあれば、 <xref:Microsoft.Office.Tools.Excel.ListObject>、 <xref:Microsoft.Office.Tools.Excel.Workbook>、 <xref:Microsoft.Office.Tools.Excel.Worksheet>、または <xref:Microsoft.Office.Tools.Word.Document> オブジェクトを返します。 Getvstoobject メソッドを返しますそれ以外の場合、 **null**です。 たとえば、GetVstoObject メソッドが返されます、<xref:Microsoft.Office.Tools.Word.Document>場合、指定した<xref:Microsoft.Office.Interop.Word.Document>Word ドキュメント プロジェクトのドキュメントの基になるオブジェクトです。  
  
 ドキュメント レベルのプロジェクトでは、新しい GetVstoObject メソッドを使うことはできません<xref:Microsoft.Office.Tools.Excel.Workbook>、 <xref:Microsoft.Office.Tools.Excel.Worksheet>、または<xref:Microsoft.Office.Tools.Word.Document>ホスト項目を実行時にします。 このメソッドは、デザイン時にプロジェクトで生成される既存のホスト項目へのアクセスにのみ使用できます。 実行時に新しいホスト項目を作成する場合は、VSTO アドイン プロジェクトを開発する必要があります。 詳細については、次のトピックを参照してください。 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) および [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="using-the-getvstoobject-and-hasvstoobject-methods"></a>GetVstoObject メソッドと HasVstoObject メソッドの使用  
 HasVstoObject と GetVstoObject メソッドを呼び出すには、Globals.Factory.GetVstoObject または Globals.Factory.HasVstoObject メソッドを使用し、ネイティブの Word または Excel オブジェクトを渡す (など、<xref:Microsoft.Office.Interop.Word.Document>または<xref:Microsoft.Office.Interop.Excel.Worksheet>) テストを実行します。  
  
## <a name="see-also"></a>参照  
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [ServerDocument クラスを使用してサーバー上のドキュメントを管理します。](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)  
  
  