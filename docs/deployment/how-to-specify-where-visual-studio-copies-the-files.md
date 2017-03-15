---
title: "方法: Visual Studio がファイルをコピーする場所を指定する | Microsoft Docs"
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
  - "Publish Location プロパティ"
  - "発行, 指定 (場所を)"
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法: Visual Studio がファイルをコピーする場所を指定する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce を使用してアプリケーションを発行する場合、`Publish Location` プロパティによってアプリケーション ファイルとマニフェストが配置される場所が指定されます。  これには、ファイル パスまたは FTP サーバーへのパスを指定できます。  
  
 `Publish Location`\[プロジェクト デザイナー\] の **\[発行\]** ページで、または、発行ウィザードを使用して  **プロパティを指定することができます。** 詳細については、「[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)」を参照してください。  
  
> [!NOTE]
>  ClickOnce を使用してアプリケーションの複数のバージョンをインストールすると、以前のバージョンのアプリケーションは、指定した発行場所の Archive というフォルダーに移されます。  以前のバージョンがこのようにアーカイブされることで、インストール ディレクトリが以前のバージョンのフォルダーから分離されます。  
  
### 発行場所を指定するには  
  
1.  **ソリューション エクスプ ローラー**で、プロジェクトを選択し、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
2.  **\[発行\]** タブをクリックします。  
  
3.  **\[発行場所\]** フィールドに、次の形式のいずれかを使用して、発行場所を入力します。  
  
    -   ファイル共有またはディスク パスを発行するには、UNC パス \(\\\\Server\\ApplicationName\) またはファイル パス \(C:\\Deploy\\ApplicationName\) のいずれかを使用して、パスを入力します。  
  
    -   FTP サーバーを発行するには、ftp:\/\/ftp.microsoft.com\/ApplicationName という形式を使用して、パスを入力します。  
  
     **\[発行場所\]** ボックスでは、テキストは参照 \(**\[...\]**\) ボタンが機能する順番で並んでいる必要があります。  
  
## 参照  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)