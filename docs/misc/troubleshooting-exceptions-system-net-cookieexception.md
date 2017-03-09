---
title: "例外のトラブルシューティング : System.Net.CookieException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "CookieException クラス"
ms.assetid: 7db6b962-cc5e-4b63-be65-894a8f186b38
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Net.CookieException
<xref:System.Net.CookieException> 例外は、クッキーをクッキー コンテナーに追加するときにエラーが発生するとスローされます。  
  
## 関連するヒント  
 **クッキーのサイズがクッキーのコンテナーに許可された最大値を超えていないことを確認します。**  
 この例外は、長さが <xref:System.Net.Cookie> を超える <xref:System.Net.CookieContainer.MaxCookieSize%2A> を <xref:System.Net.CookieContainer> に追加しようとするとスローされます。 クッキーの最大サイズは、既定では 4,096 バイトです。  
  
 **クッキーの Name プロパティを設定するときに、値が null 参照または空の文字列でないことを確認します。**  
 <xref:System.Net.Cookie.Name%2A> プロパティは、<xref:System.Net.Cookie> クラスのインスタンスを使用する前に初期化される必要があります。 等号 \(\=\)、セミコロン \(;\)、コンマ \(,\)、改行 \(\\n\)、復帰 \(\\r\)、およびタブ \(\\t\) は予約されているため、この属性値には使用できません。 ドル記号 \($\) は最初の文字として使用できません。  
  
 **クッキーの Port プロパティを設定するときに、値が有効であり、二重引用符で囲まれていることを確認します。**  
 <xref:System.Net.Cookie.Port%2A> 属性は、クッキーの送信先ポートを制限します。 既定値は、制限がないことを示します。 このプロパティを空の文字列 \(""\) に設定すると、HTTP 応答に使用されるポートにポートが制限されます。 それ以外の場合は、コンマ区切りのポート値を含む文字列を引用符で囲む必要があります。  
  
 **クッキーの Value プロパティを設定するときに、値が null でないことを確認します。**  
 セミコロン \(;\) およびコンマ \(,\) は予約されているため、このプロパティには使用できません。  
  
## 参照  
 <xref:System.Net.CookieException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Write a Cookie](../Topic/How%20to:%20Write%20a%20Cookie.md)