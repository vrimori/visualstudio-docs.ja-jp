---
title: "NumberOfChars は 0 より大きくなければなりません。 | Microsoft Docs"
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
  - "vbrTextFieldParser_NumberOfCharsMustBePositive"
ms.assetid: 3eea4bbf-cd49-4d19-adfb-0e2adf087065
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# NumberOfChars は 0 より大きくなければなりません。
`TextFieldParser` オブジェクトの `PeekChars` メソッドを使用する場合、`0` よりも大きい `NumberOfChars` 値を指定する必要があります。  
  
### このエラーを解決するには  
  
-   `NumberOfChars` を `0` よりも大きい値に変更します。  
  
## 参照  
 [How to: Read From Text Files with Multiple Formats](../Topic/How%20to:%20Read%20From%20Text%20Files%20with%20Multiple%20Formats%20in%20Visual%20Basic.md)   
 [My.Computer.FileSystem.OpenTextFieldParser メソッド](http://msdn.microsoft.com/ja-jp/e5869f85-c078-485f-8323-8dc716494546)   
 [TextFieldParser.PeekChars メソッド](http://msdn.microsoft.com/ja-jp/4a180d26-d46d-4cc1-9af7-d23abe27c89b)   
 [Parsing Text Files with the TextFieldParser Object](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object)   
 [TextFieldParser Object](/dotnet/visual-basic/language-reference/objects/textfieldparser-object)