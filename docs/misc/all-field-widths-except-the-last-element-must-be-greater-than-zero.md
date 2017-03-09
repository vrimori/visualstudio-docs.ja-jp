---
title: "最後の要素以外のすべてのフィールド幅は 0 より大きくなければなりません | Microsoft Docs"
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
  - "vbrTextFieldParser_FieldWidthsMustPositive"
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 最後の要素以外のすべてのフィールド幅は 0 より大きくなければなりません
最後の要素以外のすべてのフィールド幅は 0 より大きくなければなりません。 最後の要素内の 0 以下のフィールド幅は、最後のフィールドが可変長であることを示しています。  
  
 最後の要素以外のフィールド幅が 0 以下に設定されているため、処理に失敗しました。 0 以下のフィールド幅を最後の要素として使用し、最後のフィールドが可変長であることを示すことができますが、他の要素として使用することはできません。  
  
### このエラーを解決するには  
  
-   フィールド幅を正しい長さに設定します。  
  
## 参照  
 [TextFieldParser.SetFieldWidths メソッド](http://msdn.microsoft.com/ja-jp/958fed9f-e0f3-4fc5-83b4-386156bdf036)   
 [TextFieldParser.FieldWidths プロパティ](http://msdn.microsoft.com/ja-jp/c6985360-60c6-494e-89e7-43b6b73f2597)   
 [How to: Read From Fixed\-width Text Files](../Topic/How%20to:%20Read%20From%20Fixed-width%20Text%20Files%20in%20Visual%20Basic.md)   
 [TextFieldParser Object](/dotnet/visual-basic/language-reference/objects/textfieldparser-object)