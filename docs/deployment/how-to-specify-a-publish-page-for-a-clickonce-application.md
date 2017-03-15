---
title: "方法 : ClickOnce アプリケーションの発行ページを指定する | Microsoft Docs"
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
  - "ClickOnce 配置, 指定 (発行ページを)"
  - "配置 (アプリケーションを) [ClickOnce], 指定 (発行ページを)"
  - "Publish Page プロパティ"
  - "発行, ClickOnce"
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# 方法 : ClickOnce アプリケーションの発行ページを指定する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを発行するとき、既定の Web ページ \(publish.htm\) が生成され、アプリケーションと共に発行されます。  このページには、アプリケーションの名前、アプリケーションや必須コンポーネント \(指定されている場合\) をインストールするためのリンク、および、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] について説明するヘルプ トピックへのリンクが含まれています。  プロジェクトの **"ページの発行"** プロパティで、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションの Web ページの名前を指定できます。  
  
 発行ページを指定すると、次に発行したときにそのページが発行場所にコピーされます。再び発行してもページは上書きされません。  ページの外観をカスタマイズする場合は、変更内容を失うことなくカスタマイズを実行できます。  詳細については、「[方法 : ClickOnce の既定の Web ページをカスタマイズする](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)」を参照してください。  
  
 **"ページの発行"** プロパティは、**\[発行オプション\]** ダイアログ ボックスで設定できます。このダイアログ ボックスは、**プロジェクト デザイナー**の **\[発行\]** ペインからアクセスできます。  
  
### ClickOnce アプリケーションにカスタム Web ページを指定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトが選択されている状態で、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
2.  **\[発行\]** ペインをクリックします。  
  
3.  **\[オプション\]** をクリックして **\[発行オプション\]** ダイアログ ボックスを開きます。  
  
4.  **\[配置\]** をクリックします。  
  
5.  **\[発行オプション\]** ダイアログ ボックスで、**\[発行後に配置 Web ページを開く\]** チェック ボックスがオンであることを確認します \(既定ではオンです\)。  
  
6.  **\[配置 Web ページ:\]** ボックスに Web ページの名前を入力し、**\[OK\]** をクリックします。  
  
### 発行するたびに発行ページが起動されないようにするには  
  
1.  **ソリューション エクスプローラー**でプロジェクトが選択されている状態で、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
2.  **\[発行\]** ペインをクリックします。  
  
3.  **\[オプション\]** をクリックして **\[発行オプション\]** ダイアログ ボックスを開きます。  
  
4.  **\[配置\]** をクリックします。  
  
5.  **\[発行オプション\]** ダイアログ ボックスで、**\[発行後に配置 Web ページを開く\]** チェック ボックスをオフにします。  
  
## 参照  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)   
 [方法 : ClickOnce の既定の Web ページをカスタマイズする](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)