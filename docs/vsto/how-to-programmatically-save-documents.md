---
title: '方法: プログラムによってドキュメントを保存します。'
ms.date: 02/02/2017
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
ms.openlocfilehash: 99a50ec83d69217d123d11aa83ff02600b82108c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53821595"
---
# <a name="how-to-programmatically-save-documents"></a>方法: プログラムによってドキュメントを保存します。
  Microsoft Office Word 文書を保存するいくつかの方法はあります。 ドキュメントを保存するには、ドキュメントの名前を変更することがなく、または新しい名前を持つ文書を保存することができます。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="save-a-document-without-changing-the-name"></a>名前を変更することがなく、ドキュメントを保存します。  
  
### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>ドキュメント レベルのカスタマイズに関連付けられているドキュメントを保存するには  
  
1.  <xref:Microsoft.Office.Tools.Word.Document.Save%2A> クラスの <xref:Microsoft.Office.Tools.Word.Document> メソッドを呼び出します。 このコード例を使用するには、プロジェクトの `ThisDocument` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]  
  
### <a name="to-save-the-active-document"></a>アクティブ文書を保存するには  
  
1. 呼び出す、<xref:Microsoft.Office.Interop.Word._Document.Save%2A>アクティブなドキュメントのメソッド。 このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスからコードを実行します。  
  
    [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
    [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]  
  
   かどうかを保存するドキュメントは、アクティブなドキュメントがわからない場合、その名前でを参照できます。  
  
### <a name="to-save-a-document-specified-by-name"></a>名前で指定されたドキュメントを保存するには  
  
1.  引数として文書名を使用して、<xref:Microsoft.Office.Interop.Word.Documents>コレクション。 このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスからコードを実行します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]  
  
## <a name="save-a-document-with-a-new-name"></a>新しい名前を持つドキュメントを保存します。  
 新しい名前を持つドキュメントを保存するのにには、SaveAs メソッドを使用します。 このメソッドを使用することができます、<xref:Microsoft.Office.Tools.Word.Document>またはネイティブのドキュメント レベルの Word プロジェクトでホスト項目<xref:Microsoft.Office.Interop.Word.Document>すべての Word プロジェクトでのオブジェクト。 このメソッドは、その他の引数は省略可能ですが、新しいファイル名を指定する必要があります。  
  
> [!NOTE]  
>  表示する場合、 **SaveAs**  ダイアログ ボックスの内側、<xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>イベント ハンドラーの`ThisDocument`設定と、*キャンセル*パラメーターを**false**アプリケーションの可能性があります予期せず終了します。 設定した場合、*キャンセル*パラメーターを**true**、自動保存が無効になっていることを示すエラー メッセージが表示されます。  
  
### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>新しい名前でドキュメント レベルのカスタマイズに関連付けられているドキュメントを保存するには  
  
1.  呼び出す、<xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A>のメソッド、`ThisDocument`完全修飾パスとファイル名を使用して、プロジェクト内のクラス。 指定した名前のファイルが既に対象のフォルダー内に存在する場合、そのファイルは警告なしで上書きされます。 このコード例を使用するには、 `ThisDocument` クラスからコードを実行します。  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A>ターゲット ディレクトリが存在しない場合、またはファイルを保存する他の問題がある場合、メソッドが例外をスローします。 使用することをお勧め、 **try… catch**ブロックの周囲、<xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A>メソッドまたは呼び出し元のメソッド内で。  
  
     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]  
  
### <a name="to-save-a-native-document-with-a-new-name"></a>新しい名前を持つネイティブのドキュメントを保存するには  
  
1.  呼び出す、<xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>のメソッド、<xref:Microsoft.Office.Interop.Word.Document>完全修飾パスとファイル名を使用して、保存します。 指定した名前のファイルが既に対象のフォルダー内に存在する場合、そのファイルは警告なしで上書きされます。  
  
     次のコード例では、新しい名前で、アクティブなドキュメントを保存します。 このコード例を使用するには、プロジェクトの `ThisDocument` クラスまたは `ThisAddIn` クラスからコードを実行します。  
  
    > [!NOTE]  
    >  <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>ターゲット ディレクトリが存在しない場合、またはファイルを保存する他の問題がある場合、メソッドが例外をスローします。 使用することをお勧め、 **try… catch**ブロックの周囲、<xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A>メソッドまたは呼び出し元のメソッド内で。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]  
  
## <a name="compile-the-code"></a>コードのコンパイル  
 このコード例で必要な要素は次のとおりです。  
  
-   名前でドキュメントを保存するという名前の文書*NewDocument.doc*という名前のディレクトリに存在する必要があります*テスト*失われます。  
  
-   新しい名前を持つドキュメントを保存するという名前のディレクトリ*テスト*C ドライブ上に存在する必要があります  
  
## <a name="see-also"></a>関連項目  
 [方法: プログラムによって文書を閉じる](../vsto/how-to-programmatically-close-documents.md)   
 [方法: プログラムによって既存文書を開く](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Document ホスト項目](../vsto/document-host-item.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
