---
title: '方法: Office ソリューションに署名します。'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 076cfcb6b63d650665e79a1e2d522595d4a82922
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804696"
---
# <a name="how-to-sign-office-solutions"></a>方法: Office ソリューションに署名します。
  ソリューションに署名する場合は、証拠として、証明書を使用してソリューションに信頼を付与できます。 複数のソリューションに対して、同じ証明書を使用して追加のセキュリティ ポリシーの更新プログラムのないすべてのソリューションが信頼されます。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 および配置が、マニフェストの生成および編集ツールを使用してマニフェストにアプリケーションを手動で編集する場合 (*mage.exe*と*mageui.exe*) を使用する前にマニフェストに再署名する必要があります。 詳細については、「[方法 :アプリケーション マニフェストと配置マニフェストに再署名](../deployment/how-to-re-sign-application-and-deployment-manifests.md)します。

## <a name="sign-by-using-a-certificate"></a>証明書を使用してサインインします。
 証明書は、一意のキーとソリューション発行者の id を含むファイルです。 証明書機関から証明書を購入または独自の証明書を作成し、署名証明書の権限を持つできます。

 Visual Studio は、Office ソリューションのデバッグを有効にする一時的な証明書で署名します。 証拠として、デプロイされたソリューションで一時的な証明書を使用する必要がありますできません。

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>証明書を使用して Office ソリューションに署名するには

1.  **プロジェクト** メニューのをクリックして_SolutionName_**プロパティ**します。

2.  **[署名]** タブをクリックします。

3.  選択**ClickOnce マニフェストに署名**します。

4.  クリックして証明書を見つけます**ストアから選択**または**ファイルから選択**証明書に移動するとします。

5.  正しい証明書が使用されていることを確認するには、次のようにクリックします。**詳細**証明書情報を表示します。

## <a name="see-also"></a>関連項目

- [セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)
- [Office ソリューションに信頼を付与](../vsto/granting-trust-to-office-solutions.md)
- [[署名] ページ (プロジェクト デザイナー)](../ide/reference/signing-page-project-designer.md)
