---
title: "方法: エンド ユーザーがインストールを開始する場所を指定する | Microsoft Docs"
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
  - "配置 (アプリケーションを) [ClickOnce], 指定 (インストール URL を)"
  - "Installation URL プロパティ"
  - "インストール, 指定 (インストール URL を)"
  - "URL, 指定 (インストール URL を)"
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法: エンド ユーザーがインストールを開始する場所を指定する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを発行するとき、ユーザーがアプリケーションをダウンロードおよびインストールするためにアクセスする場所は、必ずしもアプリケーションを最初に発行する場所である必要はありません。  たとえば、組織によっては、開発者がアプリケーションをステージング サーバーに発行した後、管理者がアプリケーションを Web サーバーに移動する場合もあります。  
  
 そのような場合には、`Installation URL` プロパティを使用して、ユーザーがアプリケーションをダウンロードするためにアクセスする Web サーバーを指定できます。  これは、アプリケーションのマニフェストに更新プログラムを検索する場所を認識させるために必要です。  
  
 `Installation URL` プロパティは、**プロジェクト デザイナー**の **\[発行\]** ページで設定できます。  
  
 **注意** `Installation URL` プロパティは、**発行ウィザード**を使用して設定することもできます。  詳細については、「[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)」を参照してください。  
  
### インストール URL を指定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトが選択されている状態で、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
2.  **\[発行\]** タブをクリックします。  
  
3.  \[インストールの URL\] フィールドに、http:\/\/www.microsoft.com\/ApplicationName の形式の完全修飾 URL を使用するか、または \\\\Server\\ApplicationName の形式の UNC パスを使用して、インストール場所を入力します。  
  
## 参照  
 [方法: Visual Studio がファイルをコピーする場所を指定する](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)