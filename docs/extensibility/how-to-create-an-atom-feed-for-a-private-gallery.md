---
title: "方法: Atom の作成のプライベート ギャラリー フィード |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3b966aa30fa2e7e9eae07b56c1a578f9688772a0
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>方法: Atom を作成するプライベート ギャラリーのフィード
Atom (RSS) フィードをイントラネットの場所に拡張機能が含まれており、フィードへの追加を作成する**拡張機能と更新**をプライベート ギャラリーとして。 詳細については、「[プライベート ギャラリー](../extensibility/private-galleries.md)」を参照してください。  
  
## <a name="creating-an-atom-feed"></a>作成する Atom フィード  
 Atom フィードをプライベート ギャラリーとしてを作成するには、最初に、フォルダーに、拡張機能 (.vsix ファイル) を収集します。 場合は、サブフォルダーにそれらを整理できます。 次のリソースも必要になります。  
  
-   プライベート ギャラリーとして、拡張機能を利用できるようにする atom.xml ファイルです。 Atom.xml ファイルに接続する方法については**拡張機能と更新**を参照してください[プライベート ギャラリー](../extensibility/private-galleries.md)です。  
  
-   拡張機能 (たとえば、スクリーン ショット) から抽出されたすべてのイメージ ファイルを格納するフォルダー。 使用できるように、atom.xml ファイルがこれらのイメージへの相対リンクを含む**拡張機能と更新プログラム**です。  
  
 たとえば、フォルダーに次の 2 つの拡張機能を収集することを想定します。  
  
-   Template_Wizard_239.vsix は空の VSIX プロジェクト テンプレート。  
  
-   SelectionHighlight.vsix は、選択した単語のすべてのインスタンスを強調表示するツールです。  
  
 Atom.xml ファイルの内容は次の例のようにします。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<feed xmlns="http://www.w3.org/2005/Atom">  
<title type="text" />   
<id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
<updated>2011-04-14T21:25:48Z</updated>   
<entry>  
<id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
<title type="text">Highlight all occurrences of selected word</title>   
<summary type="text">This extends the editor to highlight ....</summary>   
<published>2011-04-14T14:24:51-07:00</published>   
<updated>2011-04-14T14:24:22-07:00</updated>   
<author>  
<name>Microsoft</name>   
</author>  
<link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />   
<link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />   
<content type="application/octet-stream" src="SelectionHighlight.vsix" />   
<Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010">  
<Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>   
<Version>1.31</Version>   
<References />   
<Rating xsi:nil="true" />   
<RatingCount xsi:nil="true" />   
<DownloadCount xsi:nil="true" />   
</Vsix>  
</entry>  
<entry>  
<id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>   
...  
</entry>  
</feed>
```  
  
 2 つのリンク タグを画像の生成されたフォルダー内のスクリーン ショットを参照することに注意してください。  
  
## <a name="see-also"></a>関連項目  
 [プライベート ギャラリー](../extensibility/private-galleries.md)
