---
title: "方法: XML エディターから XSLT 変換を実行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a432dabb09f3242ff3ba73527b86aac45e609588
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>方法: XML エディターから XSLT 変換を実行する
XML エディターでは、XSLT スタイル シートを XML ドキュメントと関連付けて変換を実行し、結果を表示させることができます。 XSLT 変換から得られた結果の出力は、新しいドキュメント ウィンドウに表示されます。  
  
 **出力**プロパティは、出力ファイル名を指定します。 場合、**出力**プロパティが空白、一時ディレクトリにファイル名が生成されます。 ファイル拡張子はスタイル シート内の `xsl:output` 要素に基づき、.xml、.txt、または .htm のいずれかが付けられます。  
  
 場合、**出力**プロパティ .htm ファイルとファイル名が指定または .html の拡張機能、XSLT 出力の使用のプレビュー時[!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)]Internet Explorer です。 他のファイル拡張子はすべて、[!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio によって選択されている既定のエディターを使用して開かれます。 たとえば、ファイル拡張子が .xml の場合、Visual Studio では XML エディターが使用されます。  
  
### <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>XML ドキュメントから XSLT 変換を実行するには  
  
1.  XML エディターで XML ドキュメントを開きます。  
  
2.  XSLT スタイル シートを XML ドキュメントと関連付けます。  
  
    -   XML ドキュメントに `xml-stylesheet` 処理命令を追加します。 たとえば、ドキュメントのプロローグに `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` という行を追加します。  
  
         または  
  
    -   XSLT スタイル シートを使用して、追加、**プロパティ**ウィンドウです。 ドキュメント内**プロパティ ウィンドウ**、 をクリックして、**参照**ボタンをクリックして、 **Stylesheet**フィールドで、XSLT スタイル シートを選択し、をクリックして**を開く**.  
  
3.  クリックして、 **ShowXSL 出力**のボタンでは、 **XML エディター**ツールバー。  
  
    > [!NOTE]
    >  XML ドキュメントに関連付けられているスタイル シートがない場合は、使用するスタイル シートの指定を求めるダイアログ ボックスが表示されます。  
    >   
    >  XSLT 変換から得られた結果の出力は、新しいドキュメント ウィンドウに表示されます。  
  
### <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>XSLT スタイル シートから XSLT 変換を実行するには  
  
1.  XML エディターで XSLT スタイル シートを開きます。  
  
2.  内の XML ドキュメントを指定、**入力**ドキュメントのフィールド**プロパティ**ウィンドウです。  
  
    > [!NOTE]
    >  この XML ドキュメントは、変換に使用する入力ドキュメントです。 XSLT 変換が開始されると、ドキュメントが指定されていない場合、**ファイルを開く** ダイアログ ボックスが表示され、その時点でドキュメントを指定することができます。  
  
3.  クリックして、 **ShowXSLT 出力**のボタンでは、 **XML エディター**ツールバー。  
  
     XSLT 変換から得られた結果の出力は、新しいドキュメント ウィンドウに表示されます。  
  
### <a name="to-provide-a-different-output-file-name"></a>異なる出力ファイル名を指定するには  
  
1.  ファイル名を指定、**出力**ドキュメントのフィールド**プロパティ**ウィンドウです。  
  
2.  クリックして、 **ShowXSLT 出力**のボタンでは、 **XML エディター**ツールバー。  
  
     新しいドキュメント ウィンドウに、XSLT 変換からの出力結果が表示され、出力 ウィンドウで使用されるエディターは、のファイル拡張子によって異なります。、**出力**プロパティを文書化します。  
  
## <a name="see-also"></a>関連項目  
 [XML エディター](../xml-tools/xml-editor.md)