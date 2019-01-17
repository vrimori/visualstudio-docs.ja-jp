---
title: '方法: Atom を作成するプライベート ギャラリーのフィード |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0f761bd99fe13822c0e3a5abdb35be85bd3395ef
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227916"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>方法: Atom プライベート ギャラリーのフィードの作成します。
Atom (RSS) フィードを拡張機能を含みにフィードを追加するイントラネット上の場所を作成する**拡張機能と更新**をプライベート ギャラリーとして。 詳細については、次を参照してください。[プライベート ギャラリー](../extensibility/private-galleries.md)します。  
  
## <a name="create-an-atom-feed"></a>Atom フィードを作成します。  
 Atom をプライベート ギャラリーとしてフィードを作成するを収集して、拡張機能 (*.vsix*ファイル) のフォルダーにします。 場合は、サブフォルダーにそれらを編成できます。 次のリソースも必要になります。  
  
- *Atom.xml*ファイルをプライベート ギャラリーとして拡張機能を利用できるようにします。 接続する方法については、 *atom.xml*ファイルを**拡張機能と更新**を参照してください[プライベート ギャラリー](../extensibility/private-galleries.md)します。  
  
- 拡張機能 (たとえば、スクリーン ショット) から抽出されたすべてのイメージ ファイルを格納するフォルダー。 *Atom.xml*で利用できるように、ファイルがこれらのイメージへの相対リンクを含む**拡張機能と更新**します。  
  
  たとえば、フォルダーに次の 2 つの拡張機能を収集したとします。  
  
- *Template_Wizard_239.vsix*、これは、空の VSIX プロジェクト テンプレート。  
  
- *SelectionHighlight.vsix*、選択した単語のすべてのインスタンスを強調表示するためのツールであります。  
  
  内容、 *atom.xml*ファイルは次の例のようになります。  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>
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
    <Vsix xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
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
  
 2 つのリンク タグをイメージの生成されたフォルダーのスクリーン ショットを参照することに注意してください。  
  
## <a name="see-also"></a>関連項目  
 [プライベート ギャラリー](../extensibility/private-galleries.md)
