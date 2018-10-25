---
title: XSLT スタイル シートの編集 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7dd25a531682c74284a74f065dc729f37ac7fb1a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287003"
---
# <a name="editing-xslt-style-sheets"></a>XSLT スタイル シートの編集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
XML エディターは、XSLT スタイル シートの編集にも使用することができます。 IntelliSense、アウトライン、XML スニペットなどの、エディターが備える既定の機能を活用できます。 さらに、XSLT での開発を容易にする新機能もあります。  
  
## <a name="xslt-features"></a>XSLT 機能  
 XSLT スタイル シートの操作時に固有な機能の説明を次の表に示します。  
  
 **構文の色分け表示**  
 XSLT キーワードなど`template`、`match`で指定された XSLT キーワードの色で表示されますが、**フォントおよび色**設定します。  
  
 **波線の下線**  
 XML エディターは、インストールされた xslt.xsd ファイルを使用して XSLT スタイル シートを検証します。 検証エラーは、青色の波下線で表示されます。 XML エディターは、バックグラウンドでスタイル シートのコンパイルも行い、適切な波下線でコンパイラのエラーや警告を通知します。  
  
 **スクリプト ブロックのサポート**  
 スクリプト ブロック内のコードは XSLT デバッガーによってサポートされているので、ブレークポイントを設定してスクリプト ブロックのコードをステップ実行することができます。  
  
 **XSLT 出力の表示**  
 XSL 変換を実行し、XML エディターから出力を参照することができます。 詳細については、次を参照してください。[方法: XML エディターから XSLT 変換を実行](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md)します。  
  
 **XSLT をデバッグします。**  
 XML エディターでは、XSLT ファイルから XSLT デバッガーを起動できます。 このデバッガーは、XSLT ファイルでのブレークポイントの設定や、XSLT 実行状態の表示などをサポートしています。 XSLT 変数の上にカーソルを置くと、変数の値を示すツール ヒントが表示されます。 このデバッガーを使用すると、スタイル シートのデバッグや、他のアプリケーションから呼び出されたコンパイル済みの XSL 変換のデバッグが可能です。 詳細については、次を参照してください。 [XSLT のデバッグ](../xml-tools/debugging-xslt.md)します。  
  
## <a name="see-also"></a>関連項目  
 [XML エディター](../xml-tools/xml-editor.md)



