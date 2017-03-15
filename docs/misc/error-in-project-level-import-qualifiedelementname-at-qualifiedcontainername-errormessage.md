---
title: "&#39;&lt;qualifiedcontainername&gt;&#39; でのプロジェクト レベル インポート &#39;&lt;qualifiedelementname&gt;&#39; でエラーが発生しました: &lt;errormessage&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC30797"
  - "vbc30797"
helpviewer_keywords: 
  - "BC30797"
ms.assetid: 529f354f-f255-4adc-ab21-bd1796e58d69
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;qualifiedcontainername&gt;&#39; でのプロジェクト レベル インポート &#39;&lt;qualifiedelementname&gt;&#39; でエラーが発生しました: &lt;errormessage&gt;
ステートメントが別のアセンブリで定義されたプログラミング要素にアクセスしていますが、そのアセンブリへのプロジェクト参照がありません。  
  
 たとえば、`otherNamespace.otherClass.desiredEnumeration` という修飾文字列を使用して、`desiredEnumeration` という名前の列挙体にアクセスするコードがあるとします。 ユーザーのプロジェクトの参照の中から、コンパイラが `otherNamespace.otherClass` を見つけることができない場合に、このエラーが生成されます。  
  
 **エラー ID:** BC30797  
  
### このエラーを解決するには  
  
1.  プログラミング要素の修飾文字列にあるすべての要素のスペルが正しいことを確認します。  
  
2.  プロジェクトに、目的のプログラミング要素を定義しているアセンブリへの参照があることを確認します。  
  
3.  エラー メッセージを調べて、適切なアクションを実行します。  
  
## 参照  
 [NOTINBUILD: 同じ名前を持つ複数の変数がある場合に参照を解決する](http://msdn.microsoft.com/ja-jp/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [NIB 方法: プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [NIB 方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)