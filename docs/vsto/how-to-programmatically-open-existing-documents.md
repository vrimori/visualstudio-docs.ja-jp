---
title: "方法: プログラムによって既存文書を開く | Microsoft Docs"
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
  - "ドキュメント [Visual Studio での Office 開発], 開く"
  - "Word [Visual Studio での Office 開発], 開く (文書を)"
ms.assetid: 08f7fe4b-d96d-4a0c-b32a-aa7fd7992316
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 方法: プログラムによって既存文書を開く
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> メソッドは、絶対パスとファイル名で指定した既存の Microsoft Office Word 文書を開きます。  このメソッドは、開かれたドキュメントを表す <xref:Microsoft.Office.Interop.Word.Document> を返します。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### 文書を開くには  
  
-   <xref:Microsoft.Office.Interop.Word.Documents> コレクションの <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> メソッドを呼び出し、文書へのパスを指定します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_VstcoreWordAutomation#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#5)]  
  
### 文書を読み取り専用で開くには  
  
-   <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> メソッドを呼び出し、文書へのパスを指定し、メソッドの呼び出しの中で *ReadOnly* 引数を **True** に設定します。  
  
     [!code-csharp[Trin_VstcoreWordAutomation#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreWordAutomation#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#6)]  
  
## コードのコンパイル  
 このコード例に必要な条件は次のとおりです。  
  
-   NewDocument.doc という名前の文書が、ドライブ C の Test ディレクトリに存在する。  
  
## 参照  
 [方法: プログラムによって新しい文書を作成する](../vsto/how-to-programmatically-create-new-documents.md)   
 [方法: プログラムによって文書を閉じる](../vsto/how-to-programmatically-close-documents.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  