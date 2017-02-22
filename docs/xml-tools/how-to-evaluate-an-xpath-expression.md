---
title: "方法 : XPath 式を評価する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 方法 : XPath 式を評価する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XPath 式は、\[クイック ウォッチ\] ダイアログ ボックスを使用して評価することができます。XPath 式は、W3C XPath 1.0 勧告に沿って有効である必要があります。XPath 式を評価するためのコンテキストは、現在の XSLT コンテキスト、つまり、\[ローカル\] ウィンドウに表示される `self::node()` ノードによって提供されます。  
  
 XPath 式を評価する際にどの機能がサポートされるかについて次の一覧に示します。  
  
-   組み込みの XPath 関数はサポートされます。  
  
-   組み込みの XSLT 関数はサポートされません。  
  
-   ユーザー定義関数はサポートされません。  
  
> [!NOTE]
>  次の手順では、「[チュートリアル : XSLT スタイル シートのデバッグ](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)」の belowAvg.xsl と books.xml を使用します。  
  
### XPath 式を評価するには  
  
1.  `xsl:if` 開始タグにブレークポイントを挿入します。  
  
2.  XML エディター ツール バーの \[Debug XSL \(XSL のデバッグ\)\] ボタンをクリックします。  
  
     デバッガーが起動され、`xsl:if` タグで実行が中断されます。  
  
3.  右クリックして \[クイック ウォッチ\] を選択します。  
  
     \[クイック ウォッチ\] ダイアログ ボックスが表示されます。  
  
4.  \[クイック ウォッチ\] ダイアログ ボックスの \[式\] フィールドに「`./price/text()`」と入力し、\[再評価\] をクリックします。  
  
     現在の book ノードの価格が \[値\] ボックスに表示されます。  
  
5.  XPath 式を `./price/text() < $bookAverage` に変更し、\[再評価\] をクリックします。  
  
     \[値\] ボックスに、XPath 式が `true` に評価されたことが示されます。  
  
## 参照  
 [XSLT のデバッグ](../xml-tools/debugging-xslt.md)