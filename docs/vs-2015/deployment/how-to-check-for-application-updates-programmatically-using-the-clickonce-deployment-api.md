---
title: '方法: ClickOnce 配置 API を使用してプログラムでアプリケーションの更新プログラムの確認 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ecb3ba8e0fd05e0fb0cd79cde32abe235af743e2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533363"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>方法 : ClickOnce 配置 API を使用してアプリケーションの更新プログラムをプログラムで確認する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: ClickOnce 配置 API のアプリケーションの更新プログラムを使用してプログラムで確認](https://docs.microsoft.com/visualstudio/deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api)します。  
  
ClickOnce では、デプロイ後にアプリケーションを更新する 2 つの方法を提供します。 最初のメソッドでは、一定の間隔で更新を自動的にチェックする ClickOnce 配置を構成できます。 2 番目のメソッドを使用するコードを記述することができます、<xref:System.Deployment.Application.ApplicationDeployment>更新をチェックするクラス、ユーザーの要求など、イベントに基づいています。  
  
 次の手順は、プログラムによる更新プログラムを実行するためのいくつかのコードを示し、プログラムによる更新プログラムのチェックを有効にする、clickonce による配置を構成する方法についても説明します。 します。  
  
 ClickOnce アプリケーションをプログラムで更新するには、更新プログラムの場所を指定する必要があります。 これは、配置プロバイダーと呼ばれます。 このプロパティの設定の詳細については、次を参照してください。 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)します。  
  
> [!NOTE]
>  以下から別の更新に 1 つの場所からアプリケーションをデプロイしで説明する手法を使用することもできます。 詳細については、次を参照してください。[方法: 配置の更新用の別の場所の指定](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)します。  
  
### <a name="to-check-for-updates-programmatically"></a>プログラムで更新プログラムを確認するには  
  
1.  任意のコマンドラインまたは visual ツールを使用して、新しい Windows フォーム アプリケーションを作成します。  
  
2.  ボタン、メニュー項目を作成またはその他のユーザー インターフェイス項目を選択して更新プログラムを確認するユーザーをします。 その項目のイベント ハンドラーからの確認し、更新プログラムをインストールするには、次のメソッドを呼び出します。  
  
     [!code-cpp[ClickOnceAPI#6](../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp#6)]
     [!code-csharp[ClickOnceAPI#6](../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs#6)]
     [!code-vb[ClickOnceAPI#6](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb#6)]  
  
3.  アプリケーションをコンパイルします。  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Mage.exe を使用してプログラムで更新プログラムを確認するアプリケーションを展開するには  
  
-   説明したように、Mage.exe を使用してアプリケーションをデプロイするための指示に従って[チュートリアル: ClickOnce アプリケーションを手動で配置](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)します。 配置マニフェストを生成する Mage.exe を呼び出すときに、コマンド ライン スイッチを使用することを確認してように`providerUrl`ClickOnce が更新プログラムを確認する URL を指定するとします。 アプリケーションから更新する場合[ http://www.adatum.com/MyApp ](http://www.adatum.com/MyApp)、たとえば、配置マニフェストを生成する呼び出しが、これのようになります。  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>MageUI.exe を使用してプログラムで更新プログラムを確認するアプリケーションを展開するには  
  
-   説明したように、Mage.exe を使用してアプリケーションをデプロイするための指示に従って[チュートリアル: ClickOnce アプリケーションを手動で配置](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)します。 **展開オプション**タブで、設定、**開始場所**フィールドをアプリケーション マニフェストが ClickOnce が更新プログラムを確認する必要があります。 **更新オプション**タブで、、**アプリケーションの更新プログラムを確認する必要があります**チェック ボックスをオンします。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 アプリケーションは、プログラムによる更新を使用する完全な信頼アクセス許可が必要です。  
  
## <a name="see-also"></a>関連項目  
 [方法: 配置の更新用の別の場所の指定](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [ClickOnce の更新方法を選択します。](../deployment/choosing-a-clickonce-update-strategy.md)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)



