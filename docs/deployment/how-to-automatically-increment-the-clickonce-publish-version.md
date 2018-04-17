---
title: '方法: 発行のバージョンに自動的にインクリメント ClickOnce |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 0a0cc134dbed973681ed43830435a6ce5ae0331c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>方法: ClickOnce の発行バージョンを自動的にインクリメントする
発行するときに、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションでは、変更、`Publish Version`プロパティにより、アプリケーションの更新プログラムとして発行されます。 既定では、Visual Studio が自動的にインクリメント、`Revision`数、`Publish Version`アプリケーションを発行するたびにします。  
  
 この動作を無効にすることができます、**発行**のページ、**プロジェクト デザイナー**です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>発行バージョンを自動的にインクリメントを無効にするには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  **発行するバージョン** セクションで、クリア、**リリースごとにリビジョンを自動的に**チェック ボックスをオンします。  
  
## <a name="see-also"></a>関連項目  
 [方法: ClickOnce の発行バージョンを設定する](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)