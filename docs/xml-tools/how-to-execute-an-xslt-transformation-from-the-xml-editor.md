---
title: '方法: XML エディターから XSLT 変換を実行する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 742e78eca883dd2e9e9fc5ecfa8ec5381f003b61
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987571"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>方法: XML エディターから XSLT 変換を実行します。

XML エディターでは、XSLT スタイル シートを XML ドキュメントと関連付けて変換を実行し、結果を表示させることができます。 XSLT 変換から得られた結果の出力は、新しいドキュメント ウィンドウに表示されます。

**出力**プロパティは、出力ファイル名を指定します。 場合、**出力**プロパティが空白の一時ディレクトリにファイル名が生成されます場合、。 ファイル拡張子がに基づいて、`xsl:output`要素のスタイル シート *。xml*、.*txt*または *。htm*します。

場合、**出力**プロパティを持つファイル名を指定します、 *。htm*または *。html*拡張 XSLT 出力がプレビューを使用して[!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)]Internet Explorer。 他のファイル拡張子はすべて、[!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio によって選択されている既定のエディターを使用して開かれます。 たとえば、ファイル拡張子がある場合です。*xml*、Visual Studio は、XML エディターを使用します。

## <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>XML ドキュメントから XSLT 変換を実行するには

1.  XML エディターで XML ドキュメントを開きます。

2.  XSLT スタイル シートを XML ドキュメントと関連付けます。

    -   XML ドキュメントに `xml-stylesheet` 処理命令を追加します。 たとえば、ドキュメントのプロローグに `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` という行を追加します。

         - または -

    -   XSLT スタイル シートを使用して、追加、**プロパティ**ウィンドウ。 文書の**プロパティ ウィンドウ**、 をクリックして、**参照**ボタン、**スタイル シート**フィールドで、XSLT スタイル シートを選択し、をクリックして**を開く**.

3.  をクリックして、 **ShowXSL 出力**のボタンでは、 **XML エディター**ツールバー。

    > [!NOTE]
    > XML ドキュメントに関連付けられているスタイル シートがない場合は、使用するスタイル シートの指定を求めるダイアログ ボックスが表示されます。
    >
    >  XSLT 変換から得られた結果の出力は、新しいドキュメント ウィンドウに表示されます。

## <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>XSLT スタイル シートから XSLT 変換を実行するには

1.  XML エディターで XSLT スタイル シートを開きます。

2.  内の XML ドキュメントの指定、**入力**ドキュメントのフィールド**プロパティ**ウィンドウ。

    > [!NOTE]
    > この XML ドキュメントは、変換に使用する入力ドキュメントです。 XSLT 変換が開始されると、ドキュメントが指定されていない場合、**ファイルを開く** ダイアログ ボックスが表示されたら、およびその時点でドキュメントを指定することができます。

3.  をクリックして、 **ShowXSLT 出力**のボタンでは、 **XML エディター**ツールバー。

     XSLT 変換から得られた結果の出力は、新しいドキュメント ウィンドウに表示されます。

## <a name="to-provide-a-different-output-file-name"></a>異なる出力ファイル名を指定するには

1.  ファイル名を指定、**出力**ドキュメントのフィールド**プロパティ**ウィンドウ。

2.  をクリックして、 **ShowXSLT 出力**のボタンでは、 **XML エディター**ツールバー。

     XSLT 変換からの出力結果が新しいドキュメント ウィンドウに表示され、出力ウィンドウで使用されるエディターは、ファイルの拡張子によって異なります、**出力**ドキュメントのプロパティ。

## <a name="see-also"></a>関連項目

- [XML エディター](../xml-tools/xml-editor.md)