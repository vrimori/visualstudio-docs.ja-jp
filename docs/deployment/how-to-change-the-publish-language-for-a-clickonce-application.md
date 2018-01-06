---
title: "方法: 変更、ClickOnce アプリケーションの発行の言語 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
caps.latest.revision: "19"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 7d368f036e8a5f8599a802bb6f57eba7bc6d767d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>方法: ClickOnce アプリケーションの発行言語を変更する
発行するときに、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション、ユーザー インターフェイスの言語と、開発用コンピューターのカルチャに既定のインストール中に表示されます。 ローカライズされたアプリケーションを発行する場合は、言語とローカライズされたバージョンと一致するカルチャを指定する必要があります。 これによって決定されますが、`Publish language`プロジェクトのプロパティです。  
  
 `Publish language`プロパティを設定することができます、**発行オプション**ダイアログ ボックスからアクセスできる、**発行**のページ、**プロジェクト デザイナー**です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
### <a name="to-change-the-publish-language"></a>発行の言語を変更するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  クリックして、**発行**タブです。  
  
3.  クリックして、**オプション**を開く ボタン、**発行オプション** ダイアログ ボックス。  
  
4.  をクリックして**説明**です。  
  
5.  **発行オプション** ダイアログ ボックス、言語を選択してからカルチャ、**発行の言語**クリックしてドロップダウン リスト**OK**です。  
  
## <a name="see-also"></a>参照  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)