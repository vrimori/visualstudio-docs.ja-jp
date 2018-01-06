---
title: "方法: XPath 式の評価 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8a0072df206fcdfc27966632e3801316bcfb7274
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-evaluate-an-xpath-expression"></a>方法 : XPath 式を評価する
含む XPath 式を評価することができます、 **クイック ウォッチ**  ダイアログ ボックス。 XPath 式は、W3C XPath 1.0 勧告に沿って有効である必要があります。 現在の XSLT コンテキスト-は、`self::node()`内のノード、 **[ローカル]**ウィンドウ: XPath 式の評価コンテキストを提供します。  
  
 XPath 式を評価する際にどの機能がサポートされるかについて次の一覧に示します。  
  
-   組み込みの XPath 関数はサポートされます。  
  
-   組み込みの XSLT 関数はサポートされません。  
  
-   ユーザー定義関数はサポートされません。  
  
> [!NOTE]
>  次の手順から belowAvg.xsl および books.xml ファイルを使用して、[チュートリアル: XSLT スタイル シートのデバッグ](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)トピックです。  
  
### <a name="to-evaluate-an-xpath-expression"></a>XPath 式を評価するには  
  
1.  `xsl:if` 開始タグにブレークポイントを挿入します。  
  
2.  クリックして、 **XSL のデバッグ**XML エディター ツールバーのボタンをクリックします。  
  
     デバッガーが起動され、`xsl:if` タグで実行が中断されます。  
  
3.  右クリックし  **クイック ウォッチ**です。  
  
     **クイック ウォッチ**  ダイアログ ボックスが表示されます。  
  
4.  入力`./price/text()`で、**式**のフィールド、 **クイック ウォッチ**  ダイアログ ボックスをクリック**再評価**です。  
  
     現在の book ノードの価格が表示されます、**値**ボックス。  
  
5.  XPath 式を変更して`./price/text() < $bookAverage` をクリック**再評価**です。  
  
     **値**ボックスに表示する XPath 式の評価結果`true`です。  
  
## <a name="see-also"></a>参照  
 [XSLT のデバッグ](../xml-tools/debugging-xslt.md)