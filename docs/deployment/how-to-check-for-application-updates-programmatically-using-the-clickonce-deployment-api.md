---
title: '方法: ClickOnce 配置 API を使用してプログラムでアプリケーションの更新プログラムの確認 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5953af7c6aafe914be409d8c3ab459b6b4261e54
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>方法 : ClickOnce 配置 API を使用してアプリケーションの更新プログラムをプログラムで確認する
ClickOnce を展開した後にアプリケーションを更新する 2 つの方法を提供します。 最初のメソッドでは、一定の間隔で更新プログラムを自動的に確認し、ClickOnce 配置を構成できます。 2 番目のメソッドを使用するコードを記述することができます、<xref:System.Deployment.Application.ApplicationDeployment>ユーザーの要求など、イベントに基づいて、更新プログラムを確認するクラス。  
  
 次の手順では、プログラムで更新プログラムを実行するためのいくつかのコードを表示してをプログラムで更新プログラムのチェックを有効にする、ClickOnce 配置を構成する方法についても説明します。  
  
 ClickOnce アプリケーションをプログラムで更新するのには、更新プログラムの場所を指定する必要があります。 これは、配置プロバイダーと呼ばれます。 このプロパティを設定する方法の詳細については、次を参照してください。 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)です。  
  
> [!NOTE]
>  1 つの場所からアプリケーションの展開が、別の更新を次に示す手法を使用することもできます。 詳細については、次を参照してください。[する方法: 配置の更新用の別の場所の指定](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)です。  
  
### <a name="to-check-for-updates-programmatically"></a>プログラムで更新プログラムを確認するには  
  
1.  優先されるコマンド ライン ツールまたはビジュアル ツールを使用して新しい Windows フォーム アプリケーションを作成します。  
  
2.  ボタン、メニュー項目を作成またはその他のユーザー インターフェイス項目ようにする、更新プログラムを確認する場合に選択します。 その項目のイベント ハンドラーからの確認し、更新プログラムをインストールするには、次のメソッドを呼び出します。  
  
     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]  
  
3.  アプリケーションをコンパイルします。  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Mage.exe を使用してプログラムで更新プログラムをチェックするアプリケーションを展開するには  
  
-   説明したように、Mage.exe を使用してアプリケーションを展開するための指示に従って[チュートリアル: ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)です。 配置マニフェストを生成する Mage.exe を呼び出すときに必ず使用してコマンド ライン スイッチ`providerUrl`ClickOnce が更新プログラムを確認する URL を指定するとします。 アプリケーションが更新される場合[ http://www.adatum.com/MyApp ](http://www.adatum.com/MyApp)、たとえば、配置マニフェストを生成する、呼び出しが、次のようになります。  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>MageUI.exe を使用してプログラムで更新プログラムをチェックするアプリケーションを展開するには  
  
-   説明したように、Mage.exe を使用してアプリケーションを展開するための指示に従って[チュートリアル: ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)です。 **展開オプション** タブで、設定、**開始場所**フィールドをアプリケーション マニフェストが ClickOnce が更新プログラムを確認する必要があります。 **更新オプション**タブで、、**アプリケーションの更新プログラムを確認する必要があります**チェック ボックスをオンします。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 アプリケーションには、プログラムによる更新を使用する完全な信頼アクセス許可が必要です。  
  
## <a name="see-also"></a>関連項目  
 [方法: 配置の更新用の別の場所の指定](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [ClickOnce の更新方法の選択](../deployment/choosing-a-clickonce-update-strategy.md)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)