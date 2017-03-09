---
title: "例外のトラブルシューティング : System.ArgumentOutOfRangeException | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
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
  - "ArgumentOutOfRangeException クラス"
ms.assetid: f53c58d9-7c4e-407f-93d3-1e59d90d98f5
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.ArgumentOutOfRangeException
<xref:System.ArgumentOutOfRangeException> は、メソッドが呼び出されたとき、そのメソッドに渡された引数の 1 つ以上が null 参照 \(Visual Basic では `Nothing`\) ではなく、かつ有効値を含まない場合にスローされます。  
  
## 関連するヒント  
 **このメソッドのすべての引数が、呼び出されたメソッドで定義された有効値を持つことを確認します。**  
 null 参照ではない引数は、有効値を格納している必要があります。  
  
 **コレクションを使用している場合、インデックスの値がコレクションのサイズよりも小さいことを確認します。**  
 インデックスの値は、コレクションのサイズの範囲内であることが必要です。サイズの範囲を超えたり、0 未満の値にしたりできません。 詳細については、「[コレクション](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
 **オーバーロードされた、2 つの引数を持つ ComboBox クラスまたは ListBox クラスの FindString メソッドまたは FindStringExact メソッドを使用している場合は、startIndex パラメーターを確認します。**  
 この例外は、`startIndex` が、関連付けられたリストの最終項目のインデックス値に等しい場合にスローされます。 このエラーを解決するには、`startIndex` パラメーターとして 0 を渡すか、1 つの引数を持つ `FindString` メソッドまたは `FindStringExact` メソッドを指定します。 詳細については、「[CComboBox::FindString](../Topic/CComboBox::FindString.md)」または「[CListBox::FindString](../Topic/CListBox::FindString.md)」を参照してください。  
  
## 参照  
 <xref:System.ArgumentOutOfRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)