---
title: ドキュメント レベルのカスタマイズをプログラミングします。
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 512952a27e2b1c22df256e36f8cbea59f04a3295
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692832"
---
# <a name="program-document-level-customizations"></a>ドキュメント レベルのカスタマイズをプログラミングします。
  ドキュメント レベルのカスタマイズを使用して、Microsoft Office Word または Microsoft Office Excel を拡張する場合に、次のタスクを実行できます。  
  
-   オブジェクト モデルを使用してアプリケーションを自動化します。  
  
-   ドキュメントの画面にコントロールを追加します。  
  
-   カスタマイズ アセンブリから、ドキュメント内に Visual Basic for Applications (VBA) コードを呼び出します。  
  
-   VBA からカスタマイズ アセンブリ内のコードを呼び出します。  
  
-   Microsoft Office がインストールされていないサーバー上にドキュメントがあるときに、そのドキュメントの特定の要素を管理します。  
  
-   アプリケーションのユーザー インターフェイス (UI) をカスタマイズします。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 ドキュメント レベルのプロジェクトのコードの記述には、Visual Studio の他のプロジェクトの種類とは異なる点があります。 相違点の多くは、Office オブジェクト モデルがマネージ コードに公開される方法に起因しています。 詳細については、次を参照してください。 [Office ソリューションでコードを記述](../vsto/writing-code-in-office-solutions.md)です。  
  
 Visual Studio での Office 開発ツールを使用して作成できるドキュメント レベルのカスタマイズとソリューションの他の種類に関する全般については、次を参照してください。 [Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)です。  
  
## <a name="use-the-generated-classes-in-document-level-projects"></a>ドキュメント レベルのプロジェクトで生成されたクラスを使用します。  
 ドキュメント レベルのプロジェクトを作成するときに、Visual Studio は、コードの記述を開始できるプロジェクト クラスを自動的に生成します。 Visual Studio は、Word と Excel 用のさまざまなクラスを生成します。  
  
-   Word 用のドキュメント レベルのプロジェクトでは、クラスは既定で `ThisDocument` と呼ばれます。  
  
-   Excel 用のドキュメント レベルのプロジェクトには、生成されたクラスが複数あり、ワークブック自体のために 1 つ、各ワークシート用に 1 つずつです。 既定では、それらのクラスの名前は次のようになります。  
  
    -   `ThisWorkbook`  
  
    -   `Sheet1`  
  
    -   `Sheet2`  
  
    -   `Sheet3`  
  
 生成されたクラスには、ドキュメントを開いたり閉じたりしたときに呼び出されるイベント ハンドラーが含まれています。 ドキュメントを開いたときにコードを実行するには、 `Startup` イベント ハンドラーにコードを追加します。 ドキュメントを閉じたときにコードを実行するには、 `Shutdown` イベント ハンドラーにコードを追加します。 詳細については、次を参照してください。 [Office プロジェクトのイベント](../vsto/events-in-office-projects.md)です。  
  
### <a name="understand-the-design-of-the-generated-classes"></a>生成されたクラスの設計を把握します。  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]を対象とするプロジェクトでは、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] のホスト項目の種類はインターフェイスなので、生成されたクラスがそこから実装を派生させることはできません。 代わりに、生成されたクラスでは、次の基本クラスからそのほとんどのメンバーが派生します。  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>から派生します。  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>から派生します。  
  
-   `Sheet` *n*: から派生した<xref:Microsoft.Office.Tools.Excel.WorksheetBase>です。  
  
 これらの基本クラスは、そのメンバーのすべての呼び出しを [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]の対応するホスト項目インターフェイスの内部実装にリダイレクトします。 たとえば、 <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> クラスの `ThisDocument` メソッドを呼び出す場合、 <xref:Microsoft.Office.Tools.Word.DocumentBase> クラスはこの呼び出しを <xref:Microsoft.Office.Tools.Word.Document> の [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]インターフェイスの内部実装にリダイレクトします。  
  
## <a name="access-the-object-model-of-the-host-application"></a>ホスト アプリケーションのオブジェクト モデルへのアクセスします。  
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
  
 詳細については、Word と Excel のオブジェクト モデルを使用して、次を参照してください。 [Word オブジェクト モデルの概要](../vsto/word-object-model-overview.md)と[Excel オブジェクト モデルの概要](../vsto/excel-object-model-overview.md)です。  
  
 詳細については、`Globals`オブジェクトを参照してください[Office プロジェクト内のオブジェクトへのアクセスをグローバル](../vsto/global-access-to-objects-in-office-projects.md)です。  
  
