---
title: "方法 : ClickOnce アプリケーションのスタート メニューの名前を指定する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "ClickOnce 配置, スタート メニューの名前"
  - "スタート メニューの名前"
  - "スタート メニューのリソース名"
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : ClickOnce アプリケーションのスタート メニューの名前を指定する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションがオンラインとオフラインの両方で利用できるようにインストールされると、**\[スタート\]** メニューと **\[プログラムの追加と削除\]** の一覧にエントリが追加されます。  既定では、表示名がアプリケーション アセンブリの名前と同じになりますが、**\[発行オプション\]** ダイアログ ボックスで **\[製品名\]** を設定すると、表示名を変更できます。  
  
 **\[製品名\]** は publish.htm ページに表示されます。インストールされたオフライン アプリケーションの場合は、それが **\[開始\]** メニューの項目と、**\[プログラムの追加と削除\]** に表示される名前になります。  
  
 **\[発行者名\]** は、publish.htm ページの **\[製品名\]** の上に表示されます。インストールされたオフライン アプリケーションの場合は、それが **\[開始\]** メニューでのアプリケーション アイコンの配置先のフォルダー名になります。  
  
 **\[製品名\]** プロパティと **\[発行者名\]** プロパティは、**プロジェクト デザイナー**の **\[発行\]** ページから使用できる **\[発行オプション\]** ダイアログ ボックスで設定できます。  
  
### スタート メニューに表示する名前を指定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトが選択されている状態で、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
2.  **\[発行\]** タブをクリックします。  
  
3.  **\[オプション\]** をクリックして **\[発行オプション\]** ダイアログ ボックスを開きます。  
  
4.  **\[説明\]** をクリックします。  
  
5.  **\[発行オプション\]** ダイアログ ボックスで、**\[製品名\]** に表示名を入力します。  
  
6.  必要な場合は、**\[発行者名\]** に発行者名を入力します。  
  
## 参照  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)