---
title: '方法 : XSLT でブレークポイントを使用する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 430b7f14f35506b45fe73be47d056cdd7b6a9c95
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-use-breakpoints-with-xslt"></a>方法: XSLT でブレークポイントを使用します。

XSLT スタイル シート内または XML ソース ドキュメント内でブレークポイントを設定することができます。 タグにブレークポイントを設定した場合は、実行の開始時に、ソース行情報を含む次のステートメントにブレークポイントが移動します。

詳細については、次を参照してください。[デバッグの基礎: ブレークポイント](../debugger/using-breakpoints.md)です。

## <a name="set-a-breakpoint-in-a-style-sheet"></a>スタイル シートにブレークポイントを設定します。

XSLT スタイル シートでは、開始タグ、終了タグ、およびテキスト ノードにブレークポイントを設定できます。 スクリプト ブロック内のコードにブレークポイントを設定することもできます。

### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>スタイル シート内にブレークポイントを設定するには

1.  XML エディターでスタイル シートを開きます。

2.  ブレークポイントの場所にカーソルを置き、右クリックし、順にポイント**ブレークポイント**、 をクリック**ブレークポイントの挿入**です。

3.  参照 ボタンをクリックして (**.**) で、**入力**ドキュメントのプロパティ ウィンドウのフィールドです。

4.  XML ソース ドキュメントを見つけてクリックして**開く**です。

     これで、XSLT 変換のために使用されるソース ドキュメント ファイルが設定されます。

5.  クリックして、 **XSL のデバッグ**XML エディター ツールバーのボタンをクリックします。

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>XML ソース ドキュメント内のブレークポイントを設定します。

XML ソース ドキュメントでは、要素、属性、名前空間ノード、コメント、処理命令、およびテキスト ノードにブレークポイントを設定できます。 ドキュメント ノード、または、親要素から継承された名前空間ノードにブレークポイントを設定することはできません。

### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>XML ソース ドキュメント内にブレークポイントを設定するには

1.  XML エディターで XML ドキュメントを開きます。

2.  ブレークポイントの場所にカーソルを置き、右クリックし、順にポイント**ブレークポイント**、 をクリック**ブレークポイントの挿入**です。

3.  参照 ボタンをクリックして (**.**) で、 **Stylesheet**ドキュメントのプロパティ ウィンドウのフィールドです。

4.  XML ソース ドキュメントを見つけてクリックして**開く**です。

     これで、XSLT 変換のために使用されるソース ドキュメント ファイルが設定されます。

5.  クリックして、 **XSL のデバッグ**XML エディター ツールバーのボタンをクリックします。

## <a name="see-also"></a>関連項目

- [チュートリアル: XSLT スタイル シートをデバッグします。](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)