## <a name="add-controls-to-documents"></a>ドキュメントにコントロールを追加します。  
 ドキュメントの UI をカスタマイズするには、Windows フォーム コントロールまたは *ホスト コントロール* をドキュメントの画面に追加します。 さまざまな種類のコントロールを組み合わせ、コードを記述することによって、コントロールのデータへのバインド、ユーザー情報の収集、およびユーザーの操作への応答を実行できます。  
  
 ホスト コントロールは Word オブジェクト モデルと Excel オブジェクト モデルの一部のオブジェクトを拡張するクラスです。 たとえば、 <xref:Microsoft.Office.Tools.Excel.ListObject> ホスト コントロールには、Excel の <xref:Microsoft.Office.Interop.Excel.ListObject> のすべての機能が用意されています。 ただし、 <xref:Microsoft.Office.Tools.Excel.ListObject> ホスト コントロールには追加のイベントやデータ バインディング機能もあります。  
  
 詳細については、次を参照してください。[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)と[Windows フォームでコントロールの Office ドキュメントの概要](../vsto/windows-forms-controls-on-office-documents-overview.md)です。  
  
## <a name="combine-vba-and-document-level-customizations"></a>VBA とドキュメント レベルのカスタマイズを結合します。  
 ドキュメント レベルのカスタマイズの一部であるドキュメントに VBA コードを使用できます。 カスタマイズ アセンブリからドキュメント内の VBA コードを呼び出したり、ドキュメント内の VBA コードがカスタマイズ アセンブリのコードを呼び出せるようにプロジェクトを構成したりすることができます。  
  
 詳細については、次を参照してください。[結合 VBA とドキュメント レベルのカスタマイズ](../vsto/combining-vba-and-document-level-customizations.md)です。  
  
## <a name="manage-documents-on-a-server"></a>サーバー上のドキュメントを管理します。  
 Microsoft Office Word または Microsoft Office Excel がインストールされていないサーバーで、ドキュメント レベルのカスタマイズのさまざまな要素を管理することができます。 たとえば、ドキュメントのデータ キャッシュにあるデータにアクセスし、変更することができます。 また、ドキュメントに関連付けられているカスタマイズ アセンブリも管理できます。 たとえば、プログラムを使用してドキュメントからアセンブリを削除して、ドキュメントがコードを実行しないようにしたり、プログラムを使用してアセンブリをドキュメントにアタッチすることができます。  
  
 詳細については、次を参照してください。 [ServerDocument クラスを使用して、サーバー上のドキュメントを管理](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)です。  
  
## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Microsoft Office アプリケーションのユーザー インターフェイスをカスタマイズします。  
 ドキュメント レベルのカスタマイズを使用して、次の方法で、Excel や Word の UI をカスタマイズできます。  
  
-   ホスト コントロールまたは Windows フォーム コントロールをドキュメントの画面に追加します。  
  
     詳細については、次を参照してください[拡張オブジェクトを使用して Word を自動化](../vsto/automating-word-by-using-extended-objects.md)、[拡張オブジェクトによる Excel の自動化](../vsto/automating-excel-by-using-extended-objects.md)、および[Windows フォームのコントロールに Office ドキュメントの概要](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
-   文書に操作ウィンドウを追加する。  
  
     詳細については、次を参照してください。[操作ウィンドウの概要](../vsto/actions-pane-overview.md)です。  
  
-   リボンにカスタム タブを追加します。  
  
     詳細については、次を参照してください。[リボンの概要](../vsto/ribbon-overview.md)です。  
  
-   リボン上の組み込みタブにカスタム グループを追加します。  
  
     詳細については、次を参照してください。[する方法: 組み込みタブをカスタマイズする](../vsto/how-to-customize-a-built-in-tab.md)です。  
  
 詳細については、Microsoft Office アプリケーションの UI をカスタマイズする、次を参照してください。 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)です。  
  
