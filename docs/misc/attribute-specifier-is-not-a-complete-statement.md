---
title: "属性指定子が完全なステートメントではありません | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32035"
  - "bc32035"
helpviewer_keywords: 
  - "BC32035"
ms.assetid: a0ddd673-4170-4bea-9c22-777d7bf21dfd
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 属性指定子が完全なステートメントではありません
属性指定子が完全なステートメントではありません。 次のステートメントに属性を適用するには、行連結文字を使用します。  
  
 属性ブロックは、ソース コード行に単独で表示されます。 属性は、宣言ステートメントの先頭で適用する必要があり、そのステートメントの一部である必要があります。  
  
 **エラー ID:** BC32035  
  
### このエラーを解決するには  
  
-   宣言ステートメントが次の行にある場合は、属性ブロックの後にスペースとアンダースコア \(`_`\) を追加して、ソース コード行を結合します。  
  
-   宣言ステートメントが属性ブロックに関連付けられていない場合は、いずれかを指定するか、属性ブロックを削除します。  
  
-   属性がアセンブリ全体または現在のアセンブリ モジュールに適用される場合、属性ブロックは、別のソース コード行に残ります。 山かっこ \(`< >`\) で囲まれた属性名の前に `Assembly:` または `Module:` を指定します。属性ブロックの後にスペースまたはアンダー スコア追加しないでください。 また、この属性ブロックをソース ファイルの先頭に配置してください。  
  
## 参照  
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [方法 : コード内でステートメントを分割および連結する](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)