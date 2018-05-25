---
title: XSLT スタイル シートの編集
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72f224e91f72d2fa751ddc8b170f78b8859c43f4
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2018
---
# <a name="edit-xslt-style-sheets"></a>XSLT スタイル シートの編集

XML エディターは、XSLT スタイル シートの編集にも使用することができます。 IntelliSense、アウトライン、XML スニペットなどの、エディターが備える既定の機能を活用できます。 さらに、XSLT での開発を容易にする新機能もあります。

## <a name="xslt-features"></a>XSLT 機能
 XSLT スタイル シートの操作時に固有な機能の説明を次の表に示します。

 **構文の色分け**

 XSLT キーワードなど`template`、`match`で指定された XSLT キーワードの色で表示されます、**フォントおよび色**設定します。

 **波形の下線**

 XML エディターを使用して、インストールされている*置かれている xslt.xsd* XSLT スタイル シートを検証するファイル。 検証エラーは、青色の波下線で表示されます。 XML エディターは、バックグラウンドでスタイル シートのコンパイルも行い、適切な波下線でコンパイラのエラーや警告を通知します。

 **スクリプト ブロックのサポート**

 スクリプト ブロック内のコードは XSLT デバッガーによってサポートされているので、ブレークポイントを設定してスクリプト ブロックのコードをステップ実行することができます。

 **XSLT 出力の表示**

 XSL 変換を実行し、XML エディターから出力を参照することができます。 詳細については、次を参照してください。[する方法: XML エディターから XSLT 変換を実行](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md)です。

 **XSLT をデバッグします。**

 XML エディターでは、XSLT ファイルから XSLT デバッガーを起動できます。 このデバッガーは、XSLT ファイルでのブレークポイントの設定や、XSLT 実行状態の表示などをサポートしています。 XSLT 変数の上にカーソルを置くと、変数の値を示すツール ヒントが表示されます。 このデバッガーを使用すると、スタイル シートのデバッグや、他のアプリケーションから呼び出されたコンパイル済みの XSL 変換のデバッグが可能です。 詳細については、次を参照してください。 [XSLT のデバッグ](../xml-tools/debugging-xslt.md)です。

## <a name="see-also"></a>関連項目

- [XML エディター](../xml-tools/xml-editor.md)