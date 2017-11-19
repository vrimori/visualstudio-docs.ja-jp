---
title: "方法: XML ファイルを編集 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cda89cc132ecd496605c19194c0221de503f4469
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-edit-xml-files"></a>方法 : XML ファイルを編集する
XML エディターは、XML ファイル用の新しいエディターです。 スタンドアロンの XML ファイル、または Visual Studio プロジェクトと関連付けられたファイルに対して使用できます。 XML エディターと関連付けられるファイル拡張子は、.config、.dtd、.xml、.xsd、.xdr、.xsl、.xslt、および .vssettings です。 XML エディターは、特定のエディターが登録されておらず、XML や DTD のコンテンツを含む他のファイルの種類にも関連付けられます。  
  
> [!NOTE]
>  XHTML ドキュメントは HTML エディターによって処理されます。  
  
### <a name="to-edit-an-xml-file"></a>XML ファイルを編集するには  
  
1.  編集するファイルをダブルクリックします。  
  
### <a name="to-add-a-new-xml-file-to-a-project"></a>新しい XML ファイルをプロジェクトに追加するには  
  
1.  **プロジェクト**メニューの **新しい項目の追加**です。  
  
2.  選択**XML ファイル**から、**テンプレート**ウィンドウです。  
  
3.  内のファイル名を入力、**名前**フィールドとキーを押して**追加**です。  
  
     XML ファイルがプロジェクトに追加され、XML エディターによって開かれます。 ファイルには既定の XML 宣言 `<?xml version="1.0" encoding="utf-8" ?>` が含まれています。  
  
### <a name="to-add-an-existing-xml-file-to-a-project"></a>既存の XML ファイルをプロジェクトに追加するには  
  
1.  **プロジェクト**メニューの **既存項目の追加**です。  
  
     **既存項目の追加** ダイアログ ボックスが表示されます。  
  
2.  XML ファイルとキーを押して選択**追加**です。  
  
### <a name="to-create-a-new-xml-or-xslt-file"></a>新しい XML ファイルまたは XSLT ファイルを作成するには  
  
1.  **ファイル**メニューの **新規**です。  
  
     **新しいファイル** ダイアログ ボックスが表示されます。  
  
2.  選択**XML ファイル**; 新しい XML ファイルを作成または選択**XSLT ファイル**新しい XSLT スタイル シートを作成します。  
  
3.  をクリックして**開く**です。  
  
### <a name="to-create-a-project-for-xml-files"></a>XML ファイル用のプロジェクトを作成するには  
  
1.  **ファイル**メニューの **新規**、し、**プロジェクト**です。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  任意のコード言語を選択して**空のプロジェクト**、 をクリック**OK**です。  
  
3.  プロジェクトに XML ファイルを追加します。  
  
     このプロジェクトに追加したスキーマは XML エディターによって検出され、このプロジェクトが開かれている間に編集する XML、スキーマ、または XSLT ファイルにおいて、検証と IntelliSense のために使用されます。  
  
## <a name="see-also"></a>関連項目  
 [XML エディター](../xml-tools/xml-editor.md)   
 [XML ドキュメントのプロパティと [プロパティ] ウィンドウ](../xml-tools/xml-document-properties-properties-window.md)   
 [方法 : XML ドキュメントから XML スキーマを作成する](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)