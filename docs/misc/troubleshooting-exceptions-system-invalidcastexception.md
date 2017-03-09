---
title: "例外のトラブルシューティング : System.InvalidCastException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "InvalidCastException クラス"
ms.assetid: a855dfe1-5c06-45a6-9c2f-c9e799ccf8f0
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.InvalidCastException
<xref:System.InvalidCastException> 例外は、明示的な参照変換でエラーが発生するとスローされます。 参照変換とは、ある参照型から別の参照型への変換をいいます。 参照変換では、参照の型は変更されますが、変換対象の型や値は変更されません。 ある型から別の型にオブジェクトをキャストすると、この例外が頻繁に発生します。  
  
## 関連するヒント  
 **変換元と変換先の型をチェックして、変換が有効であることを確認します。**  
 システムがサポートする変換については、<xref:System.Convert> を参照してください。  
  
## コメント  
 明示的な参照変換を正常に実行するには、変換元の値が Null \(Visual Basic では `Nothing`\) であるか、変換元の引数が参照するオブジェクト型を暗黙の参照変換によって変換先の型に変換できることが必要です。  
  
 カスタム イベントの呼び出しをユーザー コントロール内に含む Visual Basic 6.0 アプリケーションを新しいバージョンの Visual Basic にアップグレードして実行すると、この例外が発生し、"指定されたキャストは有効ではありません。" という追加情報が表示されることがあります。 このエラーを修正するには、 `Form1` で次のコード行を見つけます。  
  
 `Call UserControl11_MyCustomEvent(UserControl11, New UserControl1.MyCustomEventEventArgs(5))`  
  
 これを、次のコード行に置き換えます。  
  
 `Call UserControl11_MyCustomEvent(UserControl11(0), New UserControl1.MyCustomEventEventArgs(5))`  
  
## 参照  
 <xref:System.InvalidCastException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Convert an Object to Another Type in Visual Basic](../Topic/How%20to:%20Convert%20an%20Object%20to%20Another%20Type%20in%20Visual%20Basic.md)   
 [文字列の .NET Framework データ型への変換](../Topic/Converting%20Strings%20to%20.NET%20Framework%20Data%20Types.md)   
 [方法 : 構造体間にユーザー定義の変換を実装する](../Topic/How%20to:%20Implement%20User-Defined%20Conversions%20Between%20Structs%20\(C%23%20Programming%20Guide\).md)