## <a name="get-extended-objects-from-native-office-objects-in-document-level-customizations"></a>ドキュメント レベルのカスタマイズでネイティブな Office オブジェクトから拡張オブジェクトを取得します。  
 Office イベントの多くのイベント ハンドラーでは、イベントが発生するワークブック、ワークシート、またはドキュメントを表すネイティブの Office オブジェクトを受け取ります。 場合によっては、いくつかのコードはドキュメント レベルのカスタマイズでワークブックやドキュメントによってイベントが発生した場合のみ実行します。 たとえば、Excel のドキュメント レベルのカスタマイズでは、カスタマイズされたワークブック内でワークシートを 1 つアクティブ化したときに一部のコードを実行し、同時に開いている他のワークブックでワークシートをアクティブ化したときには実行しないようにします。  
  
 ネイティブの Office オブジェクトがある場合は、そのオブジェクトがドキュメント レベルのカスタマイズで *ホスト項目* または *ホスト コントロール* に拡張されているかどうかをテストできます。 ホスト項目とホスト コントロールは、Word または Excel オブジェクト モデルにネイティブで存在するオブジェクト ( [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ネイティブの Office オブジェクト *) に機能を追加する*が提供する種類のインスタンスです。 総称して、ホスト項目とホスト コントロールは *拡張オブジェクト*とも呼ばれます。 ホスト項目とホスト コントロールの詳細については、次を参照してください。[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)です。  
  
## <a name="understand-the-getvstoobject-and-hasvstoobject-methods"></a>Getvstoobject メソッドと HasVstoObject メソッドを理解します。  
 ネイティブな Office オブジェクトをテストするには、使用、`HasVstoObject`と`GetVstoObject`プロジェクト内のメソッド。  
  
-   使用して、`HasVstoObject`メソッド、カスタマイズ、拡張オブジェクトをネイティブな Office オブジェクトがあるかどうかを判断する場合。 このメソッドは、ネイティブの Office オブジェクトに拡張オブジェクトがある場合は **true** を返し、ない場合は **false** を返します。  
  
-   使用して、`GetVstoObject`メソッドの場合は、ネイティブな Office オブジェクトの拡張オブジェクトを取得します。 このメソッドは、指定したネイティブの Office オブジェクトに拡張オブジェクトがあれば、 <xref:Microsoft.Office.Tools.Excel.ListObject>、 <xref:Microsoft.Office.Tools.Excel.Workbook>、 <xref:Microsoft.Office.Tools.Excel.Worksheet>、または <xref:Microsoft.Office.Tools.Word.Document> オブジェクトを返します。 それ以外の場合、`GetVstoObject`返します**null**です。 たとえば、`GetVstoObject`メソッドを返します、<xref:Microsoft.Office.Tools.Word.Document>場合、指定した<xref:Microsoft.Office.Interop.Word.Document>Word ドキュメント プロジェクト内のドキュメントの基になるオブジェクトであります。  
  
 ドキュメント レベルのプロジェクトで使うことはできません、`GetVstoObject`メソッドを作成、新しい<xref:Microsoft.Office.Tools.Excel.Workbook>、 <xref:Microsoft.Office.Tools.Excel.Worksheet>、または<xref:Microsoft.Office.Tools.Word.Document>実行時にホスト項目。 このメソッドは、デザイン時にプロジェクトで生成される既存のホスト項目へのアクセスにのみ使用できます。 実行時に新しいホスト項目を作成する場合は、VSTO アドイン プロジェクトを開発する必要があります。 詳細については、次を参照してください。[ホスト項目とホスト コントロールのプログラム上の制限事項](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)と[拡張 Word 文書と実行時に VSTO アドイン内の Excel ブック](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)です。  
  
## <a name="use-the-getvstoobject-and-hasvstoobject-methods"></a>Getvstoobject メソッドと HasVstoObject メソッドを使用します。  
 呼び出す、`HasVstoObject`と`GetVstoObject`メソッドを使用して、`Globals.Factory.GetVstoObject`または`Globals.Factory.HasVstoObject`メソッド、およびネイティブの Word または Excel オブジェクトを渡します (など、<xref:Microsoft.Office.Interop.Word.Document>または<xref:Microsoft.Office.Interop.Excel.Worksheet>) テストを実行します。  
  
## <a name="see-also"></a>関連項目  
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [VBA とドキュメント レベルのカスタマイズを結合します。](../vsto/combining-vba-and-document-level-customizations.md)   
 [ServerDocument クラスを使用して、サーバー上のドキュメントを管理します。](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Office ソリューションでコードを記述します。](../vsto/writing-code-in-office-solutions.md)  
  
  