---
title: "方法 : ClickOnce のセキュリティ設定を有効にする | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "ClickOnce 配置, セキュリティ設定"
  - "セキュリティ [Visual Studio], ClickOnce アプリケーション"
  - "セキュリティ設定, ClickOnce 配置"
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法 : ClickOnce のセキュリティ設定を有効にする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce アプリケーションを発行するためには、アプリケーションのコード アクセス セキュリティを有効にする必要があります。  発行ウィザードを使用してアプリケーションを発行する場合、この作業は自動的に行われます。  
  
 場合によっては、コード アクセス セキュリティを有効にすることにより、アプリケーションのビルド時やデバッグ時のパフォーマンスに影響が出ることがあります。そのような場合には、セキュリティ設定を一時的に無効にできます。  
  
 ClickOnce のセキュリティ設定は、**プロジェクト デザイナー**の **\[セキュリティ\]** ページで有効にできます。  
  
### ClickOnce のセキュリティ設定を有効にするには  
  
1.  **ソリューション エクスプローラー**でプロジェクトが選択されている状態で、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
2.  **\[セキュリティ\]** タブをクリックします。  
  
3.  **\[ClickOnce セキュリティ設定を有効にする\]** チェック ボックスをオンにします。  
  
     \[セキュリティ\] ページで、アプリケーションのセキュリティ設定をカスタマイズできます。  
  
    > [!NOTE]
    >  このチェック ボックスは、**発行**ウィザードを使用してアプリケーションが発行されるたびに自動的にオンにされます。  
  
### ClickOnce のセキュリティ設定を無効にするには  
  
1.  **ソリューション エクスプローラー**でプロジェクトが選択されている状態で、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
2.  **\[セキュリティ\]** タブをクリックします。  
  
3.  **\[ClickOnce セキュリティ設定を有効にする\]** チェック ボックスをオフにします。  
  
     アプリケーションは完全に信頼されているセキュリティ設定で実行されます。**\[セキュリティ\]** ページの設定はすべて無視されます。  
  
    > [!NOTE]
    >  このチェック ボックスは、発行ウィザードを使用してアプリケーションが発行されるたびにオンにされるため、発行に成功するたびに再びオフにする必要があります。  
  
## 参照  
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)   
 [ClickOnce アプリケーションのコード アクセス セキュリティ](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)