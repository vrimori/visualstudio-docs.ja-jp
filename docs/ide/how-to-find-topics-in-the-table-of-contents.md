---
title: "方法 : 目次でトピックを検索する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "hv_contents"
helpviewer_keywords: 
  - "目次タブ [ヘルプ ビューアー 2.0]"
  - "ヘルプ ビューアー 2.0, 目次タブ"
  - "ヘルプ ビューアー 2.0, 目次のフィルタリング"
  - "目次のフィルタリング [ヘルプ ビューアー 2.0]"
ms.assetid: 8b98464d-2b05-4710-ad68-5647e78c6b7b
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 方法 : 目次でトピックを検索する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**\[目次\]** タブでは、目次 \(TOC\) を使用して情報を検索できます。  目次は、インストールしたブックに関するトピックをすべて含む、拡張可能なリストです。  TOC 内の移動方法に関するユーザー補助情報については、「[ショートカット キー \(ヘルプ ビューアー\)](../ide/shortcut-keys-help-viewer.md)」を参照してください。  
  
> [!IMPORTANT]
>  TOC で使用できるトピックの範囲は、選択したフィルターによって異なります。  
  
## TOC のフィルター処理  
 TOC をフィルター処理して、**\[目次\]** タブに表示されるトピックの範囲を絞り込むことができます。  指定した用語のルートがタイトルに含まれている場合にのみ、一覧にタイトルが表示されます。  たとえば、フィルターとして「troubleshooting」を指定すると、「troubleshoot」または「troubleshooting」を含むタイトルのみが表示されます。  タイトルに用語が含まれないノードは、省略記号 \(...\) と共に単一のノードに折りたたまれます。  
  
#### TOC をフィルター処理するには  
  
1.  **\[目次\]** タブをクリックします。  
  
2.  **\[フィルターの内容\]** ボックスに、用語を入力します。  
  
> [!NOTE]
>  フィルターの実行に時間がかかる場合は、高度な検索演算子 `title:` を使用すると、結果がすばやく表示される場合があります。  
  
## TOC とのトピックの同期  
 インデックスまたはフルテキストの検索機能を使用してトピックを開いている場合は、トピック ウィンドウと TOC を同期させることによって、TOC のどこにこのトピックがあるかを特定できます。  
  
#### TOC をトピック ウィンドウと同期させるには  
  
1.  トピックを表示します。  
  
2.  ツール バーの \[**目次のトピックを表示**\] ボタンをクリックするか、次のキーを押します                                                            Ctrl \+ S                                                           .  
  
     **\[目次\]** タブが開き、TOC 内のトピックの場所が表示されます。  
  
## 参照  
 [情報の検索](../ide/locate-information.md)   
 [Microsoft ヘルプ ビューアー](../ide/microsoft-help-viewer.md)