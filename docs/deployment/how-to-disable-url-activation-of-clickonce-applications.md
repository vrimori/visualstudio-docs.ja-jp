---
title: "方法 : ClickOnce アプリケーションの URL アクティべーションを無効にする | Microsoft Docs"
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
  - "ClickOnce 配置, URL アクティベーション"
  - "disallowUrlActivation"
  - "URL アクティベーション, ClickOnce アプリケーション"
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法 : ClickOnce アプリケーションの URL アクティべーションを無効にする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通常、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションは Web サーバーからインストールされた直後に自動的に起動します。  ただし、セキュリティ上の理由から、この動作を無効にすることもできます。その場合は、**\[スタート\]** メニューからアプリケーションを起動するようにユーザーに通知します。  次の手順では、URL アクティベーションを無効にする方法を説明します。  
  
 この手法は、Web サーバーからユーザーのコンピューターにインストールされた [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションにのみ使用できます。  URL を使用する方法でのみ起動できるオンライン専用のアプリケーションには使用できません。  オンライン専用アプリケーションとインストールされたアプリケーションの違いの詳細については、「[ClickOnce 配置ストラテジの選択](../deployment/choosing-a-clickonce-deployment-strategy.md)」を参照してください。  
  
 この手順では、[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] ツールである MageUI.exe を使用します。  このツールの詳細については、「[MageUI.exe \(マニフェスト生成および編集ツールのグラフィカル クライアント\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)」を参照してください。  この手順は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を使用して実行することもできます。  
  
## プロシージャ  
  
#### アプリケーションの URL アクティベーションを無効にするには  
  
1.  MageUI.exe で配置マニフェストを開きます。  まだ作成していない場合は、「[チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)」の手順に従います。  
  
2.  **\[配置オプション\]** タブを選択します。  
  
3.  **\[インストール後にアプリケーションを自動的に実行する\]** チェックボックスをオフにします。  
  
4.  マニフェストを保存し、署名します。  
  
## 参照  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)