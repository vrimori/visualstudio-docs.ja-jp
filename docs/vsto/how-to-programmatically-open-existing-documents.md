---
title: "方法: プログラムによって既存のドキュメントを開く |Microsoft ドキュメント"
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
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
ms.assetid: 08f7fe4b-d96d-4a0c-b32a-aa7fd7992316
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 991a282cb3fc8a34f3434c9cdb0a9be214c9e3bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-open-existing-documents"></a>方法: プログラムによって既存文書を開く
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>メソッドは、完全修飾パスとファイル名で指定された既存の Microsoft Office Word ドキュメントを開きます。 このメソッドが戻る、<xref:Microsoft.Office.Interop.Word.Document>開かれたドキュメントを表すです。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-open-a-document"></a>ドキュメントを開く  
  
-   呼び出す、<xref:Microsoft.Office.Interop.Word.Documents.Open%2A>のメソッド、<xref:Microsoft.Office.Interop.Word.Documents>コレクションをドキュメントへのパスを指定します。  
  
     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]  
  
### <a name="to-open-a-document-as-read-only"></a>読み取り専用とドキュメントを開く  
  
-   呼び出す、<xref:Microsoft.Office.Interop.Word.Documents.Open%2A>メソッドは、ドキュメントへのパスを指定し、設定、 *ReadOnly*に渡す引数**True**メソッドの呼び出しで。  
  
     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 このコード例で必要な要素は次のとおりです。  
  
-   NewDocument.doc をという名前のドキュメントが C ドライブにテストをという名前のディレクトリに存在する必要があります。  
  
## <a name="see-also"></a>参照  
 [方法: プログラムによって新しいドキュメントを作成します。](../vsto/how-to-programmatically-create-new-documents.md)   
 [方法: プログラムによって文書を閉じる](../vsto/how-to-programmatically-close-documents.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  