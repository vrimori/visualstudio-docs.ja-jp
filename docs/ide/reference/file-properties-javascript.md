---
title: "ファイルのプロパティ、JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "javascript.project.property.expandedsdknode.fileversion"
  - "javascript.project.property.expandedsdknode.uri"
  - "javascript.project.property.expandedsdknode.filename"
  - "javascript.project.property.reference.description"
  - "javascript.project.property.reference.specificversion"
  - "javascript.project.property.reference.identity"
  - "javascript.project.property.fullpath"
  - "javascript.project.property.packageaction"
  - "javascript.project.property.reference.package"
  - "javascript.project.property.copytooutputdirectory"
  - "javascript.project.property.expandedsdknode.sdkpath"
  - "javascript.project.property.reference.filetype"
  - "javascript.project.property.reference.culture"
  - "javascript.project.property.filename"
  - "javascript.project.property.reference.resolvedpath"
  - "javascript.project.property.reference.version"
ms.assetid: 085913b8-a97b-45f7-85fa-bbb0902f3ee9
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# ファイルのプロパティ、JavaScript
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ファイルのプロパティを使用して、プロジェクト システムがファイルに対して実行するアクションを指定できます。  たとえば、ファイルがリソース ファイルとしてパッケージに追加するかどうかを示すには、ファイル プロパティを設定できます。  
  
 ソリューション エクスプローラーでファイルを選択し、\[プロパティ\] ウィンドウでそのプロパティを調べることができます。  JavaScriptファイルは4種類のプロパティがあります: **\[出力ディレクトリにコピー\]**、**\[パッケージ アクション\]**、**\[ファイル名\]**と **\[ファイル パス\]**。  
  
## ファイルのプロパティ  
 このセクションでは、JavaScriptファイルに共通のプロパティについて説明します。  
  
### \[出力ディレクトリにコピー\] プロパティ  
 このプロパティは、選択したソース ファイルを出力ディレクトリにコピーする際の条件を指定します。  ファイルを出力ディレクトリにコピーしない場合は **\[コピーしない\]** を選択します。  ファイルを常に出力ディレクトリにコピーする場合は **\[常にコピーする\]** を選択します。  出力ディレクトリに既に存在する同じ名前のファイルよりも新しいときにのみファイルをコピーする場合は、**\[新しい場合はコピーする\]** を選択します。  
  
### \[パッケージ アクション\]  
 **\[パッケージ アクション\]** のプロパティは、ビルドが実行されたときにVisual Studioがファイルの処理方法を示します。  **\[パッケージ アクション\]** は複数の値が1である可能性があります:  
  
-   **\[None\]** \-ファイルはパッケージ マニフェストに含まれません。  例として、ドキュメントを含むテキスト ファイル \(Readme ファイルなど\) があります。  
  
-   **\[$Content\]** \-ファイルはパッケージ マニフェストに含まれています。  たとえば、この設定は.htm、.gif、.htm、イメージ、ビデオ、オーディオ ファイルの既定値です。  
  
-   **\[マニフェスト\]** –はパッケージ マニフェスト ファイルに含まれません。  代わりに、ファイルは入力のためにパッケージ マニフェストを生成するときに使用されます。  これはpackage.appxmanifestファイルの既定値です。  
  
-   **\[リソース\]** \-ファイルはパッケージ マニフェストに含まれません。  代わりに、ファイルの内容はパッケージ マニフェストになったパッケージのリソースのインデックス\(PRI\)に指示されます。  一般に、リソース ファイルに使用します。  
  
 **\[パッケージ アクション\]** の既定値は、ソリューションに追加するファイルの拡張子によって異なります。  
  
### \[ファイル名\] プロパティ  
 読み取り専用の値としてファイル名が表示されます。  ファイルの名前を変更するには、ソリューション エクスプローラーで右クリックし、**\[名前の変更\]**を選択する必要があります。  
  
### 完全なパスのプロパティ  
 読み取り専用の値としてファイルの完全パスを表示します。  ファイル パスを変更するには、ソリューション エクスプローラーでファイルをドラッグ アンド ドロップすることができます。  
  
## 参照のファイル プロパティ  
 ここでは [!INCLUDE[win8_app_js](../../ide/reference/includes/win8_app_js_md.md)]から参照されるファイルに共通のプロパティについて説明します。  .winmdファイルのような参照は、ソリューション エクスプローラーのSDKリファレンス、プロジェクト間参照、またはアセンブリ参照を選択すると、他のプロパティには、ファイルの種類に応じてプロパティ ウィンドウに表示される場合があります。  
  
### カルチャ  
 参照に関連付けられている言語を表示します。  
  
### ファイルの種類  
 参照の種類のファイルを表示します。  
  
### \[ファイル バージョン\]  
 参照のファイル バージョンを表示します。  
  
### 同一。  
 プロジェクト ファイルに格納されている、プロジェクトで使用される参照のIDを表示します。  
  
### Package  
 参照に関連付けられているパッケージ マニフェストの名前を表示します。  
  
### Path解決する  
 プロジェクトで使用する参照のパスを表示します。  
  
### SDK Path  
 参照されたSDKのファイルへのパスを表示します。  
  
### Uri  
 ソース ファイルを含めるプロジェクトのHTMLまたはJavaScriptファイルに含まれている必要があるURIが表示されます。  
  
### バージョン  
 参照のバージョンを表示します。  
  
## 参照  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/ja-jp/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)