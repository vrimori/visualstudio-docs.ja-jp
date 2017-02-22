---
title: "方法 : ClickOnce の発行バージョンを自動的にインクリメントする | Microsoft Docs"
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
  - "ClickOnce 配置, インクリメント (発行バージョンを自動的に)"
  - "配置 (アプリケーションを) [ClickOnce], インクリメント (発行バージョンを自動的に)"
  - "Publish Version プロパティ, インクリメント"
  - "発行, ClickOnce"
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法 : ClickOnce の発行バージョンを自動的にインクリメントする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを発行するとき、`Publish Version` プロパティを変更すると、アプリケーションが更新プログラムとして発行されます。  既定では、アプリケーションを発行するたびに `Publish Version` の`Revision` 番号が自動的にインクリメントされます。  
  
 この動作は、**プロジェクト デザイナー**の **\[発行\]** ページで無効にできます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### Publish Version の自動インクリメントを無効にするには  
  
1.  **ソリューション エクスプローラー**でプロジェクトが選択されている状態で、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
2.  **\[発行\]** タブをクリックします。  
  
3.  **\[発行するバージョン\]** セクションの **\[リリースごとにリビジョンを自動的に追加する\]** チェック ボックスをオフにします。  
  
## 参照  
 [方法 : ClickOnce の発行バージョンを設定する](../Topic/How%20to:%20Set%20the%20ClickOnce%20Publish%20Version.md)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)