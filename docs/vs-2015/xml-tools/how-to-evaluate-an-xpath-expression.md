---
title: '方法: XPath 式を評価 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 82d1330860a67b5dcb2ea52777bd84cceda4db00
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546512"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>方法 : XPath 式を評価する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用した XPath 式を評価することができます、 **クイック ウォッチ**  ダイアログ ボックス。 XPath 式は、W3C XPath 1.0 勧告に沿って有効である必要があります。 現在の XSLT コンテキスト:、`self::node()`内のノード、 **[ローカル]** ウィンドウ: XPath 式の評価コンテキストを提供します。  
  
 XPath 式を評価する際にどの機能がサポートされるかについて次の一覧に示します。  
  
-   組み込みの XPath 関数はサポートされます。  
  
-   組み込みの XSLT 関数はサポートされません。  
  
-   ユーザー定義関数はサポートされません。  
  
> [!NOTE]
>  次の手順から belowAvg.xsl と books.xml ファイルを使用して、[チュートリアル: XSLT スタイル シートのデバッグ](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)トピック。  
  
### <a name="to-evaluate-an-xpath-expression"></a>XPath 式を評価するには  
  
1.  `xsl:if` 開始タグにブレークポイントを挿入します。  
  
2.  をクリックして、 **XSL のデバッグ**XML エディターのツールバーのボタンをクリックします。  
  
     デバッガーが起動され、`xsl:if` タグで実行が中断されます。  
  
3.  右クリックして **[クイック ウォッチ]** します。  
  
     **クイック ウォッチ**  ダイアログ ボックスが表示されます。  
  
4.  入力`./price/text()`で、**式**のフィールド、 **クイック ウォッチ**  ダイアログ ボックスをクリックします**再評価**します。  
  
     現在の book ノードの価格が表示されます、**値**ボックス。  
  
5.  XPath 式を変更`./price/text() < $bookAverage`クリック**再評価**。  
  
     **値**ボックスが表示されます、XPath 式の評価が`true`します。  
  
## <a name="see-also"></a>関連項目  
 [XSLT のデバッグ](../xml-tools/debugging-xslt.md)

