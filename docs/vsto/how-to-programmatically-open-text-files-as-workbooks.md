---
title: "方法: プログラムによってテキスト ファイルをブックとして開く"
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
  - "テキスト [Visual Studio での Office 開発], テキスト ファイル"
  - "テキスト ファイル, 開く (ブックとして)"
  - "ブック, 開く (テキスト ファイルを)"
ms.assetid: 056ae3d0-7fe7-4c28-a2a5-5a948baee0e6
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 方法: プログラムによってテキスト ファイルをブックとして開く
  テキスト ファイルをブックとして開くことができます。  開くテキスト ファイルの名前を渡す必要があります。  解析を開始する行番号やファイル内のデータの列形式などを、さまざまな省略可能なパラメーターで指定できます。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## 使用例  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#80)]  
  
## コードのコンパイル  
 この例では、次のコンポーネントが必要です。  
  
-   3 行以上のテキストから成る、`Test.txt` という名前のコンマ区切りのテキスト ファイル。  
  
-   テキスト ファイル `Test.txt` がドライブ C に格納されている。  
  
## 参照  
 [ブックの操作](../vsto/working-with-workbooks.md)   
 [方法: プログラムによってブックを開く](../vsto/how-to-programmatically-open-workbooks.md)   
 [方法: プログラムによって新しいブックを作成する](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [方法: プログラムによってブックを保存する](../vsto/how-to-programmatically-save-workbooks.md)   
 [方法: プログラムによってブックを閉じる](../vsto/how-to-programmatically-close-workbooks.md)   
 [Office ソリューションの省略可能なパラメーター](../vsto/optional-parameters-in-office-solutions.md)  
  
  