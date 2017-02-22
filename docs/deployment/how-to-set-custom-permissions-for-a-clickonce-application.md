---
title: "方法 : ClickOnce アプリケーションのカスタム アクセス許可を設定する | Microsoft Docs"
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
  - "ClickOnce アプリケーション, アクセス許可"
  - "アクセス許可, ClickOnce アプリケーション"
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法 : ClickOnce アプリケーションのカスタム アクセス許可を設定する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

インターネット ゾーンまたはローカル イントラネット ゾーンの既定のアクセス許可を使用する [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを配置できます。 または、アプリケーションに必要な特定のアクセス許可用にカスタム ゾーンを作成することもできます。 そのためには、**プロジェクト デザイナー**の **\[セキュリティ\]** ページでセキュリティのアクセス許可をカスタマイズします。  
  
### アクセス許可をカスタマイズするには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
2.  **\[セキュリティ\]** タブをクリックします。  
  
3.  **\[ClickOnce セキュリティ設定を有効にする\]** チェック ボックスをオンにします。  
  
4.  **\[これは部分的に信頼するアプリケーションです\]** オプション ボタンを選択します。  
  
     **\[ClickOnce セキュリティのアクセス許可\]** セクション内のコントロールが有効になります。  
  
5.  **\[アプリケーションのインストール元のゾーン\]** ドロップダウン リストの **\[\(カスタム\)\]** を選択します。  
  
6.  **\[アクセス許可 XML の編集\]** をクリックします。  
  
     XML エディターで app.manifest ファイルが開きます。  
  
7.  `</applicationRequestMinimum>` 要素の前に、アプリケーションに必要なアクセス許可の XML コードを追加します。  
  
    > [!NOTE]
    >  アクセス許可セットの `ToXml` メソッドを使用して、アプリケーション マニフェスト用の XML コードを生成できます。 たとえば、<xref:System.Security.Permissions.EnvironmentPermission> アクセス許可セットの XML を生成するには、<xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> メソッドを呼び出します。 アクセス許可セット XML の構造の詳細については、「[NIB: 方法: XML ファイルを使用してアクセス許可セットをインポートする](http://msdn.microsoft.com/ja-jp/dea16b54-c108-408a-ac36-cdc05f746236)」をご覧ください。  
  
## 参照  
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)   
 [ClickOnce アプリケーションのコード アクセス セキュリティ](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)