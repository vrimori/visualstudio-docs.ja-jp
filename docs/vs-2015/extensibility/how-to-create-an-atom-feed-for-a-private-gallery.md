---
title: '方法: Atom を作成するプライベート ギャラリーのフィード |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c6d46129a77d0d6e0b764f2921dce77014b865f7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548956"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>方法: Atom を作成するプライベート ギャラリーのフィード
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: プライベート ギャラリーの Atom フィードを作成する](https://docs.microsoft.com/visualstudio/extensibility/how-to-create-an-atom-feed-for-a-private-gallery)します。  
  
Atom (RSS) フィードを拡張機能を含みにフィードを追加するイントラネット上の場所を作成する**拡張機能と更新**をプライベート ギャラリーとして。 詳細については、「[プライベート ギャラリー](../extensibility/private-galleries.md)」を参照してください。  
  
## <a name="creating-an-atom-feed"></a>フィードを Atom の作成  
 Atom をプライベート ギャラリーとしてフィードを作成するには、最初にフォルダーに、拡張機能 (.vsix ファイル) を収集します。 場合は、サブフォルダーにそれらを編成できます。 次のリソースも必要になります。  
  
-   プライベート ギャラリーとして拡張機能を利用できるようにする atom.xml ファイルです。 Atom.xml ファイルに接続する方法については**拡張機能と更新**を参照してください[プライベート ギャラリー](../extensibility/private-galleries.md)します。  
  
-   拡張機能 (たとえば、スクリーン ショット) から抽出されたすべてのイメージ ファイルを格納するフォルダー。 利用できるように、atom.xml ファイルがこれらのイメージへの相対リンクを含む**拡張機能と更新**します。  
  
 たとえば、フォルダーに次の 2 つの拡張機能を収集したとします。  
  
-   Template_Wizard_239.vsix は空の VSIX プロジェクト テンプレートです。  
  
-   SelectionHighlight.vsix は、選択した単語のすべてのインスタンスを強調表示するツールです。  
  
 Atom.xml ファイルの内容を次の例となります。  
  
```  
  <?xml version="1.0" encoding="utf-8" ?>   
- <feed xmlns="http://www.w3.org/2005/Atom">  
  <title type="text" />   
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
  <updated>2011-04-14T21:25:48Z</updated>   
- <entry>  
  <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
  <title type="text">Highlight all occurrences of selected word</title>   
  <summary type="text">This extends the editor to highlight ….</summary>   
  <published>2011-04-14T14:24:51-07:00</published>   
  <updated>2011-04-14T14:24:22-07:00</updated>   
- <author>  
  <name>Microsoft</name>   
  </author>  
  <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />   
  <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />   
  <content type="application/octet-stream" src="SelectionHighlight.vsix" />   
- <Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010">  
  <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>   
  <Version>1.31</Version>   
  <References />   
  <Rating xsi:nil="true" />   
  <RatingCount xsi:nil="true" />   
  <DownloadCount xsi:nil="true" />   
  </Vsix>  
  </entry>  
- <entry>  
  <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>   
  …  
  </entry>  
  </feed>  
  
```  
  
 2 つのリンク タグをイメージの生成されたフォルダーのスクリーン ショットを参照することに注意してください。  
  
## <a name="see-also"></a>関連項目  
 [プライベート ギャラリー](../extensibility/private-galleries.md)

