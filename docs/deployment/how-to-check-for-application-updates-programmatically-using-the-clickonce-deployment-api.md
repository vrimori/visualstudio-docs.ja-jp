---
title: "方法 : ClickOnce 配置 API を使用してアプリケーションの更新プログラムをプログラムで確認する | Microsoft Docs"
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
  - "アプリケーションの更新プログラム"
  - "ClickOnce 配置, 更新"
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法 : ClickOnce 配置 API を使用してアプリケーションの更新プログラムをプログラムで確認する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce には、配置されたアプリケーションを更新する 2 つの方法が用意されています。  1 番目の方法では、一定の間隔で自動的に更新プログラムを確認するように ClickOnce 配置を構成できます。  2 番目の方法では、<xref:System.Deployment.Application.ApplicationDeployment> クラスを使用して、ユーザー要求などのイベントに基づいて更新プログラムを確認するコードを作成できます。  
  
 次の手順では、プログラムによる更新を実行するためのコードを示し、プログラムによる更新プログラムの確認が可能となるように ClickOnce 配置を構成する方法を説明します。  
  
 ClickOnce アプリケーションをプログラムによって更新するには、更新プログラムの場所を指定する必要があります。  これは、配置プロバイダーと呼ばれる場合があります。  このプロパティの設定の詳細については、「[ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)」を参照してください。  
  
> [!NOTE]
>  以下で説明する手法を使用すると、ある場所からアプリケーションを配置し、それを別の場所から更新することもできます。  詳細については、「[方法 : 配置の更新用に別の場所を指定する](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)」を参照してください。  
  
### 更新プログラムの確認をプログラムから行うには  
  
1.  任意のコマンド ライン ツールまたはビジュアル ツールを使用して、新しい Windows フォーム アプリケーションを作成します。  
  
2.  更新プログラムを確認する場合にユーザーが選択するボタン、メニュー項目、またはその他のユーザー インターフェイス項目を作成します。  更新プログラムを確認してインストールするには、その項目のイベント ハンドラーから次のメソッドを呼び出します。  
  
     [!CODE [ClickOnceAPI#6](../CodeSnippet/VS_Snippets_Winforms/ClickOnceAPI#6)]  
  
3.  アプリケーションをコンパイルします。  
  
### プログラムで更新プログラムを確認するアプリケーションを Mage.exe を使用して配置する場合  
  
-   「[チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)」で説明されている、Mage.exe を使用してアプリケーションを配置するための手順に従います。  Mage.exe を呼び出して配置マニフェストを生成する場合は、必ず `providerUrl` コマンド ライン スイッチを使用し、ClickOnce が更新プログラムを確認する URL を指定します。  たとえば、アプリケーションが [http:\/\/www.microsoft.com\/ja\/jp\/default.aspx](http://www.microsoft.com/ja/jp/default.aspx) から更新される場合は、次のような呼び出しによって配置マニフェストを生成します。  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### プログラムで更新プログラムを確認するアプリケーションを MageUI.exe を使用して配置する場合  
  
-   「[チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)」で説明されている、Mage.exe を使用してアプリケーションを配置するための手順に従います。  **\[配置オプション\]** タブで、**\[Start Location\]** フィールドを ClickOnce が更新プログラムを確認するアプリケーション マニフェストに設定します。  **\[更新オプション\]** タブで、**\[アプリケーションの更新プログラムを確認する\]** チェック ボックスをオフにします。  
  
## .NET Framework セキュリティ  
 プログラムによる更新を使用するには、アプリケーションに完全信頼のアクセス許可が必要です。  
  
## 参照  
 [方法 : 配置の更新用に別の場所を指定する](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)