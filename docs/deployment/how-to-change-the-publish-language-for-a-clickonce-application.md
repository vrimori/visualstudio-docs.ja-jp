---
title: '方法: 変更、ClickOnce アプリケーションの発行の言語 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3395d0b7bbed5ec1d20e0d04894e439a9a27a15d
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154662"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>方法: ClickOnce アプリケーションの発行の言語を変更します。
発行するときに、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション、ユーザー インターフェイスの言語と開発用コンピューターのカルチャの既定のインストール中に表示されます。 ローカライズされたアプリケーションを発行する場合は、言語とローカライズされたバージョンと一致するカルチャを指定する必要があります。 これによって決定されますが、`Publish language`プロジェクトのプロパティ。  
  
 `Publish language`でプロパティを設定できる、**発行オプション**からアクセスできるダイアログ ボックス、**発行**のページ、**プロジェクト デザイナー**します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
### <a name="to-change-the-publish-language"></a>発行の言語を変更するには  
  
1.  **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **発行**タブをクリックします。  
  
3.  **オプション**ボタンをクリックして、**発行オプション** ダイアログ ボックスを開きます。  
  
4.  **説明**をクリックします。  
  
5.  **発行オプション** ダイアログ ボックスで、言語を選択し、カルチャから、**発行の言語**ドロップダウン リストをクリック**OK**します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションを発行します。](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションの発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)