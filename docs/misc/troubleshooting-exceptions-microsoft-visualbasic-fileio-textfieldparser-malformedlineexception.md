---
title: "例外のトラブルシューティング : Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Microsoft.VisualStudio.Tools.Applications.Runtime.ControlNotFoundException 例外"
ms.assetid: d780b8cc-c3f1-45ed-8f8e-3f8728a4b770
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException
<xref:Microsoft.VisualBasic.FileIO.MalformedLineException> 例外は、<xref:Microsoft.VisualBasic.FileIO.TextFieldParser> で指定の形式を使用して行を解析できないときにスローされます。  
  
 例外オブジェクトの `Error Line` プロパティには、エラーが発生した行のテキストが含まれます。  
  
## 関連するヒント  
 **TextFieldType および区切り記号が適切に定義されていることを確認します。**  
 `TextFieldType` \("Delimited" または "FixedWidth"\) は、ファイルの形式に一致する必要があります。`TextFieldType` が `FixedWidth` の場合、`FieldWidths` プロパティが正しく設定されていることを確認します。`TextFieldType` が `Delimited` の場合、`Delimiters` プロパティが正しく設定されていることを確認します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>   
 [Parsing Text Files with the TextFieldParser Object](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object)   
 [How to: Read From Comma\-Delimited Text Files](../Topic/How%20to:%20Read%20From%20Comma-Delimited%20Text%20Files%20in%20Visual%20Basic.md)   
 [How to: Read From Fixed\-width Text Files](../Topic/How%20to:%20Read%20From%20Fixed-width%20Text%20Files%20in%20Visual%20Basic.md)