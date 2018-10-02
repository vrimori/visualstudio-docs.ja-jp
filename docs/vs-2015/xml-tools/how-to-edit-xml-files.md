---
title: '方法: XML ファイルを編集 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7bb1e8803a133a85af129a6e929428aae89acaa6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547081"
---
# <a name="how-to-edit-xml-files"></a>方法 : XML ファイルを編集する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: XML ファイルの編集](https://docs.microsoft.com/visualstudio/xml-tools/how-to-edit-xml-files)します。  
  
  
XML エディターは、XML ファイル用の新しいエディターです。 スタンドアロンの XML ファイル、または Visual Studio プロジェクトと関連付けられたファイルに対して使用できます。 XML エディターと関連付けられるファイル拡張子は、.config、.dtd、.xml、.xsd、.xdr、.xsl、.xslt、および .vssettings です。 XML エディターは、特定のエディターが登録されておらず、XML や DTD のコンテンツを含む他のファイルの種類にも関連付けられます。  
  
> [!NOTE]
>  XHTML ドキュメントは HTML エディターによって処理されます。  
  
### <a name="to-edit-an-xml-file"></a>XML ファイルを編集するには  
  
1.  編集するファイルをダブルクリックします。  
  
### <a name="to-add-a-new-xml-file-to-a-project"></a>新しい XML ファイルをプロジェクトに追加するには  
  
1.  **プロジェクト**メニューの **新しい項目の追加**します。  
  
2.  選択**XML ファイル**から、**テンプレート**ウィンドウ。  
  
3.  内のファイル名を入力、**名前**フィールドとキーを押して**追加**します。  
  
     XML ファイルがプロジェクトに追加され、XML エディターによって開かれます。 ファイルには既定の XML 宣言 `<?xml version="1.0" encoding="utf-8" ?>` が含まれています。  
  
### <a name="to-add-an-existing-xml-file-to-a-project"></a>既存の XML ファイルをプロジェクトに追加するには  
  
1.  **プロジェクト**メニューの **既存項目の追加**します。  
  
     **既存項目の追加** ダイアログ ボックスが表示されます。  
  
2.  XML ファイルとキーを押して選択**追加**します。  
  
### <a name="to-create-a-new-xml-or-xslt-file"></a>新しい XML ファイルまたは XSLT ファイルを作成するには  
  
1.  **ファイル**メニューの **新規**します。  
  
     **新しいファイル** ダイアログ ボックスが表示されます。  
  
2.  選択**XML ファイル**; 新しい XML ファイルを作成するか、選択する**XSLT ファイル**新しい XSLT スタイル シートを作成します。  
  
3.  クリックして**オープン**します。  
  
### <a name="to-create-a-project-for-xml-files"></a>XML ファイル用のプロジェクトを作成するには  
  
1.  **ファイル**メニューの **新規**、し、**プロジェクト**します。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  任意のコード言語の選択**空のプロジェクト**、 をクリック**OK**します。  
  
3.  プロジェクトに XML ファイルを追加します。  
  
     このプロジェクトに追加したスキーマは XML エディターによって検出され、このプロジェクトが開かれている間に編集する XML、スキーマ、または XSLT ファイルにおいて、検証と IntelliSense のために使用されます。  
  
## <a name="see-also"></a>関連項目  
 [XML エディター](../xml-tools/xml-editor.md)   
 [XML ドキュメントのプロパティと [プロパティ] ウィンドウ](../xml-tools/xml-document-properties-properties-window.md)   
 [方法 : XML ドキュメントから XML スキーマを作成する](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)



