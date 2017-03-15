---
title: "FileName で指定されたファイルは、正しい XML ファイルではありません | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# FileName で指定されたファイルは、正しい XML ファイルではありません
指定したファイル名は、正しい XML ファイルではありません。 XML ドキュメントの許可されている構造体とコンテンツを指定する場合、ドキュメント型定義 \(DTD\)、Microsoft XML\-Data Reduced \(XDR\) スキーマ、または XML スキーマ定義言語 \(XSD\) スキーマを使用できます。[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] で XML 文法を指定する場合は、XSD スキーマをお勧めします。  
  
> [!NOTE]
>  Visual Studio の以前のバージョンにある **XML デザイナー**とは、型指定されたデータセットおよび XML スキーマのデザイナーのことです。**XML デザイナー**は、XML スキーマ ファイルの作成と編集に今も使用できます。 ただし、[!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] では、型指定されたデータセットの作成と編集用のデザイナーは、**データセット デザイナー**です。 詳細については、「[型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)」を参照してください。  
  
### このエラーを解決するには  
  
-   正しいファイル名を指定していることを確認します。  
  
-   確認する必要のある XML ファイルを **XML デザイナー**に読み込んで、指定したファイルに正しい XML が含まれていることを確認します。**\[XML\]** メニューで、**\[XML の整合性チェック\]** をクリックします。 エラーは **\[タスク一覧\]** に表示されます。  
  
-   XML ファイルに関連付けられた XML スキーマがある場合は、定義された構造体にその要素が出現し、個々の要素のコンテンツがスキーマで指定された宣言されたデータ型に準拠していることを確認します。  
  
## 参照  
 <xref:System.Xml>   
 [方法 : ファイル パスを解析する](../Topic/How%20to:%20Parse%20File%20Paths%20in%20Visual%20Basic.md)