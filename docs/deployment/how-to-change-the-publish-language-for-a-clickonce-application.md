---
title: "方法 : ClickOnce アプリケーションの発行言語を変更する | Microsoft Docs"
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
  - "ClickOnce 配置, 変更 (発行言語を)"
  - "[発行の言語] プロパティ"
  - "発行, ClickOnce"
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法 : ClickOnce アプリケーションの発行言語を変更する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを発行するとき、インストール中に表示されるユーザー インターフェイスは、既定で開発用コンピューターの言語とカルチャに設定されます。  ローカライズされたアプリケーションを発行する場合、ローカライズされたバージョンに合わせて言語とカルチャを指定する必要があります。  これは、プロジェクトの `Publish language` プロパティによって決定されます。  
  
 `Publish language` プロパティは、**プロジェクト デザイナー**の **\[発行\]** ページから表示できる **\[発行オプション\]** ダイアログ ボックスで設定します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### 発行言語を変更するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトが選択されている状態で、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
2.  **\[発行\]** タブをクリックします。  
  
3.  **\[オプション\]** をクリックして **\[発行オプション\]** ダイアログ ボックスを開きます。  
  
4.  **\[説明\]** をクリックします。  
  
5.  **\[発行オプション\]** ダイアログ ボックスの **\[発行の言語\]** ボックスの一覧で言語とカルチャを選択し、**\[OK\]** をクリックします。  
  
## 参照  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)