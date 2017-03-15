---
title: "方法: Atom を作成するプライベート ギャラリーのフィード | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Atom フィード、VSIX 非公開のギャラリー"
  - "VSIX 非公開のギャラリー、Atom フィード"
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 方法: Atom を作成するプライベート ギャラリーのフィード
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Atom \(RSS\) フィードで拡張機能を含みにフィードを追加するイントラネット上の場所を作成する **拡張機能と更新プログラム** プライベート ギャラリーとします。 詳細については、「[プライベート ギャラリー](../extensibility/private-galleries.md)」を参照してください。  
  
## フィードを Atom を作成します。  
 Atom フィードをプライベート ギャラリーを作成するには、フォルダーにまず、拡張機能 \(.vsix ファイル\) を収集するだけです。 場合は、サブフォルダーにまとめてを整理できます。 次のリソースも必要になります。  
  
-   プライベート ギャラリーと拡張機能を利用できるようにする atom.xml ファイルです。 Atom.xml ファイルに接続する方法については **拡張機能と更新プログラム**, を参照してください [プライベート ギャラリー](../extensibility/private-galleries.md)します。  
  
-   拡張 \(スクリーン ショットなど\) から抽出されたすべてのイメージ ファイルを格納するフォルダー。 使用できるように、atom.xml ファイルがこれらのイメージへの相対リンクを含む **拡張機能と更新プログラム**します。  
  
 たとえば、フォルダーに次の 2 つの拡張子を収集したとします。  
  
-   Template\_Wizard\_239.vsix は空の VSIX プロジェクト テンプレートです。  
  
-   SelectionHighlight.vsix を選択した単語のすべてのインスタンスを強調表示するツールです。  
  
 Atom.xml ファイルの内容には、次の例は似ています。  
  
```  
  <?xml version="1.0" encoding="utf-8" ?> - <feed xmlns="http://www.w3.org/2005/Atom"> <title type="text" /> <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id> <updated>2011-04-14T21:25:48Z</updated> - <entry> <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id> <title type="text">Highlight all occurrences of selected word</title> <summary type="text">This extends the editor to highlight ….</summary> <published>2011-04-14T14:24:51-07:00</published> <updated>2011-04-14T14:24:22-07:00</updated> - <author> <name>Microsoft</name> </author> <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" /> <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" /> <content type="application/octet-stream" src="SelectionHighlight.vsix" /> - <Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010"> <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id> <Version>1.31</Version> <References /> <Rating xsi:nil="true" /> <RatingCount xsi:nil="true" /> <DownloadCount xsi:nil="true" /> </Vsix> </entry> - <entry> <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id> … </entry> </feed>  
  
```  
  
 2 つのリンクのタグがイメージの生成されたフォルダーにスクリーン ショットを参照しているに注意してください。  
  
## 参照  
 [プライベート ギャラリー](../extensibility/private-galleries.md)