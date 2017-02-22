---
title: "方法: ClickOnce のオフラインまたはオンラインのインストール モードを指定する | Microsoft Docs"
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
  - "ClickOnce 配置, 指定 (インストール モードを)"
  - "ClickOnce のインストール モード"
  - "インストール モード"
  - "オフライン アプリケーション"
  - "オンライン アプリケーション"
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法: ClickOnce のオフラインまたはオンラインのインストール モードを指定する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションの `Install Mode` は、アプリケーションをオフラインで利用できるか、またはオンラインで利用できるかを指定します。  **\[アプリケーションはオンラインでのみ利用できる\]** を選択した場合、ユーザーは、アプリケーションを実行するために [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] の発行場所 \(Web ページまたはファイル共有\) へのアクセス許可を持っている必要があります。  **\[アプリケーションはオフラインでも利用できる\]** を選択した場合、アプリケーションは **\[スタート\]** メニューと **\[プログラムの追加と削除\]** ダイアログ ボックスにエントリを追加します。ユーザーは、ネットワークに接続していなくてもアプリケーションを実行できます。  
  
 `Install Mode` は、**プロジェクト デザイナー**の **\[発行\]** ページで設定できます。  
  
 **メモ** `Install Mode` は、発行ウィザードを使用して設定することもできます。  詳細については、「[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)」を参照してください。  
  
### ClickOnce アプリケーションをオンラインでのみ利用できるようにするには  
  
1.  **ソリューション エクスプローラー**でプロジェクトが選択されている状態で、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
2.  **\[発行\]** タブをクリックします。  
  
3.  **\[インストール モードと設定\]** 領域の **\[アプリケーションはオンラインでのみ利用できる\]** をクリックします。  
  
### ClickOnce アプリケーションをオンラインでもオフラインでも利用できるようにするには  
  
1.  **ソリューション エクスプローラー**でプロジェクトが選択されている状態で、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
2.  **\[発行\]** タブをクリックします。  
  
3.  **\[インストール モードと設定\]** 領域の **\[アプリケーションはオフラインでも利用できる\]** を選択します。  
  
     インストール時に、アプリケーションは **\[スタート\]** メニューと \[コントロール パネル\] の **\[プログラムの追加と削除\]** にエントリを追加します。  
  
## 参照  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)   
 [ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)