---
title: "方法 : XML ファイルを編集する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# 方法 : XML ファイルを編集する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XML エディターは、XML ファイル用の新しいエディターです。スタンドアロンの XML ファイル、または Visual Studio プロジェクトと関連付けられたファイルに対して使用できます。XML エディターと関連付けられるファイル拡張子は、.config、.dtd、.xml、.xsd、.xdr、.xsl、.xslt、および .vssettings です。XML エディターは、特定のエディターが登録されておらず、XML や DTD のコンテンツを含む他のファイルの種類にも関連付けられます。  
  
> [!NOTE]
>  XHTML ドキュメントは HTML エディターによって処理されます。  
  
### XML ファイルを編集するには  
  
1.  編集するファイルをダブルクリックします。  
  
### 新しい XML ファイルをプロジェクトに追加するには  
  
1.  \[プロジェクト\] メニューの \[新しい項目の追加\] をクリックします。  
  
2.  \[テンプレート\] ペインの \[XML ファイル\] を選択します。  
  
3.  \[名前\] フィールドにファイル名を入力し、\[追加\] をクリックします。  
  
     XML ファイルがプロジェクトに追加され、XML エディターによって開かれます。ファイルには既定の XML 宣言 `<?xml version="1.0" encoding="utf-8" ?>` が含まれています。  
  
### 既存の XML ファイルをプロジェクトに追加するには  
  
1.  \[プロジェクト\] メニューの \[既存項目の追加\] をクリックします。  
  
     \[既存項目の追加\] ダイアログ ボックスが表示されます。  
  
2.  XML ファイルを選択し、\[追加\] をクリックします。  
  
### 新しい XML ファイルまたは XSLT ファイルを作成するには  
  
1.  \[ファイル\] メニューの \[新規作成\] を選択します。  
  
     \[新しいファイル\] ダイアログ ボックスが表示されます。  
  
2.  \[XML ファイル\] を選択して新しい XML ファイルを作成するか、\[XSLT ファイル\] を選択して新しい XSLT スタイル シートを作成します。  
  
3.  \[開く\] をクリックします。  
  
### XML ファイル用のプロジェクトを作成するには  
  
1.  \[ファイル\] メニューの \[新規作成\] をクリックし、次に \[プロジェクト\] をクリックします。  
  
     \[新しいプロジェクト\] ダイアログ ボックスが表示されます。  
  
2.  任意のコードの言語を選択し、\[空のプロジェクト\] を選択します。次に、\[OK\] をクリックします。  
  
3.  プロジェクトに XML ファイルを追加します。  
  
     このプロジェクトに追加したスキーマは XML エディターによって検出され、このプロジェクトが開かれている間に編集する XML、スキーマ、または XSLT ファイルにおいて、検証と IntelliSense のために使用されます。  
  
## 参照  
 [XML エディター](../xml-tools/xml-editor.md)   
 [XML ドキュメント プロパティと \[プロパティ\] ウィンドウ](../Topic/XML%20Document%20Properties,%20Properties%20Window.md)   
 [方法 : XML ドキュメントから XML スキーマを作成する](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)