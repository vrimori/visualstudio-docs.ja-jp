---
title: "方法 : データセットを XML として保存する | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データ [Visual Studio], 保存 (XML として)"
  - "データセット [Visual Basic], 保存 (XML として)"
  - "保存 (データを)"
  - "XML [Visual Basic], データセット"
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 方法 : データセットを XML として保存する
データセットの XML データには、データセットで使用できる XML メソッドを呼び出してアクセスできます。  データを XML 形式で保存する場合は、<xref:System.Data.DataSet> の <xref:System.Data.DataSet.GetXml%2A> メソッドまたは <xref:System.Data.DataSet.WriteXml%2A> メソッドを呼び出します。  
  
 <xref:System.Data.DataSet.GetXml%2A> メソッドを呼び出すと、データセットのすべてのデータ テーブルのデータを含む文字列が XML 形式で返されます。  
  
 <xref:System.Data.DataSet.WriteXml%2A> メソッドを呼び出すと、指定したファイルに XML 形式のデータが送信されます。  
  
### データセットのデータを XML 形式で変数に保存するには  
  
-   <xref:System.Data.DataSet.GetXml%2A> メソッドは <xref:System.String> を返すため、<xref:System.String> 型の変数を宣言し、<xref:System.Data.DataSet.GetXml%2A> メソッドの結果を代入します。  
  
     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-cs[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]  
  
### データセットのデータを XML 形式でファイルに保存するには  
  
-   <xref:System.Data.DataSet.WriteXml%2A> メソッドには、いくつかのオーバーロードがあります。  次のコードに、変数を宣言してからファイルを保存する有効なパスを代入してデータをファイルに保存する方法を示します。  
  
     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-cs[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]  
  
## 参照  
 [DataSets、DataTables、および DataViews](../Topic/DataSets,%20DataTables,%20and%20DataViews.md)   
 [Visual Studio の XML ツール](../xml-tools/xml-tools-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)