---
title: "方法: XML エディターから XSLT 変換を実行する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# 方法: XML エディターから XSLT 変換を実行する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XML エディターでは、XSLT スタイル シートを XML ドキュメントと関連付けて変換を実行し、結果を表示させることができます。XSLT 変換から得られた結果の出力は、新しいドキュメント ウィンドウに表示されます。  
  
 **Output** プロパティでは、出力のファイル名を指定します。**Output** プロパティが空白の場合は、一時ディレクトリ内にファイル名が生成されます。ファイル拡張子はスタイル シート内の `xsl:output` 要素に基づき、.xml、.txt、または .htm のいずれかが付けられます。  
  
 **Output** プロパティで、拡張子が .htm または .html のファイル名が指定されている場合は、[!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Internet Explorer を使用して、XSLT 出力のプレビューが行われます。他のファイル拡張子はすべて、[!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio によって選択されている既定のエディターを使用して開かれます。たとえば、ファイル拡張子が .xml の場合、Visual Studio では XML エディターが使用されます。  
  
### XML ドキュメントから XSLT 変換を実行するには  
  
1.  XML エディターで XML ドキュメントを開きます。  
  
2.  XSLT スタイル シートを XML ドキュメントと関連付けます。  
  
    -   XML ドキュメントに `xml-stylesheet` 処理命令を追加します。たとえば、ドキュメントのプロローグに `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` という行を追加します。  
  
         または  
  
    -   \[プロパティ\] ウィンドウを使用して、XSLT スタイル シートを追加します。ドキュメントの \[プロパティ ウィンドウ\] で、\[Stylesheet\] フィールドの \[参照\] ボタンをクリックし、目的の XSLT スタイル シートを選択します。次に、\[開く\] をクリックします。  
  
3.  XML エディター ツール バーの \[Show XSL Output \(XSL 出力を表示\)\] ボタンをクリックします。  
  
    > [!NOTE]
    >  XML ドキュメントに関連付けられているスタイル シートがない場合は、使用するスタイル シートの指定を求めるダイアログ ボックスが表示されます。  
    >   
    >  XSLT 変換から得られた結果の出力は、新しいドキュメント ウィンドウに表示されます。  
  
### XSLT スタイル シートから XSLT 変換を実行するには  
  
1.  XML エディターで XSLT スタイル シートを開きます。  
  
2.  ドキュメントの \[プロパティ\] ウィンドウの \[入力\] フィールドで、XML ドキュメントを指定します。  
  
    > [!NOTE]
    >  この XML ドキュメントは、変換に使用する入力ドキュメントです。XSLT 変換が開始されたときにドキュメントが指定されていない場合、\[ファイルを開く\] ダイアログ ボックスが表示されるので、その時点でドキュメントを指定することができます。  
  
3.  XML エディター ツール バーの \[Show XSL Output \(XSL 出力を表示\)\] ボタンをクリックします。  
  
     XSLT 変換から得られた結果の出力は、新しいドキュメント ウィンドウに表示されます。  
  
### 異なる出力ファイル名を指定するには  
  
1.  ドキュメントの \[プロパティ\] ウィンドウの \[出力\] フィールドで、ファイル名を指定します。  
  
2.  XML エディター ツール バーの \[Show XSL Output \(XSL 出力を表示\)\] ボタンをクリックします。  
  
     XSLT 変換から得られた結果の出力は、新しいドキュメント ウィンドウに表示されます。出力のウィンドウで使用されるエディターは、\[出力\] ドキュメント プロパティのファイル拡張子によって異なります。  
  
## 参照  
 [XML エディター](../xml-tools/xml-editor.md)