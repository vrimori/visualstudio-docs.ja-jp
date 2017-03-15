---
title: "方法 : ClickOnce アプリケーションのファイルの関連付けを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 配置, ファイルの関連付け"
  - "ファイルの関連付け, ClickOnce アプリケーション"
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法 : ClickOnce アプリケーションのファイルの関連付けを作成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを 1 つまたは複数のファイル名拡張子に関連付けることができるため、ユーザーがファイルを開くと、その種類に対応するアプリケーションが自動的に開始します。  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションへのファイル名拡張子サポートの追加は簡単です。  
  
### ClickOnce アプリケーションのファイルの関連付けを作成するには  
  
1.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを通常の方法で作成するか、既存の [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを使用します。  
  
2.  アプリケーション マニフェストをメモ帳などのテキスト エディターや XML エディターで開きます。  
  
3.  `assembly` 要素を検索します。  詳細については、「[ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)」を参照してください。  
  
4.  `assembly` 要素の子として `fileAssociation` 要素を追加します。  `fileAssociation` 要素には 4 つの属性があります。  
  
    -   `extension` : アプリケーションに関連付けるファイル名拡張子。  
  
    -   `description` : Windows シェルに表示される、ファイルの種類に関する説明。  
  
    -   `progid` : レジストリ内でマークするためにファイルの種類を一意に識別する文字列値。  
  
    -   `defaultIcon` : このファイルの種類に使用するアイコン。  アイコンは、アプリケーション マニフェストにファイル リソースとして追加する必要があります。  詳細については、「[方法 : ClickOnce アプリケーションにデータ ファイルを含める](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)」を参照してください。  
  
     `file` 要素および `fileAssociation` 要素の例については、「[\<fileAssociation\> 要素](../deployment/fileassociation-element-clickonce-application.md)」を参照してください。  
  
5.  アプリケーションに複数のファイルの種類を関連付けるには、さらに `fileAssociation` 要素を追加します。  `progid` 属性は、それぞれ異なることに注意してください。  
  
6.  アプリケーション マニフェストの作業が終了したら、マニフェストに再び署名します。  この操作は、Mage.exe を使用してコマンド ラインから実行できます。  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     詳細については、「[Mage.exe \(マニフェストの生成および編集ツール\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)」を参照してください。  
  
## 参照  
 [\<fileAssociation\> 要素](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)   
 [Mage.exe \(マニフェストの生成および編集ツール\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)