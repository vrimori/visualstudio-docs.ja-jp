---
title: '方法: プログラムによって文書を保存 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 89e2a236d8755b764971b7823056edda3e944e65
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-save-documents"></a>方法: プログラムによって文書を保存する
  Microsoft Office Word 文書を保存するいくつかの方法はあります。 ドキュメントを保存するには、ドキュメントの名前を変更することがなくまたは新しい名前を持つドキュメントを保存することができます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="saving-a-document-without-changing-the-name"></a>名前を変更することがなく、ドキュメントの保存  
  
#### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>ドキュメント レベルのカスタマイズに関連付けられているドキュメントを保存するには  
  
1.  <xref:Microsoft.Office.Tools.Word.Document> クラスの <xref:Microsoft.Office.Tools.Word.Document.Save%2A> メソッドを呼び出します。 このコード例を使用するには、プロジェクトの `ThisDocument` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]  
  
#### <a name="to-save-the-active-document"></a>アクティブ文書を保存するには  
  
1.  呼び出す、<xref:Microsoft.Office.Interop.Word._Document.Save%2A>アクティブな文書のメソッドです。 このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
     [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]  
  
 かどうかを保存するドキュメントは、アクティブなドキュメントがわからない場合は、その名前で参照できます。  
  
#### <a name="to-save-a-document-specified-by-name"></a>名前で指定した図面を保存するには  
  
1.  引数として文書名を使用して、<xref:Microsoft.Office.Interop.Word.Documents>コレクション。 このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]  
  
## <a name="saving-a-document-with-a-new-name"></a>新しい名前で、ドキュメントの保存  
 新しい名前を持つドキュメントを保存するのにには、名前を付けて保存メソッドを使用します。 このメソッドを使用することができます、<xref:Microsoft.Office.Tools.Word.Document>またはネイティブのドキュメント レベルの Word プロジェクトでホスト項目<xref:Microsoft.Office.Interop.Word.Document>すべての Word プロジェクトでのオブジェクト。 このメソッドは、新しいファイル名を指定する、他の引数は省略可能なことが必要です。  
  
> [!NOTE]  
>  表示する場合、 **SaveAs**  ダイアログ ボックスの内側、<xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>のイベント ハンドラー`ThisDocument`設定と、*キャンセル*パラメーターを**false**アプリケーションの場合があります予期せず終了します。 設定した場合、*キャンセル*パラメーターを**true**、自動保存が無効になっていることを示すエラー メッセージが表示されます。  
  
#### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>新しい名前を持つドキュメント レベルのカスタマイズに関連付けられているドキュメントを保存するには  
  
1.  呼び出す、<xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A>のメソッド、`ThisDocument`完全修飾パスとファイル名を使用して、プロジェクト内のクラスです。 指定した名前のファイルが既に対象のフォルダー内に存在する場合、そのファイルは警告なしで上書きされます。 このコード例を使用するには、 `ThisDocument` クラスからコードを実行します。  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A>ターゲット ディレクトリが存在しない場合、またはファイルを保存するその他の問題がある場合、メソッドが例外をスローします。 使用することをお勧め、 **try… catch**ブロックの周囲、<xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A>メソッド内または呼び出し元のメソッドです。  
  
     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]  
  
#### <a name="to-save-a-native-document-with-a-new-name"></a>新しい名前を持つネイティブのドキュメントを保存するには  
  
1.  呼び出す、<xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>のメソッド、<xref:Microsoft.Office.Interop.Word.Document>完全修飾パスとファイル名を使用して、保存します。 指定した名前のファイルが既に対象のフォルダー内に存在する場合、そのファイルは警告なしで上書きされます。  
  
     次のコード例では、新しい名前を持つ、アクティブなドキュメントを保存します。 このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスからコードを実行します。  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>ターゲット ディレクトリが存在しない場合、またはファイルを保存するその他の問題がある場合、メソッドが例外をスローします。 使用することをお勧め、 **try… catch**ブロックの周囲、<xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>メソッド内または呼び出し元のメソッドです。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 このコード例で必要な要素は次のとおりです。  
  
-   名前でドキュメントを保存するには、NewDocument.doc をという名前のドキュメントが C ドライブにテストをという名前のディレクトリに存在する必要があります。  
  
-   C ドライブに新しい名前を持つドキュメントを保存するには、テストをという名前のディレクトリが存在する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムによって文書を閉じる](../vsto/how-to-programmatically-close-documents.md)   
 [方法: プログラムによって既存のドキュメントを開く](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Document ホスト項目](../vsto/document-host-item.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  